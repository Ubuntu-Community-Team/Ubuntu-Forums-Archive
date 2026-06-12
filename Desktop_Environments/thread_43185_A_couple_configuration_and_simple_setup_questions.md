---
title: "A couple configuration and simple setup questions"
date: 2005-06-21
forum: Desktop Environments
---

### Post by fuag155555 on 2005-06-21
Hey glad to have kubuntu up and runnin, oh yeah.  \\:D/ 

But there are a few things that are really irking me that would be nice to know how to change. I'll order them from most important to least. Although thier all important  :^o  :-P 

1. Although I can tell it to mount my winXp partition, eg I added this line to /etc/fstab
"/dev/hda1       /mnt/winXp      ntfs    ro,user,noauto        0       0"

And it mounts ok, but it will only let my root user look at it.. eg su... ls /mnt/winXp look at it, if I try to make a device link on my desktop and look at it or ls /mnt/winXp as a normal user, it says I don't have the correct permissions..

2. In normal default kde in the plastik theme when the window is not focused, the boarder is a lighter shade of blue, not white to blend in with the rest of teh window, i think this looks ugly and it is really annoying a way around this would be great

3. Also in default 4.0.1 the trash bin is on the desktop not the kde menu bar, I would very much like to have it on the desktop, although I can find out how to take it off the menubar, I can't find out how to add one to the desktop...

These all seem like simple n00bish questions, hope I'm right on that assumption 
 :-P 

but untill then...

 ](*,)

---

### Post by TeeJay on 2005-06-21
[QUOTE=fuag155555]Hey glad to have kubuntu up and runnin, oh yeah.  \\:D/ 

But there are a few things that are really irking me that would be nice to know how to change. I'll order them from most important to least. Although thier all important  :^o  :-P 

1. Although I can tell it to mount my winXp partition, eg I added this line to /etc/fstab
"/dev/hda1       /mnt/winXp      ntfs    ro,user,noauto        0       0"

And it mounts ok, but it will only let my root user look at it.. eg su... ls /mnt/winXp look at it, if I try to make a device link on my desktop and look at it or ls /mnt/winXp as a normal user, it says I don't have the correct permissions..

2. In normal default kde in the plastik theme when the window is not focused, the boarder is a lighter shade of blue, not white to blend in with the rest of teh window, i think this looks ugly and it is really annoying a way around this would be great

3. Also in default 4.0.1 the trash bin is on the desktop not the kde menu bar, I would very much like to have it on the desktop, although I can find out how to take it off the menubar, I can't find out how to add one to the desktop...

These all seem like simple n00bish questions, hope I'm right on that assumption 
 :-P 

but untill then...

 ](*,)[/QUOTE]

try this in fstab instead

/dev/hda1       /mount/winXp  ntfs    umask=0222      0       0


to show trash can on the desktop 

Applications:  System Tools: Configuration Editor

 apps:  nautilus: desktop:

tick,   trash_icon_visible

---

### Post by Knome_fan on 2005-06-21
Hi,

1. I think you have to add unmask options to you fstab line:
[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

2. You can change the colors to your liking in the Control Center. I think it's under Look&Feel (I'm not on an English system right now), then choose color and you can start to edit the colors of every component. Tip: You can click on the part you want to change in the preview picture.

3. Put a file called trash.desktop into your user's Desktop directory and put the following into the file:
[Desktop Entry]
Type=Link
URL=trash:/
Encoding=UTF-8
Icon=trashcan_full
EmptyIcon=trashcan_empty
Name=Trash
Name[de]=Mülleimer

---

### Post by fuag155555 on 2005-06-21
Cool, that fixed everything ^ ^ but just a note, the thing I had to change to make the trash show up on the desktop is to change the Hidden=true to false schweet, my kde is bling bling again  :grin: 

I have not done a forums search yet, will go do one right after this post, but I can't seem to find a program to edit my nvidia settings, on other distros I have used nvidia-settings on this one I found an nvidia-glx-config app (note I have run apt-get install nvidia-glx and done all the necessary changes to my xorg.conf and modules. I would like to disable annoying things that slow down your drivers such as verticle sync and anistropic filtering at the driver level, I know theres an app out there made by nvidia to do this, is it in the apt system yet  :-? 

Other than that, this distro ROX!!!! definantly the best distro I've ever seen, rivals gentoo which has been my main distro for years and years, but I'm gettin sick of teh long compile times  :-P

---

### Post by fuag155555 on 2005-06-21
haha.. duh, forgot it was a seperate package.. ^ ^ This distro is majorly sweet. Although I'm a bit suspicouse of wether or not kubuntu really means anything in any language..  ;-)

---

### Post by fdoving on 2005-06-24
[QUOTE=fuag155555]haha.. duh, forgot it was a seperate package.. ^ ^ This distro is majorly sweet. Although I'm a bit suspicouse of wether or not kubuntu really means anything in any language..  ;-)[/QUOTE]
 It's just 'ubuntu' with a K in front :)

Kool Ubuntu, KDE Ubuntu, K..ubuntu  :) 

You can read more about what ubuntu means at [http://ubuntulinux.org/](http://ubuntulinux.org/)

---

