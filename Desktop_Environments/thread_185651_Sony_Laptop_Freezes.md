---
title: "Sony Laptop Freezes"
date: 2006-06-01
forum: Desktop Environments
---

### Post by gadgetwizard1 on 2006-06-01
Submitted by gadgetwizard on Mon, 2006-05-29 23:09.

Hi everyone, i have been running Ubuntu 5.04 on my Sony Picturebook C1MHP for many months now, everything works nice Jog Dial, Bluetooth, Suspend, just the camera not working but that's useless anyway.
So, decided to upgrade to 5.10. What a disaster!, Nothing worked anymore..most importantly, everything was really slow...especially boot time.
So i decided to upgrade to 6.06.RC WOW really nice..everything works..boot time good too BUT and it's a big BUT , after running for a while the whole thing just freezes! 
The only way to get out of the freeze is to hold the power button down and reboot. In addition to this some of the application buttons (Close, Next) have lines on them, when i hover the pointer over them they clean up (wierd huh?)FYI i have 6.06 RC running on an IBM X21 and so far it's been a dream.
So..anyone know why 6.06 RC freezes?
In the mean time i have had to re-install 5.04 as it's the only version that seems to work. Every other version seems to be going backward not forward.
BTW, i can run 5.04 or XP all day and it never freezes so i don't think it is a hardware fault.

---

### Post by gadgetwizard1 on 2006-06-04
OK, after re-installing 5.04 i have now run this OK for 5 days. Brilliant no freezes. Tried the 6.06 RC again today and within 2 minutes system freeze.

Can anyone tell me what's going on here? What do i need to check? Could it be a driver problem? I compared the Xorg.conf file for 6.06 against 5.04 and they looked the same. Both were using ati as the device driver.

I have, once again, returned to 5.04. 

I have also noticed that some buttons still have lines or dusruption on them, but not with 5.04. Only when using 6.06 RC. Could this be related?

Any ideas anyone?

---

### Post by DrBair on 2006-06-04
I'd be willing to bet money that its the video card drivers. Try jumping back to the 'vesa' or 'ati' driver for a while to see if it fixes it. 

Also, take a look at the last kernel logs after the system locks, there may be some clues in there.

---

### Post by gadgetwizard1 on 2006-06-05
Thanks, i will try the 'vesa' driver.

Can i assume that it's a simple case of changing the xorg.conf file to 'vesa' and then re-booting?

---

