---
title: "Dell XPS15 and Linux-ACPI trouble"
date: 2011-05-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sid.mallya on 2011-05-18
Hey guys ! I use a dual booting system of Ubuntu 11.04 (32-bit) and Windows 7 (64-bit) on my Dell XPS 15.

Here are the two problem I am facing -->

1. The laptop doesn't go into 'Sleep' mode. It crashes and I have to hard reboot in order to do anything.

2. If I close the screen of the laptop, it should ideally go into lock mode, as in Windows where I have to sign back in; but on Linux, if I close the screen, it crashes and I have hard reboot again.

Both these problems occur ONLY when I am in the Linux OS. Windows works just fine.

IMO, there is a ACPI problem when I am using Linux. I earlier had Linux Mint 10 (64-bit) and faced the same issues.

On mint, I used to get the following error:

```
GLib Warning **: getpwuid_r(): failed due to unknown user id (0)
```

What could be the problem ?

---

### Post by sid.mallya on 2011-05-18
I am told that I should make the following changes in the grub file. Is this correct ?

1. sudo gedit /etc/default/grub
2. append "acpi=off" in the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash", making it -->

```
GRUB_CMDLINE_LINUX_DEFAULT="acpi=off quiet splash"
```
3. sudo update-grub

---

### Post by sid.mallya on 2011-05-30
Bump !

---

