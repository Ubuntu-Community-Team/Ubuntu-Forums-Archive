---
title: "PCSX2 Dependecies"
date: 2011-05-03
forum: Gaming &amp; Leisure
---

### Post by gstla on 2011-05-03
Hey guys, I'm not sure whether you're aware or not, but the popular emulator PCSX2 for Playstation 2 has been updated to version 0.9.8.  I saw that they had a Linux port, so I wanted to install it, but I've got one problem.

gtk2, opengl, libbz2, libjpeg, glew-dev, libxxf86vm-dev,  x11proto-xf86vidmodeautomake and autoconf (version >= 1.9) Nvidia  Cg-Toolkit (link), libasound-dev, joystick 

I managed to extract the archive in the archive manager, so now I've got a folder with PCSX2 in it, but I can run it (and run a game in ISO format) but it just shows a white, blank screen.  I want to make sure that these dependencies are up to date (and if, not, install them). 

I'd appreciate the help.  I'm new to specific terminal commands, so be direct ; ).

---

### Post by Fisher on 2011-05-06
Had the same problem here :-(
But I got the binary from their site.
Installed nvidia cg-toolkit and glew, then got libZeroGSoglr.so.0.96.2 from an old harddrive backup, put it on the plugins folder and things get working, very slowly but working.
Seems that the GSNull plugin is for debuging purposes only!!
I'm really not sure if nvidia cg-toolkit was necessary, but i'm sure glew is!
I'm attaching the plugin, just uncompress it on your plugin folder, then select it on tne plugins configuration dialog.
Hope it works to you too!!

---

