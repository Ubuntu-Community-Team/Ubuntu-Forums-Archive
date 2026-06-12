---
title: "pic previews not showing up in kflickr"
date: 2008-11-03
forum: Desktop Environments
---

### Post by beerorkid on 2008-11-03
I searched around and have not been able to fix this.

ubuntu 8.10 fresh install from an early beta.
Gnome

[Found this which makes sense.]("http://www.boazarad.com/image-previews-not-showing-up-in-konqueror-and-kflickr")

> Image previews not showing up in konqueror and kFlickr

I just got a new digital camera, and was annoyed that for some odd reason, konqueror and kFlickr were no longer showing image previews for pictures taken with the new camera.

The solution for this problem was simple - apparently, konqueror has a configureable limit to the size of file it displays previews of. This setting can easily be changed in konqueror through:
Settings -> Configure Konqueror -> Previews & Meta Data -> Maximum file size.

Turns out, that all the pictures from my 2 Mega Pixel cellphone camera were under 1MB in size, while the pictures from my new digital camera (set at 3 Mega Pixels) were just over 1MB. The default setting for previewable file size in my distribution was 1MB - hence the problem.

Changing the settings in konqueror also immediately solved the problem in kFlickr. 

got into gconf-editor and set /apps/nautilus/preferences/show_image_thumbnails to "always"

even rebooted and no luck.

Same thing happened to my home machine which I went through the upgrade process.

I use kflickr a bunch and figure this is some little setting somewhere and I am just not seeing it.  I load bunches of pics and put them in diff photosets and having the previews makes it much easier.  Just about to uninstall completely and try again.

---

