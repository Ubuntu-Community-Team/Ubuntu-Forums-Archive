---
title: "A Few Probemsl"
date: 2005-12-04
forum: Desktop Environments
---

### Post by Rockford on 2005-12-04
Ok, here is the thing that I need to accomplish: WIRELESS INTERNET ACCESS

The wired networking was a breeze.  Anyways, I was told that it is probably best to use ndiswrapper to get it running.  So partially through the install I realize that I have to make my own kernel.  So heres when the fun starts :(.  I try to follow the instructions on this site: [https://wiki.ubuntu.com/KernelByHandHowto](https://wiki.ubuntu.com/KernelByHandHowto)  

Problems started under the source section.  When i entered the command tar jxf linux-source-2.6.8.1.tar.bz2 i got a bunch of errors saying "could not open blah blah, something like that"  so i login as root in the gui.  So i manually extract the folders to the location usr/src/.  Thats all fine and dandy, but the problems are just beginning.

Under the config section it says to navigate here "/usr/src/linux" but under my usr/src there is no linux folder, only my linux-patches and linux-source folders.  So im like wtf.  I cant get the "cp" command to work, no matter what i tried, and from then on in, no other commands work.  when i put "make menuconfig" i get the following error: "make: *** No rule to make target `menuconfig'.  Stop."  i tried make xconfig aswell.  I am really not to sure what to do now.  

If there is any other way to make wireless networking work, without making anychanges to menuconfig, xconfig or gconfig, please let me know.  the wireless card im using is a wcp11 by linksys

If you need to know, im running a sony vaio PCG-FX310 laptop.  Any help is greatly appreciated and thanks in advance.

---

