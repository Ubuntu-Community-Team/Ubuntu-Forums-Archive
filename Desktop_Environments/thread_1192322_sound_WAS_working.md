---
title: "sound WAS working"
date: 2009-06-20
forum: Desktop Environments
---

### Post by sylar30 on 2009-06-20
To those Ubuntu users who still may be using Ubuntu 8.1 and/or converted to 9.04:

My sound has been working fine since I installed Ubuntu 8.1.  Recently, I downloaded some updates.  Unfortunately I cannot remember what they were.   I just remember for several days all I had to pick was an intel-org-video driver.  I figured why bother downloading it if I don't need it. So, several days later (yesterday) I downloaded a bunch of new offerings that looked like they could be useful.  None of them had anything to do with my sound drivers or so I thought.  Now I just get static on start up and whenever I try to use any application that uses sound.  I figured upgrading to 9.04 might have taken out any old files causing problems.  So, I did the upgrade and I STILL have no sound.  Any suggestions?  One more thing... I have a dual boot with Linux and Windows Vista Home Premium..sound works just fine in Windows.  Please help!

---

### Post by The-Don on 2009-06-22
With updates, especially the kernel - the drivers you installed originally for your soundcard may need reinstalling for the new kernel.

What s/card do you have?

---

### Post by Pengwyn44 on 2009-06-27
I have the same problem. Sound worked fine with 8.04, now silence reigns with 9.04. My sound card is:-
04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10).
I have checked the hardware by running 8.04 again from live CD. Sound works OK with that.

I have tried substituting the etc/modprobe.d/alsa-base file from 8.04 with the alsa-base.conf file in 9.04 but no joy.
I hope someone can explain why this should have happened. Someone from Canonical perhaps?

Pengwyn44

---

### Post by Pengwyn44 on 2009-06-27
I have solved my own problem! Just shows how easy it can be to overlook the obvious yet odd default setting. Right clicking on the loudspeaker icon at the top of the screen opens a menu. The top item on the menu is "Mute".
Mine had a tick in the box! Once removed the sound IS OK.

Pengwyn44

---

