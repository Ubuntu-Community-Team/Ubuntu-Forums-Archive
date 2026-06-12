---
title: "ttys are blank on ubuntu 8.10 64bits"
date: 2009-02-15
forum: General Help
---

### Post by aribender on 2009-02-15
I'm running Ubuntu 8.10 64 bits on an LG R200 laptop. Everything works like a charm, except that whenever I try to switch to tty1 (that is, ctrl-alt-f1) the screen goes black and nothing shows up. However, I can still login (without even seeing what I'm typing) and check that it works, only not showing on screen.

A brief description of my hardware:
Intel core 2 duo t8100
2GB ram
Video Intel 965 Express


          Thanks in advance

---

### Post by indeterminate on 2009-02-15
Mine does this too. However, TTYs 2-5 all work fine.

---

### Post by gpstar on 2009-02-24
same problem for me. Nvidia 9800M GTX, all my tty's show blank screen, but i'm still able to do things in them, just can't see anything. Can't seem to find a fix for this.

---

### Post by gpstar on 2009-05-21
bump 

wondering if any fixes for this yet? The bug is still present in Jaunty. Only happens when using nvidia drivers higher than the 96.43.11 version.

i've tried the "options nvidia NVreg_UseVBios=0" workaround in /etc/modprobe.d/options that some people reported success with, but it doesn't work on laptops it seems. (though the options file is gone in jaunty, but can create your own .conf file in there and it'll do the same thing).

I also notice this gets written in my Xorg.0.log file everytime I try to switch to another tty.

```
(WW) NVIDIA(0): ACPI: Error: Unable to find the DOS (Enable/Disable output
(WW) NVIDIA(0):     switching) file path under /proc/acpi/video. The NVIDIA X
(WW) NVIDIA(0):     driver will not be able to respond to ACPI display change
(WW) NVIDIA(0):     hotkey events.

```

also attached is my Xorg.0.log file.

specs
nvidia 9800m gt
nvidia driver version 180.51

---

### Post by gpstar on 2009-05-21
ok finally solved this blank tty problem.

beta driver version: 185.18.10 solves the problem, all the virtual tty's now work.

can grab the beta driver from here

[ftp://download.nvidia.com/XFree86/Linux-x86_64/185.18.10/](ftp://download.nvidia.com/XFree86/Linux-x86_64/185.18.10/)

or can install it from here and stay up to date when new versions come out.

[https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)

---

### Post by poisoneggs on 2009-09-02
I have the same problem, except that I don't have an nvidia card...

---

