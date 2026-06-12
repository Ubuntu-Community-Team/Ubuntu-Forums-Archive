---
title: "fglrx and xinerama"
date: 2006-01-10
forum: General Help
---

### Post by Phage on 2006-01-10
Hi,

I had xinerama working very nicly using the "radeon" driver(or might have been "ati" not sure), but now I've switched to using the flgrx driver as it makes my DVD playback alot better or seems to, and I'd like to have 3D acceleration.

I've read that the latest version of the fglrx driver now supports xinerama, there seems to be alot of posts about using dual monitors on the forums but the situations seem slightly different to mine, the more I read the more I get confused.

So I'd like to know if xinerama can actually be used with fglrx now with the new drivers, and if so how, I've tried some trial and error in my xorg config but with no real success. Maybe someone could point out the important parts of the xorg.confg in order to get a dual setup working.

my setup is a ATI radeon 9500 using dual head for a 17" and a 19", I'd like the ability to drag windows from one screen to the other(hence xinerama) and have different resolutions and refresh rates on both.

---

### Post by Phage on 2006-01-11
any one got any tips at all?

---

### Post by viz_e on 2006-01-12
sudo fglrxconfig 
and then follow the instructions. It worked for me without tuning....

---

### Post by Plutarch on 2007-12-16
Hi, when I try to run sudo fglrxconfig, nothing happens on my machine. I have installed the fglrx driver. Is there some other package I need?
Thanks,

---

