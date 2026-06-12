---
title: "Intel Integrated Graphics and Desktop Effects"
date: 2008-04-04
forum: Desktop Effects &amp; Customization
---

### Post by aristotlewilde on 2008-04-04
So my "new" motherboard has Intel Integrated Graphics.  

It seems my drivers are not whitelisted.  I am having a helluva time getting Desktop Effects working.  Oddly enough, when I boot the Hardy Beta Live CD, I have effects w/o issue.

But after installing Gutsy they never worked.  I am considering just doing a fresh install of Hardy Heron, but am afraid that once I install, I'll have the same problem.  I tried checking the xorg.conf in teh live session, but it gives me no clues.

I searched and found several people with similar issue.  No definitive answer or fix (at least one that worked for me).  Can anyone point me in the right direction to getting this working?

I don't want to have to buy a new video card just to switch desktops :) .

My motherboard info is below.

ASRock P4I65GV Intel 865GV Socket478 mATX MB w/Snd Vid LAN

---

### Post by prshah on 2008-04-04
> **aristotlewilde said:**
> So my "new" motherboard has Intel Integrated Graphics.  


This information ```
cat /etc/X11/xorg.conf | grep -i -A 3 -B 3 graphics
``` will be a good point to start solving your problem.

---

### Post by aristotlewilde on 2008-04-04
Thanks I'll have a shot at that.  Since my install was so fresh anyway, I decided to toss Hardy Beta on after all.  

I'll post progress on my issue. 

Thanks again.

---

### Post by aristotlewilde on 2008-04-04
Well lookee here!  A full Hardy Heron Beta install, and I have desktop effects!?!?!?

I guess I'll leave well enough alone.

---

### Post by dariusdwtt on 2008-04-04
Fantastic news!!!!

as I had the same problems with gutsy, and am currently in the process of downloading THE HERON   :)

---

### Post by old_geekster on 2008-04-04
> **dariusdwtt said:**
> Fantastic news!!!!

as I had the same problems with gutsy, and am currently in the process of downloading THE HERON   :)

I tried a clean install, but it didn't work.  So, I did the upgrade and it worked perfectly.  Compiz is not functioning properly, but it is not crucial to my getting things accomplished.  I will wait patiently for the update that corrects my problem and there will be one.:)

---

### Post by aristotlewilde on 2008-04-04
> **old_geekster said:**
> I tried a clean install, but it didn't work.  So, I did the upgrade and it worked perfectly.  Compiz is not functioning properly, but it is not crucial to my getting things accomplished.  I will wait patiently for the update that corrects my problem and there will be one.:)

Signature: DFI LanParty UT nF4 Ultra-D (slot 939)
AMD64 X2 4800+ (220 x12) - OCZ 5002048XTC - 2GB (2.5,3,3,7)
XFX 7900 GTX 512 MB [665/1630], SyncMaster 226BW,
Hitachi 80 GB SATAll 3.0 - 2ea. - WinXP Pro SP2/Hardy Heron 8.04 64-bit (Development)

Old Geekster, we have nearly the same systems.  I run strictly windows on my x2 4800+ system now (and it will be my Ubuntu box in a few months when I go quad core), and just put together a nice little P4 system as my dedicated Ubuntu machine for now.

---

