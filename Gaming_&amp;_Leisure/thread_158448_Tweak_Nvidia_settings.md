---
title: "Tweak Nvidia settings?"
date: 2006-04-11
forum: Gaming &amp; Leisure
---

### Post by justleen on 2006-04-11
Hey All!

Can any one here give me some pointers on how to tweak my nvidia card?
Its probably some config file, but i cant seem to find it.. :(

What i would like, is to change the cards preferences, for AA/ Anisotropic filtering and such.. Basicly what you find under windows in the Nvidia settings..

Can i use the nvidia-settings package for this?  If so, how??


Feeling very silly at the moment :-k

---

### Post by Monster_user on 2006-04-11
The nVidia-settings package has those options in it, in other distros I have used.

I expect the reason Ubuntu's nvidia-settings app does not have them, is because Ubuntu does not use the official nVidia drivers.

You may have to download the Ubuntu Kernel-source package for your Kernel (2.6.12?), Then install the nVidia drivers from a bash prompt.

Here is the Breezy Badger "HowTo".
[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

---

### Post by Niko Johnson on 2009-10-14
you can get the nvidia settings by running ```
 sudo apt-get install nvidia-settings 
``` then run this as root ```
 nvidia-settings 
``` and there you go... if you are really having problems then there are a few more steps, but for the most part it looks like you already have the drivers installed  and dont need to run ```
 nvidia-xconfig
``` but it you just installed ubuntu and it looks crappy on your monitor there are a few more steps that i wont get into yet unless you ask for them, hope this helped even a little

---

