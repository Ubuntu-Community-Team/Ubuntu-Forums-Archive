---
title: "Ubuntu boots to 640x480 when monitor is off"
date: 2006-06-09
forum: Desktop Environments
---

### Post by mcewen98 on 2006-06-09
Hello.  I've searched around a bit for this, but have not turned up anything.  When I boot up Ubuntu, and either don't have the monitor turned on, or have my KVM switch set to another machine, Gnome defaults to 640x480 resolution.  If I go into the option menu to change the resolution, 640x480 is the only option available, so I then have to reboot with the monitor turned on (or the KVM switch set to that machine), and it will go into the normal 1280x1024 correctly.

Does anyone have an idea why this is happening?  I looked at the xorg.conf file, the color depth is set to 24bit.  I looked at the resolutions available that correspond to that color depth, removed everything below 1024x768, and it still boots to 640x480 with the monitor off.

Thanks.

---

### Post by mcewen98 on 2006-06-09
well.. figured it out on my own.  I ran: sudo dpkg-reconfigure  xserver-xorg

accepted mostly the defaults, picked Nvidia instead of NV for the driver, manually set the monitor sync range doing the 'simple' option.. chose 19" monitor - and it fixed the problem.

---

### Post by davescafe on 2006-06-09
[QUOTE=mcewen98]Hello.  I've searched around a bit for this, but have not turned up anything.  When I boot up Ubuntu, and either don't have the monitor turned on, or have my KVM switch set to another machine, Gnome defaults to 640x480 resolution.  If I go into the option menu to change the resolution, 640x480 is the only option available, so I then have to reboot with the monitor turned on (or the KVM switch set to that machine), and it will go into the normal 1280x1024 correctly.

Does anyone have an idea why this is happening?  I looked at the xorg.conf file, the color depth is set to 24bit.  I looked at the resolutions available that correspond to that color depth, removed everything below 1024x768, and it still boots to 640x480 with the monitor off.

Thanks.[/QUOTE]

I had this same problem - I installed Dapper through a KVM, and when I was finished, I only ever had the option of 640x480.

Solution I used: 
1.  Boot off the desktop CD
2.  At the boot screen - this is the screen where you are given the choice to "start or install ubuntu", press the <F4> key.
3.  Select the desired screen resolution for your system.  For example, in your case, you might want to select 1280 X 1024 32.
4.  Install Ubuntu like normal
Then you are done
When you reboot after install, the login screen should be in the proper, high-resolution, even though you are going through a KVM.  

If, after you log-in, your screen resolution goes back down to 640 x 480, then go to the System menu, then select Preferences, then select Screen Resolution.  You should be able to change it now to a higher resolution setting.

---

### Post by fmo on 2006-06-09
It happens to me too, if you just press CTRL+ALT+BACKSPACE it restarts X at the good resolution.

---

