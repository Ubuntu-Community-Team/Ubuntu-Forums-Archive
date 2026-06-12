---
title: "flightgear @ feisty - working slow"
date: 2007-04-21
forum: Gaming &amp; Leisure
---

### Post by nadav2605 on 2007-04-21
hello,
i have an intel 945 chipset with gma 950 graphics card integrated. i installed feisty and flightgear from synaptic and it's working very slow!! with all the rendering options to the minimal and it's like 10 fps. i have 1GB ddr2 ram, it shouldn't be so slow. also the sound is very bad quality, any suggestions how to fix these problems?

Thank you very much!

---

### Post by gjohn2 on 2007-04-23
I am having similar problems with planeshift.
same card, 1.5gb ram, direct rendering: yes
and all that. :(  help.

its dreadfully slow.

---

### Post by malmjako on 2007-06-29
Hello, I too have troubles running FlightGear on Ubuntu 7.04, with an ATI X600, using the open-source radeon video driver. I have installed FlightGear from the official repositories. With the lowest settings possible (no clouds, no fog, 640x480, etc.) I get a frame rate of between 1 and 2 frames per second. On the same computer I get acceptable performance from X-Plane, and last time I tried FlightGear (about a year ago, I would think, on Ubuntu Dapper) I had good performance. 

I haven't tried proprietary, but I think I was using them last time, when it worked. However, If it would be possible to run on the open-source drivers I would really like it. I'm also running AIGLX and Beryl. Using Beryl or Metacity as window manager makes no difference to FlightGear performance.

Any ideas?

---

### Post by hyperair on 2007-06-29
Mine works, but it's on an nVidia card, using proprietary drivers. nVidia Geforce 4 MX 440. RAM: 1.2GB and CPU: Intel P4 2.66GHz.

Only problem: after a while, the screen quivers a lil, and then it hangs the entire machine. Sometimes it'll the entire screen (not just the FlightGear window) will turn black and come back on first. But it always ends up hanging the entire machine. Even ssh won't work.I reckon the longest it's run is 15 minutes before that happens.

---

### Post by martinw89 on 2007-06-29
> **malmjako said:**
> Hello, I too have troubles running FlightGear on Ubuntu 7.04, with an ATI X600, using the open-source radeon video driver. I have installed FlightGear from the official repositories. With the lowest settings possible (no clouds, no fog, 640x480, etc.) I get a frame rate of between 1 and 2 frames per second. On the same computer I get acceptable performance from X-Plane, and last time I tried FlightGear (about a year ago, I would think, on Ubuntu Dapper) I had good performance. 

I haven't tried proprietary, but I think I was using them last time, when it worked. However, If it would be possible to run on the open-source drivers I would really like it. I'm also running AIGLX and Beryl. Using Beryl or Metacity as window manager makes no difference to FlightGear performance.

Any ideas?

Actually, using Beryl or not makes a very big difference.  Beryl utilizes your video card directly and it won't move out of the way for other 3D apps.  For me, 3D games are unplayable with Beryl but more than 60FPS without it.

Also, as far as I know, the open source ATI drivers are not good at 3D acceleration yet.

---

### Post by hyperair on 2007-06-29
I get the feeling that some software package (at its current version in the Feisty repositories) is having some sort of bug or other. I installed nexuiz not too long ago, and I could play it fine, without much lag (except when there's some huge explosion). But now, it won't last for 20 minutes without hanging (and taking the computer with it)

---

### Post by malmjako on 2007-06-29
> **martinw89 said:**
> Actually, using Beryl or not makes a very big difference.  Beryl utilizes your video card directly and it won't move out of the way for other 3D apps.  For me, 3D games are unplayable with Beryl but more than 60FPS without it.

Also, as far as I know, the open source ATI drivers are not good at 3D acceleration yet.

What I mean is, switching to Metacity instead of Beryl (from the Beryl Manager icon) doesn't improve the speed. It still doesn't do more than 1-2 fps.

Yes, I have seen that 3D acceleration is termed "experimental" on the radeon driver for my video card, but shouldn't it be possible to get approximately the same performance in FlightGear and X-Plane? 

Another thought, should I disable AIGLX or something in xorg.conf?

---

### Post by martinw89 on 2007-06-29
Oh I didn't know you meant that X-Plane was working equally as well with the same drivers.  Honestly my knowledge of ATI drivers is very limited so I can't really help.  And I see what you mean now about Metacity / Beryl.

---

### Post by ruarymac on 2007-08-02
Might not be much help but I posted a question a couple of days ago a long a similar theme.  What I found was that FlightGear was very slow and using all CPU time.  The fix I stumbled across was to change the screen resolution down to some lower value then change it back up to my origonal value.  Then FlightGear ran fine.  When starting it again the next day it failed once more and again this senario fixed it.  It has not failed since.  Possibly something to do with video drivers but I worry about it some other time as this is an easy fix.  Hope it helps you too.

Ruary

---

### Post by hyperair on 2007-08-02
Oh mine was a pretty easy fix. =P My PSU blew, then I realized that that was the problem all the while. Not enough power. It was aging, definitely, and while I could play CS:Source for n hours last time, it hung after half an hour that time.

---

