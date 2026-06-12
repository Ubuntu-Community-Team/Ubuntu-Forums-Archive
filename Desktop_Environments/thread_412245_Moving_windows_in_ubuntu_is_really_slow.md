---
title: "Moving windows in ubuntu is really slow"
date: 2007-04-17
forum: Desktop Environments
---

### Post by Sp4cedOut on 2007-04-17
I just got ubuntu installed on my laptop and everything seems to be working OK, however, whenever a move a window by clicking and holding on the title bar and dragging, the window moves and refreshes really slow.

Laptop: HP dv2000
Processor: AMD Turion 64 X2
Graphics: GeForce GO 6150

---

### Post by tak1150 on 2007-04-17
what graphics card do you have? (it may be integrated w/ the motherboard)

---

### Post by WiseElben on 2007-04-17
You will want to install the nVidia drivers:

```
$ sudo apt-get install nvidia-glx
```

Then you will need to edit your xorg.conf file. First we will back up the xorg.conf file:

```

$ cd /etc/X11/
$ sudo cp xorg.conf xorg.conf.backup

```

Now that a backup is made, you can edit the file safely:

```

$ gksudo gedit xorg.conf

```

Search for the "Screen" section and replace the Device from "nv" to "nvidia". Now reboot your X by pressing Ctrl + Alt + Backspace. If you see the nVidia splash screen, then you are done.

NOTE: If X fails, you will want to replace the corrupted file with the backup. Write this down incase you need to revert:

```

$ sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

```

---

### Post by Sp4cedOut on 2007-04-18
Thanks a lot, now I realize I also can't connect to the internet.  The wireless works fine in Vista but doesn't work in Ubuntu, earlier I posted about this laptop and people said the built in wireless might needed to be configured.

here's what I've got:

$ iwconfig
eth1 IEEE 802.11/g  ESSID: "" Nickname: "Broadcom 4311"
Mode: Managed
Access Point: Invalid
RTN thr: off
Fragment thr: off
Link Quality:0
Signal Level: 0
Noise Level: 0
(all other outputs 0)

and yes, I did check if my laptops wifi was on.  Thanks in advance.

---

