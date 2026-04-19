# Event Attach Images

An Ecoscope workflow that matches images to EarthRanger events by timestamp and uploads them as file attachments.

## Overview

This workflow scans a folder of images, extracts EXIF timestamps, and matches each image to the nearest EarthRanger event within a configurable time window. Matched images are uploaded as file attachments to their corresponding events. A dashboard is produced showing matched and unmatched images.

## Workflow Steps

1. **Process Images** — Recursively scans the image folder, reads EXIF timestamps and camera metadata (make, model).
2. **Get Events** — Fetches EarthRanger events within the selected time range.
3. **Attach Images to Events** — Matches images to events by timestamp proximity. For ER Mobile events, the window spans from `event_time - window` to `created_at + window` to account for submission delay.
4. **Upload Images** — Uploads matched images as file attachments to their EarthRanger events.
5. **Dashboard** — Surfaces a matched images table and an unmatched images table.

## Configuration

| Parameter | Description |
|---|---|
| Time Range | Date range and timezone the camera clock was set to |
| Image Folder | Path to folder containing images (scanned recursively) |
| Event Types | Filter events by type (leave empty for all) |
| Time Window (minutes) | Matching tolerance in minutes (default: 4) |

## Supported Image Formats

JPG, JPEG, PNG, TIFF, BMP, GIF, WEBP

## Compile

```bash
./dev/recompile.sh
```
