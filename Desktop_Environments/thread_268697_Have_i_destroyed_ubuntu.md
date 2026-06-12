---
title: "Have i destroyed ubuntu?"
date: 2006-09-30
forum: Desktop Environments
---

### Post by Crooksey on 2006-09-30
Well, i edited my hostname in /etc/hostname

Then i reboot, try to sudo and it says "sudo: unable to lookup <newhostname> via gethostbyname()", and adminstrative applications wont start, how can i fix this?

---

### Post by daller on 2006-09-30
Have you tried to change it back?

If you have problems under normal conditions, you can boot in recovery-mode - Press "Escape" while GRUB counts down! - And then choose "Recovery Mode" - Or what it's called!

---

### Post by Josh1 on 2006-09-30
I had this problem as well, I couldn't figure out how to fix so I just reinstalled. Lucky it was my "testing ubuntu" partition! :D.

---

### Post by Crooksey on 2006-09-30
How am i meant to edit any file out of my home directory without a sudo feature?

Lol ill try a liveCD

---

### Post by pod25 on 2006-09-30
Do you have another computer in at hand ? If so use putty to ssh across.

---

### Post by Crooksey on 2006-09-30
My LiveCD idea worked fine, so how would i go about changing my hostname so i wont have this problem?

---

### Post by Crooksey on 2006-09-30
](*,)  ./bump

---

### Post by someguyouknow on 2006-09-30
not sure for gnome but in kde, use system settings or kcontrol
network settings>domain name settings

---

### Post by CatKiller on 2006-09-30
> **Crooksey said:**
> My LiveCD idea worked fine, so how would i go about changing my hostname so i wont have this problem?

Mount your hard drive somewhere, say /mnt/linux, and then edit /mnt/linux/etc/hostname.

---

