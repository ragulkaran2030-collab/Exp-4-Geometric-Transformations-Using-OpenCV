# Exp-4-Geometric-Transformations-Using-OpenCV

---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image in color mode.

### Step 3: Image Translation
- Create a translation matrix to shift the image  
- Move the image 50 pixels to the right and 80 pixels down  
- Apply transformation using `cv2.warpAffine()`  
- Display original and translated images  

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)  
- Resize the image to 2× (upscale)  
- Use `cv2.resize()`  
- Display original, downscaled, and upscaled images  

### Step 5: Image Shearing
- Create transformation matrices for:
  - Horizontal shearing  
  - Vertical shearing  
- Apply transformations using `cv2.warpAffine()`  
- Display original and sheared images  

### Step 6: Image Reflection
- Perform flipping using `cv2.flip()`:
  - Horizontal reflection  
  - Vertical reflection  
  - Both axes  
- Display all reflected images  

### Step 7: Image Rotation
- Create rotation matrices for:
  - 45° rotation  
  - 90° rotation  
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`  
- Display original and rotated images  

---

##  Program
```

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Load the image
image = cv2.imread('hockey.jpg')

if image is None:
    print("Image not found. Check the image path.")
    exit()

# Convert BGR to RGB
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

height, width = image.shape[:2]


# Step 2: Image Translation
tx, ty = 100, 50

M_translation = np.float32([
    [1, 0, tx],
    [0, 1, ty]
])

translated_image = cv2.warpAffine(
    image, M_translation, (width, height)
)

translated_rgb = cv2.cvtColor(
    translated_image, cv2.COLOR_BGR2RGB
)

plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
plt.imshow(image_rgb)
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(translated_rgb)
plt.title("Translated Image")
plt.axis('off')

plt.tight_layout()
plt.show()


# Step 3: Image Scaling
fx, fy = 0.5, 0.5

scaled_image = cv2.resize(
    image, None, fx=fx, fy=fy,
    interpolation=cv2.INTER_LINEAR
)

scaled_rgb = cv2.cvtColor(
    scaled_image, cv2.COLOR_BGR2RGB
)

plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
plt.imshow(image_rgb)
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(scaled_rgb)
plt.title("Scaled Image")
plt.axis('off')

plt.tight_layout()
plt.show()


# Step 4: Image Shearing
shear_matrix = np.float32([
    [1, 0.5, 0],
    [0.5, 1, 0]
])

sheared_image = cv2.warpAffine(
    image, shear_matrix, (width, height)
)

sheared_rgb = cv2.cvtColor(
    sheared_image, cv2.COLOR_BGR2RGB
)

plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
plt.imshow(image_rgb)
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(sheared_rgb)
plt.title("Sheared Image")
plt.axis('off')

plt.tight_layout()
plt.show()


# Step 5: Image Reflection
reflected_image = cv2.flip(image, 2)

reflected_rgb = cv2.cvtColor(
    reflected_image, cv2.COLOR_BGR2RGB
)

plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
plt.imshow(image_rgb)
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(reflected_rgb)
plt.title("Reflected Image")
plt.axis('off')

plt.tight_layout()
plt.show()


# Step 6: Image Rotation
angle = 45
center = (width // 2, height // 2)

M_rotation = cv2.getRotationMatrix2D(
    center, angle, 1
)

rotated_image = cv2.warpAffine(
    image, M_rotation, (width, height)
)

rotated_rgb = cv2.cvtColor(
    rotated_image, cv2.COLOR_BGR2RGB
)

plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
plt.imshow(image_rgb)
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(rotated_rgb)
plt.title("Rotated Image")
plt.axis('off')

plt.tight_layout()
plt.show()


# Step 7: Image Cropping
x, y, w, h = 100, 100, 200, 150

cropped_image = image[y:y+h, x:x+w]

cropped_rgb = cv2.cvtColor(
    cropped_image, cv2.COLOR_BGR2RGB
)

plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
plt.imshow(image_rgb)
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(cropped_rgb)
plt.title("Cropped Image")
plt.axis('off')

plt.tight_layout()
plt.show()
```

### Developed By:
**Name:** KARANKUMAR K

### Register No:212225040171

---

##  Output

<img width="854" height="490" alt="download" src="https://github.com/user-attachments/assets/795a0f05-19bf-47fa-8e15-8f6075986807" />

<img width="855" height="490" alt="download" src="https://github.com/user-attachments/assets/6f37955d-7f0b-4d15-8f98-0a3278fc87f0" />

<img width="854" height="490" alt="download" src="https://github.com/user-attachments/assets/f1fd0208-464e-4e7b-99ce-84fa74541e34" />

<img width="854" height="490" alt="download" src="https://github.com/user-attachments/assets/cfec0e73-c5f5-46c7-b06b-bc1d5978101b" />

<img width="854" height="490" alt="download" src="https://github.com/user-attachments/assets/997eee3f-d038-4d62-a80d-13bf3583b058" />

<img width="927" height="490" alt="download" src="https://github.com/user-attachments/assets/9600832e-52c8-422a-8473-142cc4fa476d" />


### Image Translation
- Original image is displayed  
- Translated image (shifted right and down) is displayed  

### Image Scaling
- Original image is displayed  
- Downscaled image (0.5×) is displayed  
- Upscaled image (2×) is displayed  

### Image Shearing
- Original image is displayed  
- Horizontally sheared image is displayed  
- Vertically sheared image is displayed  

### Image Reflection
- Original image is displayed  
- Horizontally flipped image is displayed  
- Vertically flipped image is displayed  
- Both-axis flipped image is displayed  

### Image Rotation
- Original image is displayed  
- 45° rotated image is displayed  
- 90° rotated image is displayed  

---

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
