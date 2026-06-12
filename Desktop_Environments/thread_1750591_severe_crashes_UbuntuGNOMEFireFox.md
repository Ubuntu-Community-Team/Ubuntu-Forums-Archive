---
title: "severe crashes Ubuntu/GNOME/FireFox"
date: 2011-05-05
forum: Desktop Environments
---

### Post by pierre44 on 2011-05-05
(I am new to Ubuntu and Linux in general, but I've used various variants of Unix as an ordinary user for many years.)

In brief, since I got this new machine a month ago, I have experienced repeated, severe crashes while using FireFox and the only option is to reboot.

Software:
Ubuntu 10.10 (pre-loaded) or 11.04, with GNOME
FireFox 3.6.10 (pre-loaded), 3.6.16, 4.0, 4.0.1

Hardware:
MSI G41M-P34 board with Intel E5400
Nvidia GT 210 (not using the proprietary driver)
4 GB RAM
any of a mechanical corded, optical corded, or optical wireless mouse (USB Logitech)
any of two USB or one PS2 keyboard

Seemingly at random while I'm using FireFox (but not Chrome or links2) the system stops responding. The keyboard is dead (and NumLock, CapsLock, ScrollLock keys do not light their respective LEDs), mouse clicks have no effect (but the mouse cursor usually still moves for a while), the system monitor (on top panel) freezes, and I cannot ssh into the system from another machine. Ctr-Alt-Del, Ctr-Alt-Bsp, Alt-SysReq-K have no effect. Alt-SysReq-[REISUB] does trigger a reboot (but what a bad idea it was to disable it by default! It took me days to even think of why it wasn't working!)

Curiously, if I'm playing a local mp3 when the system crashes, the song plays to the end, but never goes on to the next one.

FireFox is always running with scripts blocked (NoScript, FlashBlock) and no Java, so the usual causes of problems don't apply here. In fact I just crashed once while reading the ubuntuforums.org registration, and 4 times trying to post this, which I am now rewriting off-line to paste in later...

The crashes seem to be triggered by (mouse only?) input, such as switching tabs or windows, scrolling, or submitting a form, and may happen after as little as a minute after reboot, or as much as several hours.

The hardware (hard drive and RAM) was stress-tested according to the instructions of the vendor's tech support, and everything passed with no indication of a hardware problem. The tech seems to be rather grasping at straws at this point.

I am aware of the "log file viewer", however there are so many choices and the entries so cryptic in general that I have no idea where to even begin.

---

