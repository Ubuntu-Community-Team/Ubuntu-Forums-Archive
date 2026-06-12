---
title: "gdm broken"
date: 2008-11-26
forum: Desktop Environments
---

### Post by Glaxed on 2008-11-26
I use Arch Linux as my main OS, and Windows on my laptop.
I have installed Xubuntu using Virtualbox on my laptop, so I can work with code properly on-the-go.

The problem arose when I un-installed gdm.
I rebooted, logged in, and typed "**startx**" - however, X couldn't find any screens and died.

So, I re-installed gdm and rebooted... the terminal flickered 4 times. I logged in again through the terminal, installed sysv-rc-conf, and played around with the init-levels of xserver-xorg and gdm. After 6 failed attempts, I gave up.

At this point, I had already tried appending "/usr/sbin/gdm &" before "exit 0" in /etc/rc.local. I had also tried "dpkg-reconfigure -phigh xserver-xorg", and the same for the gdm package.

I already have Xubuntu configured the way I like it, and I'm reluctant to install another OS.

Any help on fixing the gdm situation is appreciated,
- glaxed

---

### Post by Glaxed on 2008-11-26
Never mind guys, I'd rather just use Arch.

Though hopefully, there is a solution to this eventually.

---

