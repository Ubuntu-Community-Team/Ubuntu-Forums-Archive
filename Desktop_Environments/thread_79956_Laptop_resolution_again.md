---
title: "Laptop resolution again"
date: 2005-10-21
forum: Desktop Environments
---

### Post by eMuNiX on 2005-10-21
I can only get my laptop to run at 640x480, I ‘ve searched extensively on this forum and have changed my xorg.conf manually to set the screen to the 1024x768 (no joy).  I have run dpkg-reconfigure xserver-xorg and set only 1024x768 there (no joy).  Changed from S3VirgeMX to VESA and xserver won’t start.  I had it working okay in Hoary but not in Breezy, it also works fine under all other distros (I just have problems with the network card instead :s).  It’s a Compaq Armada 7400 btw.

---

### Post by Heretic09 on 2005-10-21
Try to find your laptops Vertical refresh and Horizontal sync. Manually add those to x.org conf. That fixed the 640 x 480 problem on my laptop.

---

### Post by pedro4ever on 2006-01-26
I'm having the same problem with my display in Breezy on a Compaq Armada 7400. I can't find the vert. refresh or horiz. sync info. I'd appreciate any help that can be offered.

---

