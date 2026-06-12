---
title: "XORG, CPU usage and screensavers!"
date: 2006-06-06
forum: Desktop Environments
---

### Post by Onyros on 2006-06-06
Hi, guys... I'm having somewhat strange CPU usage problems with my laptop.

It has a 2.0GHz Pentium M (Sonoma), with 1GB RAM and an ATi X700 (with proper 3D acceleration through fglrx - 4250 fps in glxgears, 725 fps in fgl_glxgears).

I tried installing the i686 kernel, noticed no performance improvements whatsoever, but the laptop's fans were constantly in use, with just a few breaks in between. Therefore, I started checking out the cpu usage. I noticed that, strangely, xorg was taking up most of the resources... when idle! Even stranger, whenever I checked the system monitor out, especially its second tab where it displays graphs, cpu usage rode all the way up to 80%+.

Another strange thing I noticed, whenever I left the laptop idle for a bit, and the screensaver kicked in... the CPU throttled all the way up to 2 GHz, as if it were in great strain... and it was only the GLMatrix screensaver. Taking into account I think 3D acceleration is working well, this all added up to the total strangeness of these events.

I reverted to i386 kernel, and cpu usage is down, way down... but most of the symptoms persist. CPU usage is never as high as with the i686 kernel, but GLMatrix or other GL screensavers still present a problem, the system monitor graphs still spike my CPU usage, and the fans are still kicking in due to unusual cpu usage (lol, gotta love alliteration), but considerably less than with the i686 kernel, though.

Regarding games... I'm not much of a gamer, but I like my occasional pool game in between lumps of work. Foobillard is very choppy with this setup, but TORCS runs pretty well. I also find that strange, especially regarding the kind of results I'm getting from glxgears and fgl_glxgears.

I tried Sauerbraten... it starts with 150 fps, but whenever some other character gets in the same room... it drops as low as 10 or 15 fps, rendering the game unplayable even at 640x480.

I need your help and insight regarding this... What may be causing this? Is there anything I can do prevent this kind of irregular cpu usage, and have a better 3D performance? I'm most worried with cpu heating and the fans working a lot.

BTW, with gnome's monitoring applet, and the i386 kernel, the cpu usage is now 0% in idle, but all other problems I mentioned are still there.

---

