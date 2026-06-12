---
title: "Problems regarding usplash on AMD64"
date: 2008-02-07
forum: Desktop Effects &amp; Customization
---

### Post by Ghaagsheblah on 2008-02-07
Have spent hours on trying to install new usplash for my Gutsy AMD64 installation without any major success.

Whenever i try to install a new usplash from either gnome-look or ubuntu-art i always get a blank screen after passing GRUB.

If i however install a new usplash theme from ubuntu's repositories it works without any problems. I am also able to change between usplash themes that are installed from ubuntu's repositories or installed through dpkg for 64bit architecture.

I have also tried to install the usplash switcher (32bit version installed by using --force-architecture). Whenever i start the usplash switcher it is unable to show previews of the usplash themes that are installed for 64bit architecture, it does however show previews of the themes that are downloaded from gnome-look and ubuntu-art.

After spending hours of searching for a solution online i have not been able to find anything. It does however seem to be some difference between usplash themes for 32bit and 64bit architectures. 

Is there anyone out there with more information regarding the problems with usplash for AMD64 or how to make your own themes for the 64 bit architecture? Or if someone can confirm that there actually are differences in the usplash themes between 32bit and 64bit.

---

### Post by Keith Hedger on 2008-02-07
the usplash themes are actually librarys so u cant use one compiled on a 32 bit machine for a 64 bit ( ihad to recompile all mine when i switched to 64bit!)

if you want to compile your own its quite easy just install the usplash dev package it contains an example theme, beware though that the text background and image background colours are not as stated indexed but are  some weird rgb format (so stick to black 0x000 or white 0xffff)

---

