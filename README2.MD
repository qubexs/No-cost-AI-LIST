# Jimeng AI Free API

Jimeng AI Free API Service - OpenAI compatible interface supporting text-to-image, image-to-image, and video generation.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Version](https://img.shields.io/badge/version-v0.9.1-green.svg)
![Node](https://img.shields.io/badge/node-%3E%3D16.0.0-brightgreen.svg)
![Docker](https://img.shields.io/badge/docker-ready-blue.svg)

🎨 Jimeng AI's powerful image and video generation capabilities will be made available to developers through an OpenAI-compatible interface.

## Project Introduction

### Project Overview

Jimeng AI Free API is a reverse-engineered API server that encapsulates Jimeng AI's image and video generation capabilities into an OpenAI-compatible API interface. It supports the latest **jimeng-5.0**, **jimeng-4.6** text-to-image models, **Seedance 2.0 multimodal intelligent video generation** (model name `jimeng-video-seedance-2.0`, supporting mixed image/video/audio uploads), **Seedance 2.0-fast** (model name `jimeng-video-seedance-2.0-fast`), **Seedance 2.0 Fast VIP Vision** (ultra-fast inference, exclusive to members) and **Seedance 2.0 VIP Vision** (primary modality capability, exclusive to members), **international version of standard video generation** (jimeng-video-3.0/3.0-pro/3.5-pro), zero-configuration deployment, and multi-token support.

### Core Functions

- 🖼️ **TextSimple Image Support**: Supports multiple models including Jimeng-5.0, Jimeng-4.6, and Jimeng-4.5, with a maximum resolution of 4K.
- 🎭 **Image-to-Image Synthesis:** Combines multiple images, supports 1-10 input images.
- 🎬 **Video Generation**: Models such as jimeng-video-3.5-pro, supporting first/last frame control.
- 🌊 **Seedance 2.0 / 2.0-fast / 2.0-fast-vip / 2.0-vip**: Multimodal intelligent video generation, supports mixed upload of images/videos/audio, @1 and @2 placeholders for referencing materials. The fast version generates videos faster, and the VIP version is an exclusive channel for members.
- 🌍 **International Video Generation**: Supports international region tokens (prefixes such as sg-/it-/jp-/hk-, etc.), uses pure algorithmic signatures to bypass Shark anti-scraping, supports synchronous/asynchronous generation of regular videos (jimeng-video-3.0/3.0-pro/3.5-pro) and Seedance, and also supports the VIP model.
- 🎯 **International VIP Watermark-Free Download**: VIP Token automatically retrieves watermark-free videos, benefits API is automatically invoked, and watermark status is automatically detected.
- **OpenAI Compatibility:** Fully compatible with OpenAI API format, seamlessly integrates with existing clients.
- 🔄 **Multi-account support:** Supports multiple session IDs in round-robin mode.

### Technology Stack

| Technology | Version | Purpose |
|------|------|------|
| Node.js | >=16.0.0 | Runtime Environment |
TypeScript | ^5.0.0 | Programming Language |
Koa | ^2.15.0 | Web Framework |
| Playwright | ^1.49.0 | Browser Proxy (Seedance Anti-Crawling Bypass) |
| Docker | latest | Containerized deployment |

## Feature List

| Function Name | Function Description | Model | Status |
|---------|---------|------|------|
| Generate Images from Text Description | jimeng-5.0, jimeng-4.6, jimeng-4.5, jimeng-4.1, etc. | ✅ Available |
| Image-to-Image | Create new image by combining multiple images | jimeng-5.0, jimeng-4.6, jimeng-4.5, etc. | ✅ Available |
| Wensheng Video | Generates videos based on text descriptions | jimeng-video-3.5-pro, etc. | ✅ Available |
| Image-based video | Generate video using first/last frame images | jimeng-video-3.0, etc. | ✅ Available |
| Multi-Image Intelligent Video | Seedance 2.0 Multimodal Hybrid Generation | jimeng-video-seedance-2.0, seedance-2.0 | ✅ Available |
| Quick Multi-Image Video Generation | Seedance 2.0-fast Quick Generation | jimeng-video-seedance-2.0-fast, seedance-2.0-fast | ✅ Available |
| VIP Fast Video | Seedance 2.0 Fast VIP Vision Fast Deduction | jimeng-video-seedance-2.0-fast-vip, seedance-2.0-fast-vip | ✅ Available |
| VIP Professional Video | Seedance 2.0 VIP Vision Main Modality Capability | jimeng-video-seedance-2.0-vip, seedance-2.0-vip | ✅ Available |
| Audio-driven video | Seedance image + audio hybrid generation | jimeng-video-seedance-2.0, seedance-2.0-fast | ✅ Available |
| Asynchronous Video Generation | Task submission returns immediately; query interface blocks and waits for results | All Video Models | ✅ Available |
| International Video Generation | International Region Token Pure Algorithmic Signature Bypass Shark | jimeng-video-3.0, jimeng-video-3.0-pro, jimeng-video-3.5-pro, seedance-2.0-fast, seedance-2.0-pro, seedance-2.0-fast-vip, seedance-2.0-vip | ✅ Available |
| International Version Asynchronous Video | International Version Standard Video / Seedance Asynchronous Generation | jimeng-video-3.0, jimeng-video-3.0-pro, jimeng-video-3.5-pro, seedance-2.0-fast, seedance-2.0-pro, seedance-2.0-fast-vip, seedance-2.0-vip | ✅ Available |
| International VIP Version (Watermark-Free) | VIP Token Automatically Retrieves Watermark-Free Video URLs | All International Video Models | ✅ Available |
| Chat Interface | OpenAI Compatible Dialogue Interface | All Models | ✅ Available |

## Disclaimer

> ⚠️ **Important Note**

**The reverse API is unstable. We recommend visiting the official Jimeng AI website (https://jimeng.jianying.com/) to experience the features and avoid the risk of being blocked.**

This organization and individuals do not accept any financial donations or transactions. This project is purely for research, exchange, and learning purposes!

**For personal use only. Providing services or commercial use to others is strictly prohibited. Avoid putting pressure on the official service provider; otherwise, you will assume all risks!**

## Installation Instructions

### Environmental Requirements

- Node.js 16+
- npm or yarn
- Chromium browser (required for Seedance model, automatically managed via Playwright)
- Docker (optional)

### Method 1: Docker Deployment (Recommended)

**Using Docker Hub images:**

bash
# Pull Image
docker pull wwwzhouhui569/jimeng-free-api-all:latest

# Start the container
docker run -it -d --init --name jimeng-free-api-all \
  -p 8000:8000 \
  -e TZ=Asia/Shanghai \
  wwwzhouhui569/jimeng-free-api-all:latest
```

**Building from source code:**

bash
# Cloning Project
git clone https://github.com/wwwzhouhui/jimeng-free-api-all.git

# Enter directory
cd jimeng-free-api-all

# Build Image
docker build -t jimeng-free-api-all:latest .

# Start the container
docker run -it -d --init --name jimeng-free-api-all \
  -p 8000:8000 \
  -e TZ=Asia/Shanghai \
  jimeng-free-api-all:latest
```

### Method 2: Install from source code

bash
# Cloning Project
git clone https://github.com/wwwzhouhui/jimeng-free-api-all.git

# Enter directory
cd jimeng-free-api-all

# Install dependencies
npm install

# Install the Chromium browser (required for the Seedance model)
npx playwright-core install chromium --with-deps

# Development Mode
npm run dev

# Production Mode
npm run build && npm start
```

## Instructions for Use

### Get SessionID

1. Visit [JiMeng AI](https://jimeng.jianying.com/) and log in to your account.
2. Press F12 to open the developer tools.
3. Go to Application > Cookies
4. Locate the value of `sessionid`.

![Get sessionid](./doc/example-0.png)

### Multi-account configuration

Supports multiple account session IDs, separated by commas:

```
Authorization: Bearer sessionid1,sessionid2,sessionid3
```

Each request will randomly select one to use.

### API Endpoints

| Endpoint | Method | Description |
|------|------|------|
| `/v1/chat/completions` | POST | OpenAI-compatible chat interface |
| `/v1/images/generations` | POST | Image-to-image/text-to-image API (supports optional images parameter) |
| `/v1/images/compositions` | POST | Image-to-image API (backward compatible) |
| `/v1/videos/generations` | POST | Video generation interface (synchronous, blocking while waiting for result, includes VIP model) |
| `/v1/videos/generations/async` | POST | Asynchronous video generation interface (submit task, immediately returns task_id) |
| `/v1/videos/generations/async/:taskId` | GET | Asynchronous video generation interface (query task results, blocking and waiting) |
| `/v1/videos/international/generations` | POST | International version video generation (regular video + Seedance, synchronized) |
| `/v1/videos/international/generations/async` | POST | International version video generation (regular video + Seedance, asynchronous task submission) |
| `/v1/videos/international/generations/async/:taskId` | GET | Generate international video (regular video + Seedance, asynchronous query results) |
| `/v1/models` | GET | Retrieves a list of models |

### Quick Start

**Example of a textual image:**

bash
curl -X POST http://localhost:8000/v1/images/generations \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer your_sessionid" \
  -d '{
    "model": "jimeng-4.5",
    "prompt": "Beautiful sunset scenery, a cottage by the lake",
    "ratio": "16:9",
    resolution: 2k
  }'
```

**Example of a raw image (using the images parameter):**

bash
curl -X POST http://localhost:8000/v1/images/generations \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer your_sessionid" \
  -d '{
    "model": "jimeng-4.5",
    "prompt": "Merge the two images into a dreamlike style",
    "images": [
      "https://example.com/img1.jpg",
      "https://example.com/img2.jpg"
    ],
    "ratio": "1:1",
    "resolution": "2k",
    "sample_strength": 0.5
  }'
```

**Video generation example:**

bash
curl -X POST http://localhost:8000/v1/videos/generations \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer your_sessionid" \
  -d '{
    "model": "jimeng-video-3.5-pro",
    "prompt": "A cute kitten is playing on the grass",
    "ratio": "16:9",
    "resolution": "720p",
    "duration": 5
  }'
```

**Seedance 2.0 Multi-Image Video Example:**

bash
curl -X POST http://localhost:8000/v1/videos/generations \
  -H "Authorization: Bearer your_sessionid" \
  -F "model=jimeng-video-seedance-2.0" \
  -F "prompt=@1 and @2 start dancing" \
  -F "ratio=4:3" \
  -F "duration=4" \
  -F "files=@/path/to/image1.jpg" \
  -F "files=@/path/to/image2.jpg"
```

**Seedance 2.0-fast video example:**

bash
curl -X POST http://localhost:8000/v1/videos/generations \
  -H "Authorization: Bearer your_sessionid" \
  -F "model=jimeng-video-seedance-2.0-fast" \
  -F "prompt=@1 The person in the picture starts to smile" \
  -F "ratio=4:3" \
  -F "duration=5" \
  -F "files=@/path/to/image1.jpg"
```

**Seedance Image + Audio Mix Example:**

bash
curl -X POST http://localhost:8000/v1/videos/generations \
  -H "Authorization: Bearer your_sessionid" \
  -F "model=jimeng-video-seedance-2.0-fast" \
  -F "prompt=@1 The person in the picture starts dancing to the music @2" \
  -F "ratio=9:16" \
  -F "duration=5" \
  -F "files=@/path/to/image.png" \
  -F "files=@/path/to/audio.wav"
```

**Seedance 2.0 Fast VIP Rapid Reasoning Example (Member Exclusive Channel):**

bash
curl -X POST http://localhost:8000/v1/videos/generations \
  -H "Authorization: Bearer your_sessionid" \
  -F "model=jimeng-video-seedance-2.0-fast-vip" \
  -F "prompt=@1 The person in the picture starts to smile" \
  -F "ratio=4:3" \
  -F "duration=4" \
  -F "files=@/path/to/image.jpg"
```

**Seedance 2.0 VIP Main Modal Capability Example (Member Exclusive Channel):**

bash
curl -X POST http://localhost:8000/v1/videos/generations \
  -H "Authorization: Bearer your_sessionid" \
  -F "model=jimeng-video-seedance-2.0-vip" \
  -F "prompt=@1 and @2 start dancing" \
  -F "ratio=4:3" \
  -F "duration=5" \
  -F "files=@/path/to/image1.jpg" \
  -F "files=@/path/to/image2.jpg"
```

## Project Structure

```
jimeng-free-api-all/
├── src/
│ ├── index.ts # Application entry point
│ ├── daemon.ts # Daemon process management
│ ├── api/
│ │ ├── controllers/ # Business logic controllers
│ │ │ ├── core.ts # Core tools (Token processing, etc.)
│ │ │ ├── images.ts # Image generation logic
│ │ │ ├── videos.ts # Video generation logic
│ │ │ └── chat.ts # Dialogue completion logic
│ │ ├── routes/ # API route definition
│ │ │ ├── index.ts # Route aggregation
│ │ │ ├── images.ts # /v1/images/* endpoints
│ │ │ ├── videos.ts # /v1/videos/* endpoints
│ │ │ ├── chat.ts # /v1/chat/* Endpoint
│ │ │ └── models.ts # /v1/models Endpoint
│ │ └── consts/ # API constants and exceptions
│ └── lib/
│ ├── server.ts # Koa server configuration
│ ├── browser-service.ts # Browser proxy service (Seedance anti-scraping)
│ ├── config.ts # Configuration Management
│ ├── logger.ts # Logger tool
│ ├── util.ts # Auxiliary tools
│ ├── request/ # Request handling class
│ ├── response/ # Response handling class
│ ├── exceptions/ # Exception classes
│ └── configs/ # Configuration mode
├── configs/ # Configuration file directory
├── scripts/ # Scripts directory
│ └── logout-sessions.py # Tool for forcibly exiting historical sessions
├── doc/ # Document Resources
├── Dockerfile # Docker build file
├── package.json # Project configuration
└── tsconfig.json # TypeScript configuration
```

## Model Description

### Wensheng Image Model

| User Model Name | Internal Model Name | Description |
|-----------|-----------|------|
| `jimeng-5.0` | `high_aes_general_v50` | Version 5.0, latest model |
| `jimeng-4.6` | `high_aes_general_v42` | Latest model, recommended |
| `jimeng-4.5` | `high_aes_general_v40l` | High-quality model |
| `jimeng-4.1` | `high_aes_general_v41` | High-quality model |
| `jimeng-4.0` | `high_aes_general_v40` | Stable version |
| `jimeng-3.1` | `high_aes_general_v30l_art_fangzhou` | Art Style |
| `jimeng-3.0` | `high_aes_general_v30l` | General Model |
| `jimeng-2.1` | - | Older model |
| `jimeng-2.0-pro` | - | Older professional model |
| `jimeng-2.0` | - | Older model |
| `jimeng-1.4` | - | Early model |
| `jimeng-xl-pro` | - | XL Professional Model |

### Video Model

| User Model Name | Internal Model Name | Description |
|-----------|-----------|------|
| `jimeng-video-3.5-pro` | `dreamina_ic_generate_video_model_vgfm_3.5_pro` | Latest video model |
| `jimeng-video-3.0` | `dreamina_ic_generate_video_model_vgfm_3.0` | Video generation 3.0 |
| `jimeng-video-3.0-pro` | `dreamina_ic_generate_video_model_vgfm_3.0_pro` | Video Generation 3.0 Professional Edition |
| `jimeng-video-seedance-2.0` | `dreamina_seedance_40_pro` | Seedance 2.0 (upstream standard name, recommended) |
| `seedance-2.0` | `dreamina_seedance_40_pro` | Seedance 2.0 (backward compatible alias) |
| `seedance-2.0-pro` | `dreamina_seedance_40_pro` | Seedance 2.0 (backward compatible alias) |
| `jimeng-video-seedance-2.0-fast` | `dreamina_seedance_40` | Seedance 2.0-fast (upstream standard name) |
| `seedance-2.0-fast` | `dreamina_seedance_40` | Seedance 2.0-fast (backward compatible alias) |
| `jimeng-video-seedance-2.0-fast-vip` | `dreamina_seedance_40_vision` | Seedance 2.0 Fast VIP Vision (Exclusive Member Access) |
| `seedance-2.0-fast-vip` | `dreamina_seedance_40_vision` | Seedance 2.0 Fast VIP Vision (backward compatible alias) |
| `jimeng-video-seedance-2.0-vip` | `dreamina_seedance_40_pro_vision` | Seedance 2.0 VIP Vision Main Modal Capability Version (Member Exclusive Channel) |
| `seedance-2.0-vip` | `dreamina_seedance_40_pro_vision` | Seedance 2.0 VIP Vision (backward compatible alias) |

### Resolution Support

#### Image Resolution

| Resolution | 1:1 | 4:3 | 3:4 | 16:9 | 9:16 | 3:2 | 2:3 | 21:9 |
|--------|-----|-----|------|------|------|-----|------|------|
| 1k | 1024×1024 | 768×1024 | 1024×768 | 1024×576 | 576×1024 | 1024×682 | 682×1024 | 1195×512 |
| 2k | 2048×2048 | 2304×1728 | 1728×2304 | 2560×1440 | 1440×2560 | 2496×1664 | 1664×2496 | 3024×1296 |
| 4k | 4096×4096 | 4608×3456 | 3456×4608 | 5120×2880 | 2880×5120 | 4992×3328 | 3328×4992 | 6048×2592 |

#### Video Resolution

| Resolution | 1:1 | 4:3 | 3:4 | 16:9 | 9:16 |
|--------|-----|-----|-----|------|------|
| 480p | 480×480 | 640×480 | 480×640 | 854×480 | 480×854 |
| 720p | 720×720 | 960×720 | 720×960 | 1280×720 | 720×1280 |
| 1080p | 1080×1080 | 1440×1080 | 1080×1440 | 1920×1080 | 1080×1920 |

## API Detailed Documentation

### Image Generation Interface

**POST /v1/images/generations**

A unified interface supports both text-to-image and image-to-image modes:

| Parameter | Type | Required | Default Value | Description |
|------|------|------|--------|------|
| model | string | No | jimeng-4.5 | Model Name |
| prompt | string | is | - | Prompt word, supports multiple image generation |
| images | array | No | - | An array of image URLs (1-10 images). If provided, the image will be generated using the raw image mode; otherwise, the text will be generated using the raw image mode. |
| negative_prompt | string | no | "" | negative prompt word |
| ratio | string | No | 1:1 | Aspect Ratio |
| resolution | string | No | 2k | Resolution: 1k, 2k, 4k |
| sample_strength | number | No | 0.5 | Fineness 0-1 |
| response_format | string | No | url | url or b64_json |

**illustrate:**
- When the `images` parameter is empty or not provided, the interface performs the text-to-image function.
- When the `images` parameter provides (1-10 images), the interface performs the image generation function.
- Supports two request formats: `application/json` (where images is an array of URLs) and `multipart/form-data` (uploads files via the images field).
- In graph-based image mode, the response will additionally include the `input_images` and `composition_type` fields.

### Image-to-Image Interface (Backward Compatibility)

**POST /v1/images/compositions**

This interface is retained to ensure backward compatibility, and its functionality is the same as when the `images` parameter is provided in `/v1/images/generations`.

| Parameter | Type | Required | Default Value | Description |
|------|------|------|--------|------|
| model | string | No | jimeng-4.5 | Model Name |
| prompt | string | is | - | prompt word |
| images | array | is | - | An array of image URLs, 1-10 images |
| ratio | string | No | 1:1 | Aspect Ratio |
| resolution | string | No | 2k | resolution |

### Video Generation Interface

**POST /v1/videos/generations**

| Parameter | Type | Required | Default Value | Description |
|------|------|------|--------|------|
| model | string | No | jimeng-video-3.0 | Model Name |
| prompt | string | is | - | video description |
| ratio | string | No | 1:1 | Aspect Ratio |
| resolution | string | No | 720p | Resolution: 480p, 720p, 1080p |
| duration | number | No | 5 | Duration: 4-15 seconds (Seedance), 5 or 10 seconds (Normal) |
| file_paths | array | No | [] | First/last frame image URLs |

### Asynchronous Video Generation Interface

Due to the long queuing time on the Jimeng platform, synchronous interfaces may be blocked for 10-20 minutes. Asynchronous interfaces separate submission and query to avoid occupying the connection for a long time.

#### Submit asynchronous tasks

**POST /v1/videos/generations/async**

The request parameters are exactly the same as those of the synchronous interface `POST /v1/videos/generations`, but it immediately returns `task_id` instead of waiting for the video to be generated.

| Parameter | Type | Required | Default Value | Description |
|------|------|------|--------|------|
| model | string | No | jimeng-video-3.0 | Model Name |
| prompt | string | is | - | video description |
| ratio | string | No | 1:1 | Aspect Ratio |
| resolution | string | No | 720p | Resolution: 480p, 720p, 1080p |
| duration | number | No | 5 | Duration: 4-15 seconds (Seedance), 5 or 10 seconds (Normal) |
| file_paths | array | No | [] | First frame/last frame/source image URL |
| files | file[] | No | - | Uploaded media files (multipart) |

**Response Example:**

json
{
  "created": 1774778941,
  "task_id": "4f2acc30-2b57-11f1-9361-e959a88411c4",
  "status": "processing",
  "message": "The task has been submitted. Please use the GET request to retrieve the results for /v1/videos/generations/async/{task_id}".
}
```

**Example of usage:**

bash
# Submit a regular video generation task
curl -X POST http://localhost:8000/v1/videos/generations/async \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer your_sessionid" \
  -d '{
    "model": "jimeng-video-3.5-pro",
    "prompt": "A kitten is running on the grass",
    "ratio": "16:9",
    "resolution": "720p",
    "duration": 5
  }'

# Submit an asynchronous Seedance task (JSON + image URL)
curl -X POST http://localhost:8000/v1/videos/generations/async \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer your_sessionid" \
  -d '{
    "model": "seedance-2.0-fast",
    "prompt": "@1 The person in the picture has started to smile",
    "ratio": "4:3",
    "duration": 4,
    "file_paths": ["https://example.com/image.jpg"]
  }'

# Submit a Seedance asynchronous task (multipart file upload)
curl -X POST http://localhost:8000/v1/videos/generations/async \
  -H "Authorization: Bearer your_sessionid" \
  -F "model=seedance-2.0" \
  -F "prompt=@1 and @2 start dancing" \
  -F "ratio=4:3" \
  -F "duration=4" \
  -F "files=@/path/to/image1.jpg" \
  -F "files=@/path/to/image2.jpg"
```

#### Query Asynchronous Task Results

**GET /v1/videos/generations/async/:taskId**

When submitting the `task_id`, the server will block and wait for the video to be generated before returning the result, without requiring client polling.

**Successful response:**

json
{
  "created": 1774778988,
  "task_id": "4f2acc30-2b57-11f1-9361-e959a88411c4",
  "status": "succeeded",
  "data": [{
    "url": "https://v3-dreamnia.jimeng.com/.../video.mp4",
    "revised_prompt": "A kitten is running on the grass."
  }]
}
```

**Failure Response:**

json
{
  "created": 1774778988,
  "task_id": "4f2acc30-2b57-11f1-9361-e959a88411c4",
  "status": "failed",
  Error: [API_IMAGE_GENERATION_FAILED] Video generation timed out.
}
```

**Example of usage:**

bash
curl http://localhost:8000/v1/videos/generations/async/4f2acc30-2b57-11f1-9361-e959a88411c4 \
  --header 'Authorization: Bearer your_sessionid'
```

**Note:**
Asynchronous tasks support a maximum of **10 concurrent requests**. Submitting an API request exceeding this limit will return an error message.
> - Task data is persistently stored in the `tmp/async-tasks/` directory and is not lost upon process restart.
> - Automatically resume unfinished processing tasks and re-execute polling when the program starts.
> - Completed task will automatically expire and be cleared in 24 hours.

### Seedance 2.0 / 2.0-fast / VIP Interface

**POST /v1/videos/generations**

| Parameter | Type | Required | Default Value | Description |
|------|------|------|--------|------|
| model | string | Yes | - | jimeng-video-seedance-2.0 (recommended), jimeng-video-seedance-2.0-fast (fast version), jimeng-video-seedance-2.0-fast-vip (VIP fast reasoning), jimeng-video-seedance-2.0-vip (VIP main modality) or seedance-2.0 |
| prompt | string | No | - | Prompt word, use @1, @2 to reference source material (image/video/audio) |
| ratio | string | No | 4:3 | Aspect Ratio |
| duration | number | No | 4 | Video length 4-15 seconds |
| files | file[] | is * | - | Uploaded source files (images/videos/audio, multipart) |
| file_paths | array | is * | - | Array of source URLs (JSON) |

**Supported media types:**
- Images: jpg, png, webp, gif, bmp
- Videos: mp4, mov, m4v
- Audio: mp3, wav

**Placeholder for prompt word:**
- `@1` / `@图1` / `@image1` - Referencing the first source material
- `@2` / `@图2` / `@image2` - Referencing the second source material

### International Version Video Interface

The international version uses the CapCut/Dreamina international platform (`mweb-api-sg.capcut.com`), and the token uses a regional prefix format (such as `sg-xxx`, `it-xxx`), supporting both regular video and seedance.

#### Synchronous Generation

**POST /v1/videos/international/generations**

- Standard video models: `jimeng-video-3.0`, `jimeng-video-3.0-pro`, `jimeng-video-3.5-pro`
  - Supports JSON / multipart
  - `duration` only supports `5` or `10`.
  - When there is no source material, generate video from text; when uploading `file_paths`, you can generate video from the first frame/last frame.
- Seedance models: `seedance-2.0-fast`, `seedance-2.0-pro`, `seedance-2.0-fast-vip`, `seedance-2.0-vip` and their corresponding `jimeng-video-seedance-*` names.
  - `duration` supports `4-15`
  - At least one source file is required (keyed multipart file, keyed URL field, or `file_paths/filePaths`).

**Example of usage:**

bash
# International version of standard video synchronous generation (JSON)
curl -X POST http://localhost:8000/v1/videos/international/generations \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer sg-your_sessionid" \
  -d '{
    "model": "jimeng-video-3.0",
    "prompt": "A cute cat walking slowly on grass, cinematic, natural motion",
    "ratio": "16:9",
    "resolution": "720p",
    "duration": 5
  }'

