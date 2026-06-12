---
title: "CPU usage too high :("
date: 2006-09-08
forum: Desktop Environments
---

### Post by xp_newbie on 2006-09-08
I recently managed to install Ubuntu 6.0.6 on an old PII 350MHz 512MB system. The installation suceeded (I am posting now from that system, using Ubuntu :)) but... it is extremely sluggish. :(

I fired up System Monitor and sure enough - even without doing **anything** in the system (i.e. not even mouse movement) CPU usage is on a steady 22%.

If I just move the mouse around (again, not running any application, except for System Monitor of course), then CPU usage jumps to 40%.

Is this normal?

If not, how do I fix that?

For ease of troubleshooting I am attaching here two files:
1. lshw.txt - captures the output of the command 'lshw'
2. top.txt  - captures the output of the command 'top'.

Any help in making this system usable would be greately appreciated.

Thanks!
Alex

---

### Post by cptnapalm on 2006-09-08
There was something odd with an option with the 6.06 kernel.  I think that it is not there with 6.06.1.

But, there is an easy workaround that does no harm.

Here's a post I made when I had that problem:
[http://www.ubuntuforums.org/showthread.php?t=216442](http://www.ubuntuforums.org/showthread.php?t=216442)

---

### Post by xp_newbie on 2006-09-12
Thanks - I did just as what you suggested and it reduced the idle CPU usage by... 2%  :)  So, the idle state usage is still around 20% and when I press submit when posting a message here, Xorg takes almost 50% of the CPU. It seems as if the CPU is doing all the graphics work instead of the graphics card (Matrox MGA-200). This is strange.

Any other ideas?

---

### Post by puddpunk on 2006-09-12
Make sure you have the correct Matrox drivers installed. Should be mga...something if I remember correctly.

Also you may be interested in Xubuntu using the XFCE desktop instead of Gnome, similar features but much lighter.

---

