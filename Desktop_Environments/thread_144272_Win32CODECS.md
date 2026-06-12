---
title: "Win32CODECS"
date: 2006-03-13
forum: Desktop Environments
---

### Post by phiz on 2006-03-13
I have all necessary codecs installed, I believe. My problem is that when I try to play DIVX animated cartoons downloaded from amule, they are completely scrambled. And, when I try to play the .wmv files, all my players say that the file is encrypted/scrambled and cant be played. 


Any advice on how to fix this problem? I've tried everything I could think of...

---

### Post by Zelut on 2006-03-14
You have installed the w32codecs package?

Maybe check the [Restricted Formats]("http://wiki.ubuntu.com/RestrictedFormats") wiki to see if there is anything that you have missed..

---

### Post by RAOF on 2006-03-14
[QUOTE=phiz]...And, when I try to play the .wmv files, all my players say that the file is encrypted/scrambled and cant be played. 
...[/QUOTE]
Is it possible that the .wmv files **are** encrypted/DRM'd?  If they are, you've got no chance to play them - as far as I know, there aren't any DRM strippers for wmv - assuming you have the legal right to strip the DRM, of course.

---

### Post by phiz on 2006-03-14
they are most likely DRM encrypted, because all other WMV files I come across play just fine.

---

### Post by kugelblitz on 2008-01-22
I'm not sure if this is a similar problem or not but when i try to install win32codecs I receive this error.

Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free libdvdcss2 1.2.9-2medibuntu2+build1 [36.0kB]
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free w32codecs 20071007-0medibuntu0.7.04.1 [14.3MB]
Fetched 14.3MB in 1m36s (149kB/s)                                              
Failed to fetch [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu0.7.04.1_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu0.7.04.1_i386.deb)  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I get the same error using the gutsy archive and tried feisty to see if there was a difference. Currently I am unable to play wmv or avi filetypes and am quite frustrated.

Nevermind, i tried installing outisde of the terminal and it worked

---