# International version of Seedance generated synchronously (multipart file upload)
curl -X POST http://localhost:8000/v1/videos/international/generations \
  -H "Authorization: Bearer sg-your_sessionid" \
  -F "model=seedance-2.0-fast" \
  -F "The character in prompt=@1 begins to smile" \
  -F "ratio=4:3" \
  -F "duration=4" \
  -F "image_file=@/path/to/image.jpg"

# International version of Seedance generates (JSON + image URL) synchronously
curl -X POST http://localhost:8000/v1/videos/international/generations \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer sg-your_sessionid" \
  -d '{
    "model": "seedance-2.0-fast",
    "prompt": "The character in @1 begins to smile",
    "ratio": "4:3",
    "duration": 4,
    "file_paths": ["https://example.com/image.jpg"]
  }'

# International Version VIP Model Generation
curl -X POST http://localhost:8000/v1/videos/international/generations \
  -H "Authorization: Bearer sg-your_sessionid" \
  -F "model=seedance-2.0-fast-vip" \
  -F "The character in prompt=@1 begins to smile" \
  -F "ratio=4:3" \
  -F "duration=4" \
  -F "image_file=@/path/to/image.jpg"
```

#### Asynchronous Generation (New in v0.8.9)

**POST /v1/videos/international/generations/async**

The request parameters are exactly the same as those of the synchronous interface, but the `task_id` is returned immediately.

**GET /v1/videos/international/generations/async/:taskId**

The server queries the results of an asynchronous task, but it is blocked and waiting for the video to be generated before returning the result.

bash
# Submit an asynchronous task for the international version
curl -X POST http://localhost:8000/v1/videos/international/generations/async \
  -H "Authorization: Bearer sg-your_sessionid" \
  -F "model=seedance-2.0-fast" \
  -F "The character in prompt=@1 begins to smile" \
  -F "ratio=4:3" \
  -F "duration=4" \
  -F "image_file=@/path/to/image.jpg"

# Query Results
curl http://localhost:8000/v1/videos/international/generations/async/{task_id}
```

