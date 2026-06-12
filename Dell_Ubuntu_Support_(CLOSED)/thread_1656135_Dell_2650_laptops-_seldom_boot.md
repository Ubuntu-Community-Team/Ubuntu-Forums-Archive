---
title: "Dell 2650 laptops- seldom boot"
date: 2010-12-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jrnsr on 2010-12-30
Have installed Ubuntu 10.10 on a couple of Dell Inspiron 2650 laptops (both 512M memory) and when they run, they're great, but they only successfully boot up maybe 10% of the attempts.  Most of the time, the touchpad and keyboard are inoperative, but I recall sometimes the enter key gets me past my user Id to input password.  Trying to enter recovery mode isn't any better, but once into recovery, I'll boot up in safe graphics, but it is probably only running because it succeeded in entering  recovery, anyways.  I have elected to to boot up in safe graphics, but they still both freeze.

Ubuntu has searched the hardware and reports there's nothing requiring proprietary drivers installed.

After reading all the other problems posted, I figure my laptops are doing pretty darn good, but it sure would be nice not to set around starting up and shutting down, over and over.

---

### Post by Peter Cornstalk on 2011-01-08
[FONT=Courier New][SIZE=3]Edit /etc/default/grub

  Change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **acpi=off**"[/SIZE][/FONT][FONT=Courier New][SIZE=3]

After saving the file, run update-grub[/SIZE][/FONT]   [FONT=Courier New][SIZE=3]

reboot[/SIZE][/FONT] [FONT=Courier New][SIZE=4]
[/SIZE][/FONT]

---

