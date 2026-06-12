---
title: "visual response becomes untolerably slow with high resolution or extended desktop"
date: 2008-12-03
forum: General Help
---

### Post by juamez. on 2008-12-03
As said in the thread title. I have a laptop with an Intel Pentium M 1.87GHZ and an intel 915 chipset. The amount of ram is 2GB, which should be plenty.

So back in the days of Hardy I ran compiz fusion quite fine on full blast with this laptop. At one point, though, I got myself a 24" tft monitor. It seemed that my laptop became slower the minute I plugged the monitor onto the laptop. After some fiddling around I noticed Compiz slowing down the place, so I disabled that. Without compiz it was a lot better, but still not as blitzy as it should be.

Now I just installed Intrepid and thought to make full use of the possibility to use my big screen and the laptop together as an extended desktop - the same setup that I use in WindowsXP. I noticed it asked me to enable virtual resolution or something like that to support the resolution that makes up the extended desktop due to constraints on real resolutions. My 24" runs at 1920x1200 and my laptop at 1400x1050 so I figured that to be true.

After confirming this virtual resolution I had to log out and log back in. After logging in I noticed compiz was disabled and would not turn back on. Probably because of that virtual resolution thingie. What boggled me was the horribly slowness I felt when moving things around on the screen and when scrolling in multiple webbrowsers. The screen refresh was just unable to keep up with me. I could see tearing from the slow screen image buildup. Right now I back to a single screen setup (only the 24" monitor, the laptop screen is disabled) to bypass that virtual resolution. All is well now, but it still can do better. Maybe I'm such a minimalistich performance freak that I would be better off with xfce, fluxbox or something similar.

One last more grip: I notice WindowsXP is a lot faster on my machine - possibly  because it's very old - than Ubuntu is in Extended Desktop modus (e.g. Mirror Screens disabled). Why is that? I'm feeling orphaned by Canonical because of the slowly growing problem that my laptop isn't quite capable of running Ubuntu anymore.

So here is my question, finally: who else has noticed slowness when you let Ubuntu cope with rather high resolutions? Especially with compiz enabled and a not so great graphics card to handle the job.

---

### Post by stando007 on 2008-12-22
Hi! I have the same problem!
I have 22" external LCD monitor and notebook with 15" LCD. CPU is PentiumM 1.6GHZ and 1.2GB ram. I want to use extended desktop - in each monitor I want to have different apps. In windows XP this is possible and is wery smooth - did not noticed it in graphic performance. In Ubuntu 8.10 I am able to setup it like that with virtual resolution, but with extremely decreasing of graphic performance (glxgears shows 200fps instead of my "standard" 600fps). Moving windows and scrolling is terrible. Of course I have disabled all the effects. 

I hate this! I like to have monitoring stuff for work in my laptop's screen and some other applications on the large external LCD. This really sucks. In other way ubuntu is good enough and for me could be a replacement for windows xp. It's a pity that I always find something which prevent me to start using linux for 100%.

---

### Post by piponazo on 2009-01-08
I've observed the same problem with my computer. I have a 22" monitor and a system with Q9450 CPU, Asus P5Q-E motherboard, 4GB of RAM at 1066Mhz and a Geforce 8600 GT. 

When I connect the 22" panoramic monitor to the PC, The speed of the system seems to down respect with a 17" LCD monitor. It only occurs in Ubuntu, in Windows it's all ok.

Maybe a problem of optimization of Xorg or Nvidia driver?

[Sorry for my bad english :cry:]

---

### Post by juamez. on 2009-01-08
> **piponazo said:**
> I've observed the same problem with my computer. 
Maybe a problem of optimization of Xorg or Nvidia driver?


I suppose so, yes. Try disabling all Desktop Effects by going in System - Preferences - Appearance - Visual Effects, set to None and close. I noticed Ubuntu became faster, almost as fast as when using a low resolution! Isn't that what we all want?

This, of course, doesn't apply when you don't use Advanced Desktop Settings (a.k.a. Compiz).

---

