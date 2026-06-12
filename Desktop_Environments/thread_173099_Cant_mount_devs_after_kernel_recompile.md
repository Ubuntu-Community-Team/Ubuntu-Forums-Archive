---
title: "Cant mount devs after kernel recompile"
date: 2006-05-09
forum: Desktop Environments
---

### Post by nbpetts on 2006-05-09
ok, so i actually successfully recompiled my kernel from 2.6.12 to 2.6.16. Thats cool. But, i can no longer mount devices. Im talking Cd-rom, Ipod, second hd the whole works. When i do i a sudo mout -a i get this:

mount: /dev/hdb1 already mounted or /media/win busy

only, they arent, leastways not that i can figure. Usually this things will be mounted automatically, and displayed on my desktop, in places, etc...

i have done some searching and will do some more, but nothing was forthcoming. I cant think of any other diagnostic info to put here, but just give me the commands to type, and i will add it. Thanks.

---

### Post by seatea on 2006-05-09
I have never recompiled my kernel, but after the recent Breezy kernel update, I could not mount  usb devices. Following advice from another post that I found, I reinstalled gnome-volume-manager and HAL. That fixed my problem. You might give it a try. I used Synaptic and not the command line. I am still a bit command line challenged.

---

