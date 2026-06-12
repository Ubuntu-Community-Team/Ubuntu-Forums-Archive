---
title: "Vostro 1500 video card issues?"
date: 2007-09-29
forum: Dell  Ubuntu Support
---

### Post by sned on 2007-09-29
I've looked all over this board, and tried all sorts of things, but haven't seen anything similar to the problem I have.

I have a vostro 1500, purchased in Sept 07.  GeForce 8400M GS.  I follow the instructions to installing the Ubuntu 7.04 distro, (tried both DELL specific and general release).  The screen goes black after I do the modprobe piix and exit.  However, everything still goes on.  I can hear the Ubuntu startup sound, and so assume everything but the screen is working.

Then the weird part happens.  When I boot back into windows, I get random standby's.  I can work for a couple minutes, then the computer will drop into standby mode.  If I close the screen, the computer resumes from standby mode, so it's almost opposite of normal use.  This continues until I shut down the computer completely, and let it sit for a minute or two before restarting.

I have called Dell about this, they just replaced the screen and the cable.

Any ideas?

Thanks
-Sned

---

### Post by fak3r on 2007-10-11
I don't have any ideas for you on 7.04, but I highly recommend you install 7.10 Beta on the Vostro 1500 - the desktop livecd worked perfectly, install was normal (no modprobe piix needed) and wireless (I have the intel wifi), graphics (8400gs like you) worked perfectly.  Choosing the desktop appearance I wanted kicked off the nvidia install, no probs there.  I had to do some forum work for the sound and suspend, but hey, they work fine now!  A great laptop...sorry, I don't duel boot so I have no idea on the XP issue.  If I needed XP I would just install Ubuntu on the whole disk, then run VMWare or Vserver for a virtual XP.  Keep with it, you can get everything worked (save for the modem, dunno about that) on the 1500, it's a great 'top.

---

### Post by sned on 2007-10-19
Thanks!  Turned out it was power/motherboard issue.  Dell replaced the video card, screen, cable, etc. but still had the same problem.  Finally they sent me a new machine ... this one works perfectly, no problems dual-booting at all.  

Just installed the 7.10 release, everything except sound works, so shouldn't be too hard to fix that.

---

