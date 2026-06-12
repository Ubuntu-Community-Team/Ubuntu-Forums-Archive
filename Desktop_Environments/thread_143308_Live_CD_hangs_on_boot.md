---
title: "Live CD hangs on boot"
date: 2006-03-12
forum: Desktop Environments
---

### Post by SteveHoffmanUK on 2006-03-12
Did a search of the forum and didn't find this problem anywhere, so here goes ...

I am trying to run the Live CD of 5.01 on my desktop machine (1.53GHz, AMD Athlon XP, 128K prime memory, 256 secondary). The booting hangs at the point "Starting Enterprise Volume Management System". Note that the display changes from the ubunto brown text to the larger white-on-black text but continues to hang (don't know whether this is significant).

I have ruled out a faulty disk because it has worked successfully on my Dell laptop, but, just to make sure, I re-downloaded the Live ISO file and reburned the CD at slowest (4) speed, but it didn't help.

Also I booted with and without acpi=off, and this hasn't helped.

Any suggestions on what to do to get the live CD to boot? 

I am very impressed at ubunto's look and performance on my laptop and am eager to go live on my desktop, but I need to see how it works in Live mode first, particularly how it deals with my peripherals and wireless peer-to-peer network setup.

Thanks

---

### Post by kittycatsexycat on 2006-03-12
what cd drive are you using? try in a 32 speed cd drive... or something similar (old drive)....

make sure that your your first opition to boot from is the cd drive by going in to the setup at the start of a boot....

---

### Post by Peter41az on 2006-03-12
I have this same issue on an HP Slimline s7320 I have except it would hang at the hotplug subsystem. I later found Ubuntu didnt like the USB architecture of the HP Slimline, and the intel onboard surround sound, which doesnt work on any distro to date. . Sadly, i ended up installing Suse 10 on that one. 

What motherboard do you have? is this a production computer or built?

---

### Post by SteveHoffmanUK on 2006-03-12
Thanks for the replies. To answer the questions so far:

kitty:
CD drive: LITE-ON LTR-48246S. I'm afraid I don't have any old, slower CD drives lying about. My first option is boot from CD, and the boot process begins OK, it just hangs part way through.

Peter:
I also had the hangup at hotplug subsystem with my Dell laptop after I installed Ubuntu whenever any external peripheral (USB, floppy drive etc) was plugged in at boot-up time. I worked around it by making sure nothing was plugged in, and it no longer hung. That's OK with a laptop, but I don't really want to unplug all my peripherals from my desktop machine!

Motherboard: Jetway Skt-A V600DAP; Bus Clock is 133 MHz; this is a built desktop, not production.

---

### Post by SteveHoffmanUK on 2006-03-17
Can anyone help? Thanks

---

