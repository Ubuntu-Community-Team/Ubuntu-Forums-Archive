---
title: "A big problem !"
date: 2008-07-26
forum: Desktop Environments
---

### Post by kiran88pnjr on 2008-07-26
Hai,

I am currently using Ubuntu 8.04. I am one of that linux users waiting for the release of Kubuntu 8.04 so that we can use KDE 4  very firstly. I downloaded an image and wrote it on a CD. But after the Installation I can't log into the desktop even after entering the correct password & username. The splash screen loads evrything except Dolphin. I assumed this because the last icon in the splash screen (K icon) loaded and stopped for some time and then returned back to the login screen.We tried KDE4 of Fedora Sulphur too. But result was the same. Try to help me. Is this a bug of KDE ?

---

### Post by upchucky on 2008-07-26
You may want to post this in the installations and upgrade forum, it will get better attention there.

it seems that the installation may be having trouble with the Video card to get the desktop working, however you do need to post some machine specs, and the output of some files before anyone can figure out where the problem is.

things to post are the contents and/or results of, ```
fdisk -l
``` this shows the drive geometry of your partitions and helps to find any boot problems
 
your /boot/grub/menu.lst file  this shows what os to be booted.

your /etc/X11/xorg.conf  this shows how the graphical display is set up

they will help in solving the problem, in the mean time search the forums for information on Video cards, grub loader, menu.list, and xorg.conf

there are hundreds of posts that have clues or even exact information if the system is the same as yours.

if you can boot and get a graphical display with the live cd without doing an install to the hard drive then the information on the boot messages has clues on the video setup, this will be a generic setting but the generic setting need to be put into the right files when you do the actual install, this is done from the command line.

---

