---
title: "Crippled on old machines -  can't disable showing window contents while dragging"
date: 2016-05-23
forum: Desktop Environments
---

### Post by anontemp123 on 2016-05-23
I'm using Lubunu on an old Pentium 4 with 256MB nVidia FX5200 video.  I like everything else about it; however, the lack of "wireframes" while dragging/moving windows is sometimes crippling.  Openbox has this feature for resizing windows, but not for moving windows.  It's an odd design choice for Lubuntu's default window manager, given the distribution is partially targeted at recycling older machines.  I know I could use icewm, but I prefer to stick with the defaults because it's easier to find support.

Thanks for reading.  Just my two cents.  Also, took me forever to realize this so thought I'd post this to help someone in the future.  I've never used a window manager missing this feature.

---

### Post by oldos2er on 2016-05-24
```
sudo apt-get update && sudo apt-get install obconf
``` Let us know if this works.

---

### Post by vasa1 on 2016-05-24
> **oldos2er said:**
> ```
sudo apt-get update && sudo apt-get install obconf
``` Let us know if this works.
I think OP is correct. AFAICT, The wireframe is effective only for resizing, not for moving. It's been that way in Openbox 3.5 and in Openbox 3.6.

---

### Post by anontemp123 on 2016-05-27
oldos2er, first sorry about OS/2.  It deserved better.  Second, obconf is included by default in my downloaded ISO, so I didn't have to install it.

Like vasa1 showed, wireframe can only be enabled for resizing.  (It's not a true wireframe, but close enough.)

Thanks for the responses.

---

