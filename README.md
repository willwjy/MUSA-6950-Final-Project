# Sun Exposure and Extreme Heat Risk Mapping Project

This project maps direct sun exposure and estimates extreme heat risk across Grove Hall, Boston, using Google Street View panoramas and an AI segmentation model.

---

## Project Workflow

1. **Data Collection**
   - Download Google Street View panoramas (coordinates, yaw, pano IDs, images).
   - Use the Google Maps Street View API.

2. **Sky Segmentation (AI Inference)**
   - Apply the EfficientViT model (`efficientvit-seg-l1-cityscapes`) for sky segmentation.
   - Process panoramas using PyTorch for semantic segmentation.

3. **Fisheye Projection and Yaw Alignment**
   - Reproject stitched panoramas into hemispherical fisheye images.
   - Rotate images based on yaw metadata to north-align the sky.

4. **Sun Path Simulation**
   - Simulate daily sun positions in July 2024 using the `pvlib` solar position model.
   - Calculate average daily direct sun exposure by overlaying the sun path onto the fisheye sky masks.

5. **Extreme Heat Exposure Estimation**
   - Define high/extreme risk areas as locations receiving more than 5 hours of direct sun per day.
   - Calculate daily extreme heat duration and categorize risk levels (Low, Moderate, High, Very High).

6. **Raster Density Mapping and Visualization**
   - Generate a rasterized heatmap of sun exposure intensity using kernel density estimation.
   - Output GeoTIFF raster files for GIS analysis in tools such as ArcGIS Pro or QGIS.
   - Produce street-level hotspot visualizations of extreme heat risk.

---

This project forms a basis for real-world heat vulnerability mapping and urban cooling interventions.
