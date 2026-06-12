---
title: "Keyboard and mouse stopped working"
date: 2006-07-31
forum: Desktop Environments
---

### Post by k999 on 2006-07-31
I have been running ubuntu 6.06 for a few weeks now. Yesterday, when I started ubuntu, the keyboard and mouse had stopped working, and I haven't found out how to fix it yet. I've seen other people with similar issues post here, but I haven't found anything that works for me. I have a Logitech wireless USB keyboard and a Logitech PS2 mouse. When I boot the computer, the keyboard works in GRUB, but it doesn't work in Linux. I have a dual-boot system, and both mouse and keyboard work in Windows, so nothing is physically broken.

I've tried to play around with settings in the BIOS, switching USB Legacy stuff to On, Off and Auto, but none of these seems to help. I hadn't installed an SSH server, so there's nothing I can do to log on even remotely. I have installed an ext2/3 driver in Windows, but I'm speculating that it won't access the filesystem when it isn't unmounted cleanly. I have to physically switch off the computer, there's nothing I can do to reboot nicely when no peripherals work.

I've tried to boot with KNOPPIX 5.0.1, but I'm getting some messages that I've never seen before with earlier versions of KNOPPIX: "Allowing slow USB devices some more time to register...Ok.", and "Warning:Autodetection seems to hang, please check your computers BIOS settings" and "udevd-event[3912]: wait_for_sysfs: waiting for '/sys/class/net/eth1/devices/driver' failed". Finally, after "Network devices eth1 detected, DHCP broadcasting for IP." nothing happens. Another user has described this exact situation here: [http://www.elearnit.de/knoppix/forum/viewtopic.php?p=9128&sid=8bafd0fb5dcf936909a8fdd2c640809f]("http://www.elearnit.de/knoppix/forum/viewtopic.php?p=9128&sid=8bafd0fb5dcf936909a8fdd2c640809f")

Has anyone experienced the same, and perhaps even managed to solve it? Like I say, this has worked fine for some weeks, but suddenly it stopped working, and I can't recall having changed anything to make this happen.

/k999

---

### Post by desimo on 2006-09-02
I'm having exactly the same problem.  After having used Ubuntu with a logitech wireless mouse/keyboard combo for months, the keyboard has suddenly quit working.  The mouse still functions normally.

The keyboard is still communicating with the wireless hub, because the lights on the hub which indicate whether the FUNCTION keys are on still engage when I tap the FUNCTION key.  Though the function light engages when I tap the FUNCTION key, the CAPS LOCK light does not change when I hit CAPS LOCK.

Did you ever solve your problem, k999?  

This started happening when I switched my default from GDM to XDM.  XDM has since been removed leaving GDM as the default.

Any suggestions are appreciated...
-desimo

---

