---
title: "convert .gif files to .avi videos"
date: 2009-04-18
forum: General Help
---

### Post by sadicote on 2009-04-18
I have installed ffmpeg from Synaptic but this is what happens:
sade@sade-desktop:~$ convert '/home/sade/Documents/avatar_1218.gif' /home/sade/Documents/avatar%05d.jpg
The program 'convert' can be found in the following packages:
 * imagemagick
 * graphicsmagick-imagemagick-compat
Try: sudo apt-get install <selected package>
bash: convert: command not found
sade@sade-desktop:~$

Edit: Sorry for the bother, installed imagemagick and graphicsmagick from Synaptic and now it works, except for the poor picture quality, of course.

---

### Post by Fred Bear on 2009-05-04
The solution that I have found is a Windows program called VirtualDub.  In order for VirtualDub to run in Ubuntu or any other Linux distribution, you must first install Wine.

> sudo apt-get install wine

You can get VirtualDub from:
> [www.virtualdub.org](www.virtualdub.org)

Look at the file that I attached.  Now, look at the same file converted to .avi format:

---

