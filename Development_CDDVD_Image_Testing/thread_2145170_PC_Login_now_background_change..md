---
title: "PC Login now background change."
date: 2013-05-14
forum: Development CD/DVD Image Testing
---

### Post by Nate_is_cool on 2013-05-14
Not so much developing a program, but I do have a question about unpacking and editing an iso.

I work for a RMM company and we do alot of password resets on machines, especially when we need to re add a PC to a domain and we don't know the local user accounts. We use the software "PClogin Now" which works wonders and has saved us alot of grief. Problem is that one of our clients complained (why?) that we use 3rd party software to unlock machines and that her PC is "at risk" and now because of the higher powers we can't use the software because it doesn't have our logo and looks unprofessional. We have also experimented with the offline registry editor, but its a bit excessive. 

TL; DR If I can remove the image attached/change it to something with my company logo we can use it again. 

There is a file labeled splash.lss, but it contained a splash screen for gparted. I've tried everything I can to find the image but can't seem to get it. Here are a list of all the files on the ISO.

choice.txt
isolinux.cfg
livecd
program.mo
rd.gz
root.dat
version
boot/isolinux.bin
boot/isolinux.bt
boot/linux
syslinux/boot.msg
syslinux/options.msg
syslinux/splash.lss
syslinux/syslinux.cfg

The syslinux.cfg looks pretty interesting, unfortunately I don't have a whole lot of experience with linux.


[ATTACH=CONFIG]242585[/ATTACH]

---

### Post by schragge on 2013-05-15
To me, this doesn't look like a typical syslinux boot screen (see [screenshots](http://www.syslinux.org/wiki/index.php/Screenshots) in their wiki). If this is the start screen of a program, it's probably buried somewhere inside either rd.gz or root.dat. The former is an init RAM disk (gzipped cpio archive), the latter is probably a squashfs image, but I'm not sure. It seems to be based on Gentoo and use [fbsplash](http://fbsplash.alanhaggai.org/) (aka gensplash) to display the splash screen. I also suspect that PCLoginNow just uses [chntpw](http://en.wikipedia.org/wiki/Chntpw) internally, so perhaps replacing it with another LiveCD is an option.

---

