---
title: "modifier keys do not work through VNC"
date: 2010-08-30
forum: Desktop Environments
---

### Post by eovnu87435ds on 2010-08-30
Hey, i've been an ubuntu user for a few years now,  I just never joined the forums since I never really had problems with my installations. Today, however, is completely different. I recently converted my server from windows 2k3 to  ubuntu server 10.04, and have been setting ssh and vnc so that I can access it remotely. both x11vnc and ssh are installed and working fine, as I can connect to the server from my macbook, but here is where it gets weird. 

When in VNC, none of the modifier keys work(shift, ctrl, alt, super) and caps lock only works half the time.(I have to press it twice to turn it on and twice to turn it off).

Any help would be appreciated, as I am clueless as to what to do at this point...

Server Specs:
Dell Poweredge 2500
1x Intel Pentium III 1Ghz (coppermine)
1GB ram

---

### Post by krunge on 2010-08-30
Try the -xkb x11vnc option.  Search these forums for x11vnc+xkb for more info.

---

