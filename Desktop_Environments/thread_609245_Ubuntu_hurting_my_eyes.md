---
title: "Ubuntu hurting my eyes"
date: 2007-11-10
forum: Desktop Environments
---

### Post by Sh@m@n on 2007-11-10
Hi, 
I have NVIDIA 7959 GT and a Philips 17" LCD.

Ubuntu cannot offer me more then 55hz refresh rate. This is really hurting my eyes. On windows I can use my monitor with 75hz refresh rate?

what can I do? It's really painful...

---

### Post by -grubby on 2007-11-10
> **Sh@m@n said:**
> Hi, 
I have NVIDIA 7959 GT and a Philips 17" LCD.

Ubuntu cannot offer me more then 55hz refresh rate. This is really hurting my eyes. On windows I can use my monitor with 75hz refresh rate?

what can I do? It's really painful...

put this in the [right sub-forum]("http://ubuntuforums.org/forumdisplay.php?f=131") to start

---

### Post by tacutu on 2007-11-10
if you have a LCD, the refresh-rate shouldn't matter. The setting recomended by the manufacturer is in fact much lower than for the old CRT. In the case of CRT monitors, yes, the higher the refresh-rate the better for your eyes. For LCD monitors, though, it has no effect. Check your monitor manual and set the refresh-rate to the one recomended (usualy is 60).

Trust me, back in the days when I had a CRT monitor, my eyes hurt a lot. SInce I switched to LCD, no such problems! There must be something else that's causing you troubles... dunno, maybe too bright or something.

---

### Post by gatewayasteroid on 2007-11-11
> **Sh@m@n said:**
> Hi, 
I have NVIDIA 7959 GT and a Philips 17" LCD.

Ubuntu cannot offer me more then 55hz refresh rate. This is really hurting my eyes. On windows I can use my monitor with 75hz refresh rate?

what can I do? It's really painful...

For LDCs the refresh rate concept is almost senseless, it's just a matrix of pixels...anyway the standard should be 60Hz, never heard of 55...

---

### Post by bharadwaj on 2007-11-11
did you check your graphics card compatibility? and enabled restricted drivers?

---

### Post by Sh@m@n on 2007-11-11
Yes, I've enabled restiricted drivers of nvidia. But still no luck. Recommended refresh rate is 60 for my monitor, Ubuntu only offers 55

---

### Post by SunnyRabbiera on 2007-11-11
you might have to play around a bit, but tell me did you have this refresh rate issue on the live CD?

---

### Post by Sh@m@n on 2007-12-17
> **SunnyRabbiera said:**
> you might have to play around a bit, but tell me did you have this refresh rate issue on the live CD?

I cannot use live cd, due to jmicron_sata problems. installed using alternate cd.

But Fedora 8 can offer 60Hz refresh rate.

---

### Post by Jeff.J on 2007-12-18
Where are you getting the refresh rate info from?  If you're referring to the refresh rate listed under the gnome utility for changing resolution, it will not be correct after installing the nvidia proprietary drivers.  The nvidia readme for your driver explains why this is so.

Run nvidia-settings to see the correct refresh rate and change it as you like.  Remember if you want the settings to stick, you'll need to add "nvidia-settings --load-config-only" to your startup programs.  Check man nvidia-settings for more details.

---

### Post by chronic on 2007-12-18
refresh rate for LCD isn't the same as it is for CRTs. i really confused as to why its hurting your eyes, can you explain this more since i cant imagine its the refresh rate thats doing it.

but anyway if nvidia-settings doesn't work then try "sudo dpkg-reconfigure xserver-xorg"
this is the shotgun approach and it will completely reconfigure your xong.conf file
just make sure your actually using the proprietary driver and that you select "nvidia" as the driver

---

### Post by TameLion on 2007-12-18
I seem to remember having a similar problem a while back.. are you getting "scan lines" on the screen?

Set the desktop refresh rate to as low as possible (I think 50Hz?) and then the nvidia-settings refresh rate should work again (as in the above post)

---

### Post by Sh@m@n on 2007-12-18
> **Jeff.J said:**
> Where are you getting the refresh rate info from?  If you're referring to the refresh rate listed under the gnome utility for changing resolution, it will not be correct after installing the nvidia proprietary drivers.  The nvidia readme for your driver explains why this is so.

Run nvidia-settings to see the correct refresh rate and change it as you like.  Remember if you want the settings to stick, you'll need to add "nvidia-settings --load-config-only" to your startup programs.  Check man nvidia-settings for more details.

thank you Jeff.J

problem solved ;)

---

