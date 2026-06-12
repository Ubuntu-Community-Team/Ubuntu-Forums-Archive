---
title: "[SOLVED] Modify ZIP File"
date: 2009-01-03
forum: General Help
---

### Post by DivineOmega on 2009-01-03
I have a zip file containing folders with image within them. Example (within the ZIP file (not actual names)):

folder1/image1.jpg
folder1/image2.jpg
folder1/image3.jpg
folder2/image1.jpg
folder2/image2.jpg
folder3/image1.jpg

Is there a way to add a folder to this zip file, and place all of the folders within it, so the contents of the zip would be more like the following:

rootfolder/folder1/image1.jpg
rootfolder/folder1/image2.jpg
rootfolder/folder1/image3.jpg
rootfolder/folder2/image1.jpg
rootfolder/folder2/image2.jpg
rootfolder/folder3/image1.jpg

I need to do this through the command line on a server of mine, preferably without extracting the entire zip and recompressing it.

Note: The server is not Ubuntu, but CentOS. I'm looking for general Linux help.

Extra Comments: Is it even possible to edit the structure of files in a ZIP file? I'm in Windows at the moment and have tried to move the files in the ZIP file, to within the 'rootfolder', and it will not let me do so without recompressing the original files from outside the ZIP.

---

### Post by RealPSL on 2009-01-04
You can check the man pages for zip with ```
man zip
``` However I think you have to create rootfolder, unzip the contents there and then run ```
zip -r rootfolder.zip rootfolder
``` from outside rootfolder to get the best results.

Is there a reason you do not want to uncompress the data to make the change?

---

### Post by DivineOmega on 2009-01-04
> **RealPSL said:**
> You can check the man pages for zip with ```
man zip
``` However I think you have to create rootfolder, unzip the contents there and then run ```
zip -r rootfolder.zip rootfolder
``` from outside rootfolder to get the best results.

Is there a reason you do not want to uncompress the data to make the change?

The server is quite a busy web server, so I did not want to load it down any more than it already was. In retrospect, it probably would not have caused much disruption anyway.

I ended up fixed the format of the ZIP file locally by uncompressing and recompressing it, and then uploading the resulting ZIP to the server.

---

