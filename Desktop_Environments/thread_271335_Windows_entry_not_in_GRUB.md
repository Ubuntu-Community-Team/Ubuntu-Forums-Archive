---
title: "Windows entry not in GRUB"
date: 2006-10-04
forum: Desktop Environments
---

### Post by ThrobbingBrain66 on 2006-10-04
I installed kubuntu on my girlfriends computer today.  i was attempting to give her a dual-boot while she got used to linux.  however, the install process never added windows to the grub menu.  I never had this issue back in the day when I dual-booted.  Can someone tell me how to do this?

---

### Post by jhunholz on 2006-10-04
Assuming that kUbuntu didn't frag her Windows partition, here's the easiest way:

1. Boot into Kubuntu and open a terminal.
2. Type: sudo bash (and enter root password)
3. Type: mount /boot
4. Type: nano -w /boot/grub/grub.conf
5. Put in a new section in the grub.conf that looks something like this (assuming that hda1 is her windows partition. if it's not, then change the (hd0,0) part to something else):

title=Windows
rootnoverify (hd0,0)
makeactive
chainloader +1

6. Save the file (ctrl+o) and exit (ctrl+x)
7. Reboot the system and it should have the option there in Grub

---

### Post by ThrobbingBrain66 on 2006-10-04
thank you...i found this out about 5 minutes after I posted this and it worked fine.

---

