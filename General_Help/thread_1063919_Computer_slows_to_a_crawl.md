---
title: "Computer slows to a crawl"
date: 2009-02-08
forum: General Help
---

### Post by Donnw on 2009-02-08
When running Fldigi 3.10 on Ubuntu 8.10 it works perfectly for about 5 mins   and then the computer slows down to a crawl. checking the running processes with the top command in the terminal shows that xorg is using 90% of the cpu capacity. When Fldigi is closed everything returns to normal with xorg only using 3-5% cpu.  Any suggestions..??

---

### Post by cmapesjr on 2009-02-08
Are you using the pskviewer? It uses a lot of resources. I have found
closing it when not needed speeds things up a bit.

---

### Post by unclebeer on 2009-03-29
I'm having the same problem with fldigi 2.10 on intrepid.  Currently working on getting the new one up and running but if it's still going to do this I guess I'd better find a new program.  That sucks as fldigi has been my favorite.  Anyone know of a suitable replacement?  Or a fix to the problem?

W0BST

---

### Post by cmapesjr on 2009-03-30
I am just now getting Ubuntu 9.04a installed on the shack box.
I am going to give fldigi 3.1 a shot on this version and see how
it runs. It will be a day or two as I have to install it by hand.
I will report back soon.



Cheers
K5PHW

---

### Post by hayeduin on 2010-02-19
Hi:
 
I had the same problem when I decided to switch my digital operation (SL-USB interface) from Windows to Linux - here's the story: 
 
I upgraded from LTS to Karmic a few weeks ago and noticed a "marked decrease" in performance in Flash and Video playback which I basically ignored because I'm not into multimedia web sites. 
 
After the Karmic upgrade I installed fldigi and it ran so slow that I was about to go back to Windows.
 
Turns out the video and fldigi problems are related.
 
See the following fix for the ati driver config for Radeon video cards:
 
[http://ubuntuforums.org/showthread.php?t=1337047](http://ubuntuforums.org/showthread.php?t=1337047)
 
After I made the changes to /etc/X11/xorg.conf outlined in the post, fldigi ran perfectly.
 
GL DE KA2E

---

