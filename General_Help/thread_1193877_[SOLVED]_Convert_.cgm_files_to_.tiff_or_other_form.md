---
title: "[SOLVED] Convert .cgm files to .tiff or other format"
date: 2009-06-22
forum: General Help
---

### Post by Shannon_VanWagner on 2009-06-22
I was wasting a lot of time looking for a way to open and convert *.cgm graphics files (e.g., logos from PrintMasterGold program) to another format such as .tiff, .jpg, .bmp, etc. for a customer.

There is already a thread on this issue [here]("http://ubuntuforums.org/showthread.php?t=667226"), but it's been closed for new replies, and there doesn't seem to be an indication of a solution.

Here's what worked for me:
Open the *.cgm with OpenOffice.org 3.0.1 Impress (such as the version that's installed on Ubuntu 9.04 Jaunty Jackalope by default). After opening the *.cgm file with Impress, you can then copy the image into the clipboard, and then paste it into an image editing program such as Gimp 2.6. 

From Gimp, you can then save the image to various different graphics formats such as *.jpg, *.gif, *.bmp, *.tiff, *.png, etc.

Also, PrintMaster Gold works in wine 1.0.1, even though the installation fails with an error... to make it work, you simply have to launch the PMWTHUNK.EXE and then the PMW.EXE from the ~/.wine/drive_c/pmw folder after trying the installation.

Hope this helps someone out!

Cheers!
:D

---

### Post by The Cog on 2009-06-22
You may want to look at ImageMagick. You can do things like:
**convert image.cgm image.png**
You can do it in a script for mass conversions.

---

