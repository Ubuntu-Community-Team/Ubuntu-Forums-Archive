---
title: "3D Speed Much Lower in Intrepid?"
date: 2008-11-07
forum: Desktop Environments
---

### Post by pbotros1234 on 2008-11-07
Sorry if this is the wrong forum, btw.

After upgrading to Intrepid 8.10, I've noticed a pretty significant difference in graphics and speed. glxgears FPS is down to about 180 with a couple things open and no compositing, when back in Hardy my FPS would be much higher. Compiz also runs MUCH worse than in hardy; the cube is very jerky, and spinning it is slow. With compiz before I could freely rotate the cube, no lag or anything, and even had a pretty nice skydome and cube caps. Switching tabs and everything also takes longer.

Computer: Dell Latitude E6400
Rated Processor Speed: 2.26 GHz
Current Processor Speed from dmidecode: 1.6 GHz (normal?)
"lspci -vv" and xorg.conf attached.
Any ideas? Kernel problem, gnome problem, compiz problem??

---

### Post by Chilldude333 on 2008-11-07
I don't really have a solution (sorry!) but I'll agree with you on things running slower (at least you know you're not going crazy).  Originally my cube would rotate flawlessly and other effects I had set up would run almost flawlessly, except now things aren't running so well(heck now my screen saver doesn't even come up sometimes!).  I upgraded from 8.04d to 8.10 and my drivers are all up to date so I don't know, I agree with you.

---

### Post by hictio on 2008-11-07
Personally, I haven't noticed the slowness on my Compaq F700, with a:

Mobile AMD Sempron(tm) Processor 3600+
GeForce 7000M (rev a2)
1 GB RAM (256 MB assigned to video)

> 
Current Processor Speed from dmidecode: 1.6 GHz (normal?)


Yes, it is normal, as it steps down the speed to reduce heat & power consumption.

---

### Post by mlapaglia on 2008-11-07
I run Ubuntu on a Geforce 8600GTS and a Geforce Go 7600, both running just fine with Intrepid.. If anything compiz is much more stable than it ever has been also..

---

### Post by pbotros1234 on 2008-11-07
Well after some googling I found a bug report on this, so it seems others do have this problem. I'm guessing this is more hardware/driver related then the actual compiz software, so not sure what to do.

If it means anything, I have an Integrated Graphics card, with 1 GB of video memory, and total 2 GB of RAM.

Anyone have any ideas? Any options to open compiz with that would help?

---

### Post by Skripka on 2008-11-07
> **pbotros1234 said:**
> Well after some googling I found a bug report on this, so it seems others do have this problem. I'm guessing this is more hardware/driver related then the actual compiz software, so not sure what to do.

If it means anything, I have an Integrated Graphics card, with 1 GB of video memory, and total 2 GB of RAM.

Anyone have any ideas? Any options to open compiz with that would help?

Hmmm...I'd wager you integrated graphics are the issue here, now that you mention it.

---

### Post by kdevil on 2008-11-10
Sadly, I don't think it's just integrated graphics.  I'm having the same sort of problem after installing Intrepid, and I'm using an nVidia card.  My framerate in Team Fortress 2 seems to have been halved.

---

### Post by gregphil on 2008-11-10
Did you check if Intrepid (actually the new restricted nvidia driver required) actually supports your video card?  If you can believe it the new nvidia driver lacks support for many legacy nvidia cards (like a 4 year old Mx440 etc).  The new distribution 8.10 won't use the old restricted drivers.

It you have support you should be able to open "System-Administration-NVIDIA X Server settings" and not get an error box.

Good Luck.

---

### Post by kdevil on 2008-11-10
Yeah, my card is supported (it's not THAT old, even if it is going for $30 on Newegg).

I tried reinstalling Steam and Team Fortress 2, just to make sure it wasn't the game itself, but the slowdown is still there.

On a related note, games using DOSbox (Warcraft II, etc.) have been unplayable after moving from Hardy to Intrepid.  Massive slowdown, sound stuttering, etc, which makes me think this isn't just a graphics issue.

---

