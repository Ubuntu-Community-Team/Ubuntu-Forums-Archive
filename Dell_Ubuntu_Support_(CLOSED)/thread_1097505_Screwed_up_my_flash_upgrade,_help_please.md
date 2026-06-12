---
title: "Screwed up my flash upgrade, help please?"
date: 2009-03-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ogi010 on 2009-03-16
I'm a linux noob, and I already screwed something up on my dell mini 9.

So I thought I would get cute and try and update to flash 10, in hopes of my choppy video going away.

So like an idiot, I downloaded the tar file for adobe flash 10, ran it in the terminal and followed the prompts to get it installed.  

Anyway, it sort of installed ... firefox recognizes it in Tools -> Add-ons. 

Anyway, when I disabled flash 9 there, essentially flash no longer works.

So then I noticed the .deb package for ubuntu.  I downloaded it, installed it (with synamptic closed).  It installed fine, but when I go to youtube, I can't actually see any videos, it's as if the video portion of the page is no longer there...

Also I can't seem to get rid of flash 9 no matter what I do (I removed "flashplugin-nonfree" from symaptic but flash 9 is still shows up in firefox).

Any help would be greatly appreciated

Ogi

---

### Post by starcannon on 2009-03-16
I would probably start by trying to purge both flash installs from a command line, then reinstall flash10 using the .deb file you downloaded.
```
sudo apt-get remove  --purge flashplugin-nonfree
```
Do the same for the flash 10 .deb you downloaded.
Then reinstall the flash 10 .deb.

GL

---

