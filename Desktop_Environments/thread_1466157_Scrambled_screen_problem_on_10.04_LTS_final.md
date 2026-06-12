---
title: "Scrambled screen problem on 10.04 LTS final"
date: 2010-04-30
forum: Desktop Environments
---

### Post by macky_reddy on 2010-04-30
Hello,
 
I am using ubuntu 10.04 LTS final and when am running the live cd from usb am getting scrambled screen with 3 vertical bars check out the attachments or screenshots.
 
Am using a DV6000 HP laptop with AMD turion and Nvidia 7150m video adapter. Please help, ubuntu seems to be damn fast am really fascinated. My native resolution is 1280x800 and ubuntu detecting it and displaying a scrambled screen when am changing my screen resolution to 1024x768 screen seems to be adjusting and getting back to normal, but at 1280x800 having scrambled screen.
 
When am trying to update my nvida drivers to recommended current version it resulting in an error "System error: install archive () failed", please help how can i solve my scrambled screen at 1280x800.
 
Regards,
macky

---

### Post by k1llm3kw1k on 2010-05-01
I have the same issue but it seems to happen randomly. I submitted the bug but never had anyone look into it. Well needless to say I am still using 9.10 (via Mint).

---

### Post by macky_reddy on 2010-05-02
> **k1llm3kw1k said:**
> I have the same issue but it seems to happen randomly. I submitted the bug but never had anyone look into it. Well needless to say I am still using 9.10 (via Mint).
Well no worries mate i got it working. all you need to do is
 
1.  when u get scrambled screen try to reduce to a lower screen resolution from the native, if the screen comes to normal, then here are next steps to follow to avoid jockey error.
 
2. Instead of downloading and installing nvidia propertriarydrivers first do a system update. Install all the updates from ubuntu along with a latest kernel, restart and boot with the latest kernel.
 
3. now update to nvidia propertriary drivers now it install without error and everything is back to normal. It happens due to absence of xorg.conf file in the etc/x11 and dpkg gives an error while installing nvidia propertriarydrivers, so with updating the system everything comes back to life.
 
 
cheers

---

### Post by puvijain on 2010-12-04
How are you suppose to make changes with all that scambled desktop and GUI...?

---

### Post by maoptimus on 2010-12-06
I have the same problem with my DV6000 with nvidia 7150m it's difficult to set the lower resolution but it can be done, i'll try to solve this problem today and i'll post the steps ok?

---

### Post by maoptimus on 2010-12-06
the problem once you get the resolution down is so simple, you just have to install de propietary driver and problem solved ubuntu is now working perfectly in my laptop

---

### Post by freshmeatz on 2011-01-02
how is this solved? I have a dv6000 with nvidia doing the same thing, in now way can I use the GUI to lower the screen res, so this is far from a solved issue.:lolflag:

---

