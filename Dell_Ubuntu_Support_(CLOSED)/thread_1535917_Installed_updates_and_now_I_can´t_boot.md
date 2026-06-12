---
title: "Installed updates and now I can´t boot"
date: 2010-07-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TheBearNecessities on 2010-07-21
Hi, I´m new to this forum and very new to linux.
 
I have a dell netbook and installed ubuntu 9.10 on it. It works great and v happy. until last night when i clicked a few buttons to download and install all the updates (im sure it was about 280 files totalling around 250 MB).
 
Since that doenload I can no longer boot.
 
I get a "fsck from util-linux-ng 2.16" message.
 
then i get a few lines saying some processes terminsted with status 1 for example "udevtrigger main process", "udevtrigger post-stop process", then the next line "udevmonitor main process" is "killed by TERM signal.
 
the final line involves the "networking main process (464) terminated with status 1"
 
Im then left hanging, i.e I have what is presumeably some king of command prompt but I do not have ubuntu :(
 
Im on holiday and wouldn´t normally bother with it till i get back but my wife is really dissapointed she cant skype and facebook etc from the room and pool-side like she was able to in the firs week.
 
anyone seen this issue before? any easy fixes? for a newbie to try? :D

---

### Post by amsterdamharu on 2010-07-21
In the grub menu there might be an option to start with an older kernel. The grub menu can be seen when you press the up or down arrow keys while starting up (I assume ubuntu does not hide the menu).

When you are in the commandline you can log in and then type:
```
sudo /etc/init.d/gdm start
```This will start the graphic part of ubuntu or give you an error we can work with.

Oh yea and don't (auto) update, update when you have time to fix problems.

---

