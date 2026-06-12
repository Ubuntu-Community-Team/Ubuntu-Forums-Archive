---
title: "HOWTO: Desktop Effects and ATI Radeon X1650 Pro"
date: 2007-11-05
forum: Desktop Effects &amp; Customization
---

### Post by Chewmanfoo on 2007-11-05
Hello,

After hours of trying to make desktop effects work in Gutsy on my ATI Radeon X1650 Pro (and several reinstalls of Gutsy later) I was finally successful. I thought I'd post a HOWTO in case anyone is still stuck in the same predicament.

1. Install Gutsy
2. Do NOT install any updates that are detected
3. Do NOT enable the restricted ATI proprietary driver
4. Download the latest driver from ATI's website
5. Follow the install instructions on the driver page of ATI's website, but do NOT generate a custom package for Gutsy - just perform the standard installation
6. Reboot
7. Install any updates that are detected
8. Run sudo apt-get install xserver-xgl from a terminal
9. Reboot
10. Enable desktop effects

This worked for me, after a fresh install of Gutsy. I can't promise it will work on an install that's already been tinkered with.

---

### Post by grahambo2005 on 2008-01-13
Great stuff, I'm in the same predicament.

when installing XServer did you select default which was No or yes which makes some changes.

Graham

---

### Post by joelync on 2008-02-11
I'm gonna get this a shot. I've been beating my head against the wall trying to get this X1650 pro AGP card working. I'll post my findings. Crossing all fingers and toes now!!! Wish me luck! :)

---

### Post by joelync on 2008-02-11
Is your card PCI-E or AGP?

---

### Post by browniehead05 on 2008-02-12
I have the effects and everything working but i used the restricted drivers. everything works fine for me eccept now i cant seem to play intense games cuz i dont have the proprietary drivers. not sure if i want to jack everything up trying to get them going either. if anyone has experiance with this plz help me out. ati really sucks with linux drivers

---

### Post by msjones on 2008-02-12
I have the X1650 working fine with compiz, however when viewing screen savers my machine locks and i have to do a hard reboot.

Also I cannot play back video well, its flashing constantly unless put in full screen.... any ideas?

Thanks!

---

### Post by shottie on 2008-02-12
> **msjones said:**
> I have the X1650 working fine with compiz, however when viewing screen savers my machine locks and i have to do a hard reboot.

Also I cannot play back video well, its flashing constantly unless put in full screen.... any ideas?

Thanks!

I have x2 x1650's in crossfire, i installed gutsy, enabled restricted drivers, updated system then installed CCSM.  No probs so far.

---

### Post by msjones on 2008-02-12
is video playback ok? all running smoothly with no glitches??

Did you just enable restricted drivers on a fresh gusty install without running envy? then just installed compiz after the system update??

when i enable the restricted drivers and tried to enable compiz i just got the 'composite extension not found' error, is this because I didnt update?

Thanks

---

