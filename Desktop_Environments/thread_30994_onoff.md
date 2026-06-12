---
title: "on/off"
date: 2005-05-01
forum: Desktop Environments
---

### Post by pvphaneuf on 2005-05-01
I just installed the nvidia drivers for Ubuntu and when I restart my laptop, I wait 20 seconds then the laptop shuts itself down. I've tried to boot from a disk, but before the disk begins to run, the computer shuts itself down; actually, it won't do anything, it just shuts down... the grub loader won't even load???

---

### Post by nad on 2005-05-01
Sounds like a hardware issue. Is the machine overheated? When was the previous time you restarted? Any previous start problems? Is it set to boot from cd first?

Pull the battery, hold the power button for 30 seconds or so and let the machine rest for some time and then restart. Anything?

---

### Post by pvphaneuf on 2005-05-01
that's exactly, what I needed, I guess the thing might have overheated, causing the shutdown. Thanks for the tip. 

Though, now I have a new situation, seems after I installed the driver, I'm not able to revert to my original screen resolution of 1440x900 and am stuck on the 1280x800. Would you know how to fix that?

---

### Post by nad on 2005-05-01
Glad that helped.

There are several issues with the nvidia driver. I believe that one of the problems is that installing the nvidia driver incorrectly reconfigures your xorg.conf file. You may need to add display resolutions. Search these forums for the correct answer.

---