International standard video formats have been tested and approved: `jimeng-video-3.0`, `jimeng-video-3.0-pro`, and `jimeng-video-3.5-pro`.

#### Supported Region Prefixes

| Prefix | Region | Prefix | Region | Prefix | Region | Prefix | Region |
|------|------|------|------|------|------|------|------|
| `sg-` | Singapore | `hk-` | Hong Kong | `jp-` | Japan | `it-` | Italy |
| `al-` | Albania | `az-` | Azerbaijan | `bh-` | Bahrain | `ca-` | Canada |
| `cl-` | Chile | `de-` | Germany | `gb-` | United Kingdom | `gy-` | Guyana |
| `il-` | Israel | `iq-` | Iraq | `jo-` | Jordan | `kg-` | Kyrgyzstan |
| `om-` | Oman | `pk-` | Pakistan | `pt-` | Portugal | `sa-` | Saudi Arabia |
| `se-` | Sweden | `tr-` | Turkey | `tz-` | Tanzania | `uz-` | Uzbekistan |
| `ve-` | Venezuela | `xk-` | Kosovo | | | | |

**Note:** The US Token (prefixed with `us-`) is not currently supported by the international version of the video interface.

## Effect Demonstration

![image-20260209234137309](https://mypicture-1258720957.cos.ap-nanjing.myqcloud.com/Obsidian/image-20260209234137309.png)

![image-20260209230221386](https://mypicture-1258720957.cos.ap-nanjing.myqcloud.com/Obsidian/image-20260209230221386.png)

![Multiple image composite](https://mypicture-1258720957.cos.ap-nanjing.myqcloud.com/Obsidian/QQ_1757688787070.png)

![Wensheng Video 3.0](https://mypicture-1258720957.cos.ap-nanjing.myqcloud.com/Obsidian/QQ_1757688755495.png)

![Wensheng Video 3.5](https://mypicture-1258720957.cos.ap-nanjing.myqcloud.com/Obsidian/image-20251220192531051.png)

International version

https://dreamina.capcut.com/

![image-20260401222933526](https://mypicture-1258720957.cos.ap-nanjing.myqcloud.com/Obsidian/image-20260401222933526.png)

Points policies may vary in different regions. Currently, the Seedance 2.0-fast interface has zero points for the first time.

![image-20260401223225792](https://mypicture-1258720957.cos.ap-nanjing.myqcloud.com/Obsidian/image-20260401223225792.png)

## Development Guide

### Local Development

bash
# Cloning Project
git clone https://github.com/wwwzhouhui/jimeng-free-api-all.git
cd jimeng-free-api-all

# Install dependencies
npm install

# Install the Chromium browser (required for initial development)
npx playwright-core install chromium --with-deps

# Development Mode (Hot Reload)
npm run dev
```

### Build and Deployment

bash
# Build production version
npm run build

# Start production services
npm start
```

## Security Management: Force Exit Historical Sessions

### Scene Description

Jimeng AI uses the ByteDance account system, and **re-login will not invalidate the historical session ID** (multi-device parallel mechanism). When the session ID is leaked, shared with others, or the account being used is changed, it is necessary to actively force the historical session to be canceled on the server side.

### Exit Tool

The project provides the `scripts/logout-sessions.py` script, which uses the Playwright headless browser to automatically simulate a user clicking "Logout", thus making the specified session ID completely invalid on the Jimeng server.

**Exit Principle:**
```
Inject sessionid → Open JiMeng homepage → Verify login
  → Click the "Settings" button on the left → A drop-down menu will pop up → Click "Exit"
  → Call the /passport/web/logout/ interface → Session destroyed on the server side
```

### Install dependencies

bash
# Install Python dependencies
pip install playwright

# Install Chromium browser (first time using)
playwright install chromium
```

### How to use

**Method 1: Pass the session ID via command line (Recommended)**

bash
# Exit a single session ID
python3 scripts/logout-sessions.py 73795a52a17c7ee7e95c213a22135c96

# Batch logout of multiple session IDs (separated by spaces)
python3 scripts/logout-sessions.py \
  aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa\
  bbbbbbbbbbbbbbbbbbbbbbbbbbbb\
  cccccccccccccccccccccccccccccc
```

**Method 2: Edit the script list**

Open `scripts/logout-sessions.py`, and enter the session ID to be logged out in the `SESSION_IDS` list at the top:

Python
SESSION_IDS = [
    "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
    "bbbbbbbbbbbbbbbbbbbbbbbbbbbb",
    "cccccccccccccccccccccccccccccccc",
]
```

Then run it directly:

bash
python3 scripts/logout-sessions.py
```

### Output Example

```
JiDream AI Historical Session Force Exit Tool
============================================================
There are 3 session IDs pending processing.

[1/3] Processing: aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
         → ✅ Exit successful (Server-side issue)

[2/3] Treatment: bbbbbbbbbbbbbbbbbbbbbbbbbbbb
         → ✅ Exit successful (Server-side issue)

[3/3] Processing: cccccccccccccccccccccccccccc
         → ⬜ This is no longer valid and requires no action.

============================================================
Summary of exit results:
============================================================
  aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa → ✅ Exit successful (Server-side issue)
  bbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbbb → ✅ Exit successful (Server-side issue expired)
  cccccccccccccccccccccccccccccccccc → ⬜ Expired, no action required (No action required)

  ✅ Successfully exited: 2
  ⬜ Expired: 1 (No action required)
```

### Status Description

| Status | Meaning |
|------|------|
| ✅ Logout successful | The sessionid has been destroyed on the server and can no longer be used.
| ⬜ Expired | The sessionid has expired naturally and no action is required.
| ⚠️ Status uncertain | Please manually log in to the corresponding account to verify, or try again |
| ❌ Exit button not found | The page structure of JiDream may have changed. Please report an issue. |
| ❌ An error has occurred | Network problem or Playwright not installed correctly |

> ⚠️ **Note:** The exit operation is irreversible. Please confirm that the sessionid list is correct before execution.

---

## Frequently Asked Questions

<details>
How do I get the session ID?

1. Visit [JiMeng AI](https://jimeng.jianying.com/) and log in.
2. Press F12 to open the developer tools.
3. Go to Application > Cookies
4. Copy the value of `sessionid`

</details>

<details>
What happens if the sessionid expires?

Session IDs have a limited validity period; after they expire, you need to log in to the Jimeng website again to obtain a new session ID. It is recommended to configure multiple accounts to improve availability.

</details>

<details>
How to force account cancellation if sessionid is leaked?

Using the exit tool provided by the project, you can forcibly destroy historical session IDs on the server side:

bash
python3 scripts/logout-sessions.py <leaked sessionid>
```

See the section on [Security Management: Forced Exit from History Session](#Security Management Forced Exit from History - session) for details.

</details>

<details>
How to configure multiple accounts?

Use commas to separate multiple session IDs in the Authorization header:
```
Authorization: Bearer sessionid1,sessionid2,sessionid3
```

</details>

<details>
<summary>Docker container fails to start?</summary>

1. Check if port 8000 is in use.
2. Ensure the Docker service is running.
3. View container logs: `docker logs jimeng-free-api-all`

</details>

<details>
<summary> failed to generate and returned an error?</summary>

1. Check if the sessionid is valid.
2. Confirm that your account has sufficient points.
3. Check if the request parameters are correct.
4. Check the server logs for detailed error information.

</details>

<details>
<summary>Seedance video generation reports a "shark not pass" error?</summary>

**Domestic Version (CN Token):** v0.8.4 has been resolved using the Playwright browser proxy. Please ensure:
1. Chromium browser is already installed: `npx playwright-core install chromium --with-deps`
2. Docker users should use image version v0.8.4 or higher. The Dockerfile already includes Chromium support.
3. The first Seedance request will automatically launch the browser (in a few seconds); subsequent requests will reuse the session.

**International Version (International Token):** v0.8.9 has been bypassed via pure algorithmic signatures (X-Bogus / X-Gnarly), requiring no Chromium installation.
1. Ensure that the token uses the correct locale prefix (e.g., `sg-`, `it-`, `jp-`).
2. Signatures are automatically injected by `src/lib/x-bogus.ts` and `src/lib/x-gnarly.ts`, requiring no additional configuration.
3. US Token (prefixed with `us-`) is not currently supported by the international version of the video interface.

</details>

## Update Log

### v0.8.12 (2026-04-07) - International VIP Version - Watermark-Free Video Download

- 🎯 **International VIP Watermark-Free Download**: VIP Token automatically retrieves the watermark-free video URL, matching the actual browser download process.
  - Added benefits API call to `fetchHighQualityVideoUrl()`: `benefit_metadata` + `batch_get_user_benefit`
  - Automatically detects and records video URLs and watermark status: `display_watermark_busi_aigc` (free/with watermark) vs `display_watermark_aigc` (VIP/no watermark)
  - The signed CDN URL obtained by VIP users via `get_local_item_list` automatically points to the watermark-free video file.
- 🔧 **Video URL Extraction and Reconstruction**: `fetchHighQualityVideoUrl()` has been changed from multiple early-return methods to a unified variable + cascading degradation strategy, supporting unified post-processing after extraction.
- 🔧 **Video URL Extraction Priority Optimization**: Added `common_attr.transcoded_video.origin.video_url` as the highest priority extraction field.

### v0.8.11 (2026-04-06) - International version: Standard video generation + Image upload reconstruction + Removal of old video models

- 🌍 **International Version Standard Video Generation**: The international version's synchronous/asynchronous interfaces now support standard video models (`jimeng-video-3.0`, `jimeng-video-3.0-pro`, `jimeng-video-3.5-pro`), with a unified entry point for Seedance.
  - Added `generateInternationalVideo` / `generateInternationalVideoCore` functions
  - Added the functions `INTERNATIONAL_VIDEO_MODEL_MAP` and `getVideoBenefitType`.
  - International version of standard video draft, version 3.3.12
  - Supports video generation from the first frame/last frame (up to 2 images).
- 🔧 **Image upload logic refactoring**: The `uploadImageFromUrl` and `uploadImageBuffer` functions in `images.ts` have been replaced with a unified upload channel reused in `videos.ts`, eliminating duplicate code.
  - International version images are uploaded via `uploadInternationalImageUrl`
  - The domestic version uploads images via `uploadImageBufferForVideo`.
- 🔧 **Region-aware assistantId**: Image generation uses `getImageAssistantId()` to return the correct aid value based on the region.
- 🗑️ **Removal of old video models**: Removed `jimeng-video-2.0` and `jimeng-video-2.0-pro` (both removed from `/v1/models` and MODEL_MAP)
- 🔧 **International Version Video Parameter Optimization**: The default values ​​for duration/ratio are dynamically determined based on the model type (Seedance: duration=4/ratio=4:3, Normal Video: duration=5/ratio=1:1).
- 🐛 **Fixed core.ts checkResult:** Added compatibility handling for empty responses where `ret === '' && errmsg === ''`

### v0.8.10 (2026-04-03) - Added Seedance 2.0 VIP Vision member-exclusive model + upload area routing separation

- ✨ **New Seedance 2.0 Fast VIP Vision Model**: Ultra-fast inference version (`jimeng-video-seedance-2.0-fast-vip` / `seedance-2.0-fast-vip`), internal model `dreamina_seedance_40_vision`, exclusive for VIP members, Draft version 3.3.12
- ✨ **Added Seedance 2.0 VIP Vision Model**: Main modal capability version (`jimeng-video-seedance-2.0-vip` / `seedance-2.0-vip`), internal model `dreamina_seedance_40_pro_vision`, exclusive channel for VIP members, Draft version 3.3.12
- ✨ **VIP models are supported simultaneously in both domestic and international versions**: Both the domestic version `/v1/videos/generations` and the international version `/v1/videos/international/generations` support 4 VIP models.
- 🔧 **Upload Region Routing Separation**: Added `regionFetch()` / `cnFetch()` functions. Domestic uploads connect directly (without a proxy), while international uploads use a proxy, preventing connection failures due to proxies for CN upload targets (`imagex.bytedanceapi.com`).
- 🔧 **Enhanced Request Parameter Generation**: Added `commerce_with_input_video: "1"` and `workspace_id: 0` parameters to match the latest request format on the Jimeng official website.
- 📝 **/v1/models API Update**: Added 4 new VIP models to the model list API.

### v0.8.9 (2026-04-01) - International Version Video + Pure Algorithm Signature Bypass Shark + Asynchronous Interface

- 🌍 **New International Version Video Generation Interface**: Supports international region tokens (26 region prefixes including sg-/it-/jp-/hk-), using the CapCut/Dreamina international platform (`mweb-api-sg.capcut.com`).
  - `POST /v1/videos/international/generations` — Synchronous video generation
  - `POST /v1/videos/international/generations/async` — Asynchronous video generation (task submission)
  - `GET /v1/videos/international/generations/async/:taskId` — Asynchronous video generation (query results)
- 🔐 **X-Bogus / X-Gnarly Pure Algorithm Signature**: The international version video link does not require a Playwright browser proxy, bypassing Shark's anti-scraping measures through a pure TypeScript algorithm.
  - `src/lib/x-bogus.ts`: MD5 + RC4 + custom Base64 encoded signature (URL query parameter)
  - `src/lib/x-gnarly.ts`: ChaCha20 PRNG + custom Base64 encoded signature (HTTP request header)
- ✨ **International Version Asynchronous Video Generation**: Functionality fully equivalent to the domestic version's asynchronous interface.
  - Concurrency control (maximum 10), disk persistence (`tmp/async-tasks/`), automatic recovery after service restart, and 24-hour expiration cleanup.
  - Supports on-demand queries: Timed-out tasks remain in a processing state, allowing users to check the platform's latest status in real time when querying.

### v0.8.8 (2026-03-29) - Added asynchronous video generation interface

- ✨ **Added asynchronous video generation interface**: Resolves the issue of synchronous interface being blocked for 20 minutes and unable to return due to queuing on the JiDream platform.
  - `POST /v1/videos/generations/async` — Submits a video generation task and immediately returns the `task_id`.
  - `GET /v1/videos/generations/async/:taskId` — Query task results; the server blocks and waits for the video to be generated before returning.
- ✨ **Supports all video models**: Asynchronous calls are supported for both regular video (jimeng-video-3.5-pro, etc.) and Seedance 2.0/2.0-fast.
- ✨ **Concurrency Control**: Asynchronous tasks are limited to a maximum of 10 concurrent requests; if this limit is exceeded, the submitted API will return an error message.
- 💾 **Task Persistence**: Task data is saved to the `tmp/async-tasks/` directory (JSON file), and is not lost upon process restart.
- 🔄 **Startup Resume**: Automatically resumes unfinished `processing` tasks and re-executes polling when the program starts.
- ⏱️ **24-hour expiration**: Completed/failed tasks will be automatically deleted after 24 hours.
- 📝 **Alias ​​are automatically enabled:** `/v1/video/generations/async` is also available.

### v0.8.7 (2026-03-22) - Added a tool for forcibly exiting historical sessions.

- 🔒 **Added `scripts/logout-sessions.py`: Simulates a click to log out using the Playwright headless browser, forcibly logging out historical session IDs in batches.
- **Logout Principle:** Inject session ID → Open the JiMeng homepage → Click "Settings → Logout" → Call the `/passport/web/logout/` API → Server-side session is completely destroyed.
- 📝 **Supports command-line parameters**: `python3 scripts/logout-sessions.py <sid1> [sid2] ...`, or add `SESSION_IDS` to the top of the script for batch processing.
- 📝 **Status Detection**: Automatically identifies and skips expired session IDs, and verifies the `window.__isLogined` status in real time after logging out.

### v0.8.6 (2026-02-20) - jimeng-5.0 Official Model Update

- 🔄 **Model renamed `jimeng-5.0-preview` → `jimeng-5.0`: The Jimeng platform has upgraded the 5.0 preview version to the official version, removing the `-preview` suffix.
- 🔧 **Update Model Configuration**: Synchronously update the model name mappings in `MODEL_MAP`, `MODEL_DRAFT_VERSIONS`, and `MODEL_CONFIGS`.
- 🔧 **Update Model List Interface**: The model IDs and descriptions returned by `/v1/models` are updated synchronously.

### v0.8.5 (2026-02-20) - Seedance supports multimodal content (mixed upload of images/videos/audio).

- ✨ **Seedance Multimodal Media Upload**: Supports mixed uploads of images, videos, and audio, automatically detecting media types based on MIME type and file extension.
- ✨ **VOD Upload Channel**: Audio/video files are uploaded via the ByteDance VOD API (`ApplyUploadInner` → Upload → `CommitUploadInner`) to obtain the actual VOD video.
- ✨ **Audio Duration Parsing**: The VOD service automatically parses audio duration, with backup support for WAV file header parsing.
- 🔧 **AWS Signature Enhancements**: `createSignature` now supports custom `region` and `service` parameters, and supports dual-channel signatures for ImageX (`imagex`) and VOD (`vod`).
- 🔧 **Separate Upload Tokens**: Image uploads use `scene: 2` (ImageX), audio/video uploads use `scene: 1` (VOD, `spaceName=dreamina`).
- 📝 **Supported Media Formats**: Images (jpg/png/webp/gif/bmp), Videos (mp4/mov/m4v), Audio (mp3/wav)

### v0.8.4 (2026-02-18) - Fixed Seedance "shark not pass" anti-scraping interception.

- 🐛 **Fixed Seedance video generation being blocked by the Shark security middleware:** Jimeng has added `a_bogus` signature verification to the `/mweb/v1/aigc_draft/generate` interface. Node.js directly returns `ret=1019, "shark not pass"` when requesting.
- ✨ **Added BrowserService browser proxy service:** Starts headless Chromium via Playwright, automatically injecting the `a_bogus` signature into the browser using ByteDance's `bdms` SDK.
- 🔧 **Only Seedance generate requests use the browser proxy:** Other requests (image generation, regular video, upload, polling, points query) remain unaffected and continue to use Node.js for direct requests.
- ⚡ **Lazy Start and Session Reuse**: The browser is only started on the first Seedance request; each sessionId has an independent session; and sessions are automatically cleaned up after 10 minutes of inactivity.
- 🔧 **Resource Optimization**: Browsers block irrelevant resources such as images, fonts, and CSS, only loading scripts related to the bdms SDK (whitelisted domains: vlabstatic.com, bytescm.com, jianying.com).
- 🐳 **Docker Support Update**: Dockerfile now uses `node:lts` (not alpine), and includes built-in Chromium system dependencies and browser installation.
- 📦 **Added dependency**: `playwright-core ^1.49.0`

### v0.8.3 (2026-02-14) - Fixed Seedance 2.0-fast points deduction failure

- 🐛 **Fixed the benefit_type error in the fast version**: `dreamina_video_seedance_20_fast` → `dreamina_seedance_20_fast` (without the `video_` prefix), resolving the `credit prededuct failed` error.
- 🔧 **Upgrade Seedance Draft version**: `3.3.8` → `3.3.9`, consistent with the official website of JiDeng.
- 🔧 **Upgrade client version number**: `VERSION_CODE` from `5.8.0` to `8.4.0`, `Chrome UA` updated to 132.
- 🔧 **Complete Request Headers**: Added `App-Sdk-Version`, `Lan`, and `Loc` headers to match requests from the JiDream website.
- 🔧 **Corrected region parameter**: `CN` → `cn` (lowercase), consistent with the official website of Jimeng.
- 🔧 **Complete the image_info.aigc_image field**: Add an `aigc_image` object to the image_info field in Seedance material_list.

### v0.8.2 (2026-02-13) - Added Seedance 2.0-fast fast video generation model

- ✨ **Added `jimeng-video-seedance-2.0-fast` model**: Seedance 2.0 fast version, internal model is `dreamina_seedance_40`, generation speed is faster.
- ✨ **Added `seedance-2.0-fast` alias: Backwards compatible alias
- 🔧 **Added fast version benefit_type**: `dreamina_video_seedance_20_fast`, to differentiate between the standard and fast versions.
- 🔧 **Optimized Seedance Model Recognition**: The `isSeedanceModel` function now uses prefix matching to automatically accommodate newly added Seedance variants.

### v0.8.1 (2026-02-10) - Seedance 2.0 Model Name Update

- 🔄 **Added model name `jimeng-video-seedance-2.0`: The original `seedance-2.0` and `seedance-2.0-pro` are retained as backward compatibility aliases.
- ⏱️ **Extended Seedance Duration Support**: Expanded from a fixed 4 seconds to a continuous range of 4-15 seconds.
- 🔧 **Draft Version Update**: The Seedance model Draft version has been changed from `3.3.9` to `3.3.8`.

### v0.8.0 (2026-02-09) - Added jimeng-5.0-preview (now renamed jimeng-5.0) and jimeng-4.6 image generation models.

- ✨ **Added jimeng-5.0-preview model**: The latest 5.0 preview version of the image generation model from Jimeng AI (internal model `high_aes_general_v50`), v0.8.6 has been renamed `jimeng-5.0`.
- ✨ **New jimeng-4.6 model**: Jimeng AI version 4.6 image generation model (internal model `high_aes_general_v42`), supports text-to-image, image-to-image, and multi-image generation.
- ⚡ **Upgrade Draft Versions**: jimeng-5.0-preview and jimeng-4.6 now use the latest `3.3.9` version.
- 🔧 **Extended Multi-Graph Generation Support**: Multi-graph detection regularity matching extended to the jimeng-5.x series models.

### v0.7.1 (2026-02-09) - Fixed the issue where video generation returned a high-definition download URL.

- 🐛 **Fixed the issue of returning low-bitrate preview URLs for videos**: The video generation interface (including Seedance 2.0) previously returned a low-bitrate preview URL (bitrate ~1152) for `vlabvod.com`. Now, the high-bitrate download URL (bitrate ~6297+) for `dreamnia.jimeng.com` is obtained via the `get_local_item_list` API.
- 🐛 **Fixed Seedance polling response parsing failure**: The `get_history_by_ids` API returned data with `historyId` as the key (e.g., `result["8918159809292"]`), instead of the `result.history_list` array. This caused the polling loop to fail to parse the response correctly, resulting in no response from the client after the video was generated.
- 🐛 **Fixed parsing of normal video polling response**: The `generateVideo` function now includes a `result[historyId]` fallback parsing feature, ensuring compatibility with API responses using the historyId key-value format.
- 🐛 **Fixed item_id extraction field name:** The video item ID returned by the API is located in the `common_attr.id` field; add this field to the extraction chain.

### v0.7.0 (2026-02-07) - Seedance 2.0 Multi-Image Intelligent Video Generation

- ✨ **New Seedance 2.0 model added:** Supports generating videos from multiple images.
- ✨ **Multi-image mixed prompts**: Supports using placeholders such as `@1` and `@2` to reference images.
- 🐛 **Fixed multipart file upload: Optimized koa-body configuration**
- 🔒 **Security Vulnerability Remediation**: Upgrade dependencies to fix 19 security vulnerabilities.
- ⚡ **Optimized parameter verification**: The `prompt` parameter is now optional.

### v0.6.0 (2024-12-20) - Added video model

- ✨ **Added jimeng-video-3.5-pro model**
- ⚡ **Upgrade Draft version**: Use version `3.3.4`
- 🔧 **Dynamic Version Management**: Automatically selects the draft version based on the model.

### v0.5.0 (2024-12-12) - Parameter format optimization

- 🔄 **Unified parameter format**: Use `ratio` and `resolution` instead of `width`/`height`
- 📤 **Supports multipart/form-data:** Supports direct file upload for generating raw images and videos.
- ⚡ **Optimized error messages**

### v0.4.0 (2024-12-11) - Optimized for no-credit system

- 🐛 **Fixed points deduction issue:** Optimized request parameters to achieve points-free payment.
- 🔧 **Update browser fingerprint**: Chrome version upgraded to 142

### v0.3.0 (2024-12-08)

- 🐛 **Fixed jimeng-4.5 model: Corrected model mapping names**
- ⬆️ **Version Upgrade Number**: `DRAFT_VERSION` upgraded to `3.3.4`
- ✨ **Extended Resolution Support**: Supports 1k/2k/4k resolutions.

## Technical Exchange Group

Welcome to join our technical exchange group to share your experiences:

![WeChat Image_20260413195228_3_441](https://mypicture-1258720957.cos.ap-nanjing.myqcloud.com/Obsidian/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20260413195228_3_441.jpg)

## Author Contact

- WeChat ID: laohaibao2025

![WeChat QR code](https://mypicture-1258720957.cos.ap-nanjing.myqcloud.com/Screenshot_20260123_095617_com.tencent.mm.jpg)

Acknowledgments

Thanks to the following projects for their contributions:

- [jimeng-free-api-all](https://github.com/zhizinan1997/jimeng-free-api-all)
- [jimeng-free-api](https://github.com/LLM-Red-Team/jimeng-free-api)

## License

[MIT License](LICENSE)

## Star History

If you like the project, please give it a Star ⭐

[![Star History Chart](https://api.star-history.com/svg?repos=wwwzhouhui/jimeng-free-api-all&type=Date)](https://star-history.com/#wwwzhouhui/jimeng-free-api-all&Date)
