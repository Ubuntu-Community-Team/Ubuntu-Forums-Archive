---
title: "Ubuntu too slow"
date: 2005-10-19
forum: Desktop Environments
---

### Post by mcvedder on 2005-10-19
Hi everybody!

After installing Ubuntu today on a Pentium Celeron D 2.4Ghz / 768mb RAM computer, I been trying to use gnome and it seems that the computer is acting really slow.. I think that it's way too slow compared to XP. Could someone tell me how can I stop some services and how can I make it faster? 

thanks :-)

---

### Post by grizzly on 2005-10-19
I am having the same problems, windows 'blink' on alt-tab, pdf reader is horribly slow and firefox was also unresponsive, well i got rid of it and got Opera but its pratically impossible to use, for now.

OFFTOPIC: btw since its my first post - THANKS a lot for the free cd \\:D/

---

### Post by Alexander Kirillov on 2005-10-20
[QUOTE=mcvedder]Hi everybody!

After installing Ubuntu today on a Pentium Celeron D 2.4Ghz / 768mb RAM computer, I been trying to use gnome and it seems that the computer is acting really slow.. I think that it's way too slow compared to XP. Could someone tell me how can I stop some services and how can I make it faster? 

thanks :-)[/QUOTE]
First: this forum is for discussion of Hoary (5.04) - if you are using Breezy, post to the appropriate forum. 

However, here are some common causes of slowness:
 - some buggy application is taking up all your memory - you can check for it by using "system monitor" in Applications->System Tools menu. On my system, after login only 106 Mb of memory is used. 
 - your hard disk is running without DMA (whatever it is, it significalnly speeds up access) - can't figure out how it could happen, but who knows. Can be determined by running 
sudo /sbin/hdparm /dev/hda

- your video card. If you are using an NVIDIA or ATI (Radeon) card, you can speed it up a lot by using commercial drivers, rather than the default ones. See instruction in Tips and Trick forum.

---

