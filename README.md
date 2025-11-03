# Digital Image Processing Assignment

## Overview
This project implements a complete digital image processing pipeline covering image acquisition, noise simulation, preprocessing, filtering, segmentation, and feature extraction.

## Assignment Structure

### 1. Image Acquisition
- Loads and displays the original image (`Image.jpg`)
- Includes error handling and validation

### 2. Noise Simulation
- **Gaussian Noise**: Added with variance=0.05 for smooth random variations
- **Salt-and-Pepper Noise**: Applied at 10% intensity for impulse noise testing

### 3. Preprocessing & Enhancement
- **Grayscale Conversion**: RGB to grayscale transformation
- **Image Resizing**: Standardized to 512×512 pixels
- **Contrast Stretching**: Applied using 2nd-98th percentile range for enhanced visibility

### 4. Noise Filtering & Denoising
Two spatial domain filters compared:
- **Gaussian Filter** (3×3 kernel, σ=1): Smooth noise reduction
- **Median Filter** (3×3 kernel): Effective for salt-and-pepper noise

**Performance Metrics:**
- PSNR (Peak Signal-to-Noise Ratio)
- SSIM (Structural Similarity Index)

### 5. Segmentation & Object Isolation
Two segmentation approaches evaluated:
- **Otsu Thresholding**: Global optimal threshold with morphological closing
- **Edge-Based (Canny)**: Edge detection with dilation, closing, and contour filling

Both methods generate normal and inverted masks, scored heuristically by coverage, component count, and fragmentation to select the optimal segmentation.

### 6. Feature Extraction (Optional)
Extracts region properties from segmented objects:
- Area (pixels)
- Centroid coordinates (x, y)
- Bounding box (x, y, width, height)
- Mean RGB color values

### 7. Result Visualization
Visual comparison of all pipeline stages with annotated regions showing IDs, bounding boxes, and centroids.

## Dependencies
```python
opencv-python (cv2)
scikit-image
PIL (Pillow)
numpy
```

## Output Files
- `GaussianNoiseColor.jpg` - Gaussian noisy image
- `SaltAndPepperNoiseColor.jpg` - Salt-and-pepper noisy image
- `GrayScale.jpg` - Grayscale conversion
- `GrayscaleResized.jpg` - Resized 512×512 image
- `ContrastStretched.jpg` - Enhanced contrast image
- `GaussianFilter.jpg` - Gaussian filtered result
- `MedianFilter.jpg` - Median filtered result
- `OtsuMask.jpg` / `EdgeMask.jpg` - Segmentation masks
- `BestSegmentationMask.jpg` - Selected optimal mask
- `IsolatedObjectsColor.jpg` - Segmented objects
- `AnnotatedRegions.jpg` - Feature visualization

## Key Findings
- Contrast stretching significantly improved object-background separation
- Median filter outperformed Gaussian filter for salt-and-pepper noise
- Otsu thresholding produced compact, homogeneous regions
- Edge-based methods captured strong boundaries but required morphological refinement
- Metric-driven mask selection (coverage + component analysis) provided robust segmentation

## Usage
Run `Assignment Code.ipynb` sequentially from top to bottom. All intermediate results are automatically saved and displayed.
