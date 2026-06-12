---
title: "Load Average"
date: 2007-04-13
forum: Desktop Environments
---

### Post by justin on 2007-04-13
I am running Feisty on an AMD Athlon X2 5200+ 2.6 GHz with 2 GB of ram.

Currently, when I run the uptime command, I get something like the following:

justin@rain:~$ uptime
 16:39:23 up 1 day, 22:03,  6 users,  load average: 1.09, 1.05, 1.01

On another computer running Feisty, a Dell Dimension 3000 with a 2.8 GHz P4 with 512 MB ram, also used as a desktop, the uptime command results in:

justin@snow:~$ uptime
 16:36:49 up 15:12,  2 users,  load average: 0.00, 0.01, 0.04


Why is it the load average is so much lower with the Dell Dimension, even though the hardware is slower?

What confuses me more is that the P4 runs Gnome, while the AMD is running a much lighter window manager, pekwm. Any ideas?

---

### Post by kidders on 2007-04-13
Hi there,

Your load averages are an indicator of how much work you're making your CPU do. (Sorry for stating the obvious!) The point is though that only you will know why one is so much higher than the other.

If nothing immediately obvious crops up in an examination of your system logs & process lists, there are a few applications (often used for benchmarking) around that can keep an eye on processes *for* you over time ... so, over the course of a few hours, you can build up a picture of what's eating your CPU time.

Possible causes include large amounts of I/O (particularly with the more CPU-intensive filesystems), malfunctioning applications, simply running more stuff for longer, graphics card misconfiguration, and so on...

---

### Post by energiya on 2007-04-14
Use "top" or "htop" (my favorite) to check what processes use your CPU. This is not Windows, so you will see what process eats your resources and how much of them ;)

---

### Post by justin on 2007-04-15
A gdm process was using 100% of core 1 of my cpu. I had uninstalled it and the rest of gnome, but I guess it kept running. I completely forgot about htop. Thanks for the responses. :D

---

### Post by shae on 2007-04-15
Your AMD machine was on for almost 2 days with daily use.  The intel machine was on for 15 hours.  Now lets say that 8 of those hours everyone was sleeping.  If I had to guess this is why.  Differences in workload and usage.  And of course:

Woe to you your average workload is 1%

Here is mine:

top - 22:07:38 up 11:03,  2 users,  load average: 0.14, 0.25, 0.17


Also notice how one was 2 users vs the other being 6 users.  If I had to guess that means you have more than one person using that computer.  Again workload.

---

