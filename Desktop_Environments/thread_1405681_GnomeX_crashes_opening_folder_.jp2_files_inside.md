---
title: "Gnome/X crashes opening folder .jp2 files inside"
date: 2010-02-12
forum: Desktop Environments
---

### Post by celem on 2010-02-12
A strange problem has cropped up with gnome on my 9.10 amd64 system. Everything seems fine until I open a folder of JPG images. The window opens, starts filling in the icons and then POOF everything disappears except the desktop background. I have to restart X with CTL-ALT-BACKSPACE. It happens every time. I have used this folder many times in the past without problem.

I have proven that this is caused by the presence of two very large .jp2 images in the folder. If I use bash to move the two .jp2 image files to /tmp, I can display the folder. But guess what, then the problem moves to /tmp.

The .jp2 images are good and can be opened without problem with GIMP. I used them on Windows Xp prior to going 100% Linux. The files are good. It seems that gnome/x crashes when trying to render an icon preview for the .jp2 files.

---

