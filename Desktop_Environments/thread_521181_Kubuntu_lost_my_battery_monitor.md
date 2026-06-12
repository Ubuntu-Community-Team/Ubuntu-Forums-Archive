---
title: "Kubuntu: lost my battery monitor"
date: 2007-08-09
forum: Desktop Environments
---

### Post by k@zp3r on 2007-08-09
Hi!

I recently managed to recompile a fresh kernel from kernel.org to get better hardware support for my Thinkpad T61 laptop. After that, my battery monitor in KDE has disappeared and I cannot seem to enable it again, it doesn't show up as an applet, program or anything.

I think it's connected to my kernel update, but since this laptop is pretty new, I might have been tweaking other things that might have caused it.

I have checked that all power management features are enabled in the kernel and when I run acpi from a shell, I get the relevant info, so it doesn't seem to be a lack of kernel support.

I have tried to install klaptopdaemon instead, but I really liked the default better (had a nice view of the current cpu frequency on each of my cores.).

Of course this isn't a big issue for me, but if anyone has any idea of where to find the missing applet, it would be greatly appreciated.

Thanks!

---

### Post by k@zp3r on 2007-08-10
Replying to my self... :-)

The program I'm missing is kde-guidance-monitor. When I start this it says:

Failed to open device
No battery found.
This is not a laptop, quitting ...

Looking at the python code for powermanage.py, I see it uses some Dbus/Hal thing to figure out if my laptop has a battery, which it then decides it doesn't.

Now, my knowledge of Hal and dbus is limited to say the least (though I am aware that it's two different things).

Anyone got any ideas to why the "hal system" (not sure I know what I'm talking about here :-)) doesn't detect my battery?

As I wrote earlier, I have upgraded my kernel, but the info in /sys and /proc seems look like it should.

Any pointers would be greatly appreciated!

---

### Post by StoneDragon on 2007-12-01
same problem here, Thinkpad x61s, shows the battery, but thinks always it's on power, even if the battery is 0%...that IS an issue ;-)

---

