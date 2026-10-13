AgOpenGPS Background Export for QGIS
A QGIS plugin that exports the current map canvas as a georeferenced background map for AgOpenGPS. Use it to combine satellite imagery, WMS layers, and vector overlays into a single background image for a field.
Features
- Exports the current QGIS map canvas to BackPic.png.
- Creates BackPic.Txt using the StartFix latitude and longitude read from the selected AgOpenGPS field's Field.txt.
- Includes the currently visible QGIS layers in the rendered map, including supported WMS layers, satellite imagery, and vector overlays.
- Creates timestamped backups of existing BackPic.png and BackPic.Txt files before replacing them.
- Leaves Field.txt, Boundary.txt, ABLines.txt, and other field data files unchanged.
- Provides an English-language user interface.
Requirements
- QGIS 3.22 or newer (the plugin has been run successfully with QGIS 4.2.3).
- An existing AgOpenGPS field folder containing Field.txt.
- Network access if the QGIS project uses online WMS or satellite layers.
Installation
Install from a release ZIP
1. Download the plugin ZIP from the project's Releases page.
2. Open QGIS.
3. Go to Plugins → Manage and Install Plugins… → Install from ZIP.
4. Select the downloaded ZIP and install it.
5. Enable AgOpenGPS Background Export if QGIS has not enabled it automatically.
Install from source
1. Download or clone this repository.
2. Copy the agopengps_export plugin folder into your QGIS profile's python/plugins directory.
3. Restart QGIS, open Plugins → Manage and Install Plugins… → Installed, and enable AgOpenGPS Background Export.
The QGIS profile plugin directory can be opened from QGIS via Settings → User Profiles → Open Active Profile Folder. Inside the profile, use python/plugins/.
Usage
1. Open your QGIS project.
2. Enable the layers you want to show in AgOpenGPS, for example satellite imagery, a drainage WMS layer, and field or drainage vector layers.
3. Set the map canvas to the area you want to export. The plugin exports the current canvas extent and rendered appearance.
4. It is recommended to close the target field in AgOpenGPS before exporting.
5. In QGIS, choose Plugins → AgOpenGPS Export → Export background map to AgOpenGPS….
6. Select the AgOpenGPS field folder containing Field.txt.
7. Choose the output image width and start the export.
8. Open the field in AgOpenGPS and verify that the image lines up with the field boundary and other known features.
The plugin writes these files into the selected field folder:
- BackPic.png — rendered background image.
- BackPic.Txt — georeferencing information used by AgOpenGPS.
If files with these names already exist, timestamped backup copies are created in the same folder before replacement.
Important limitations
- Static export: this is not a live WMS connection. To refresh the image or show updated data, export the background again.
- Rendered map only: the plugin exports an image, not editable GIS features. Drainage lines and other overlays become part of the image.
- Layer availability: online WMS or satellite layers must have finished rendering successfully in QGIS before export.
- Extent limit: the selected map extent must remain within ±4,000 metres of the StartFix location read from Field.txt.
- Image size: the export is limited to 15 megapixels to help prevent excessive memory use.
- Visual alignment: map projection, image extent, and field origin affect alignment. Always verify the result in AgOpenGPS before relying on it for field operations.
Safety recommendation
Test the plugin on a copy of an AgOpenGPS field first. Keep backups of your original field files. The plugin is intended to replace only BackPic.png and BackPic.Txt; it should not modify field boundaries, guidance lines, or other field data.
License
See LICENSE for the license terms.
Disclaimer
This is a community utility and is not an official AgOpenGPS product. AgOpenGPS and related names belong to their respective owners. Use the exported background at your own risk and verify alignment before operational use.
