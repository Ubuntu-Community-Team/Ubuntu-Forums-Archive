---
title: "Problem Streaming Audio"
date: 2006-06-23
forum: Desktop Environments
---

### Post by larry on 2006-06-23
Dear All,
I have been trying to listen to some internet radios for a few days. Some of them do not work at all and I do not understand why.
When I tried adding this url to Gxine:
[http://ogg.smgradio.com/vr32.ogg](http://ogg.smgradio.com/vr32.ogg)
it failed miserably telling it did not know how to handle it.
Helix, Xfmedia etc...did not do any better.
I am puzzled since I think I installed everything to listen to internet radio stations (I can listen to some stations included by default in Gxine).
Any suggestions?
Many thanks

Larry

---

### Post by Paerez on 2006-06-23
I would try listening to stuff using xmms to see if it is a codec problem or a gxine problem. Also, have you installed the gstreamer-ugly packages? That will help with windowsy and real and quicktime streams.

Personally I listen to somafm.com through amarok, and that works great.

---

### Post by Kouya on 2006-06-23
yoz

I tried listening to it in mplayer..works fine.

---

### Post by larry on 2006-06-25
[QUOTE=Kouya]yoz

I tried listening to it in mplayer..works fine.[/QUOTE]


Well, I do not know why but now everything works fine...
I simply rebooted my machine and now music is ok.
Cheers

Larry

---

### Post by Paerez on 2006-06-25
that may be because of linux-restricted-modules, which i am pretty sure needs a reboot to take effect, since they're kernel modules.

---

