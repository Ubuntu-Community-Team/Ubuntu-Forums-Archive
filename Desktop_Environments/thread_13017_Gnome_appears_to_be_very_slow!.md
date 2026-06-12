---
title: "Gnome appears to be very slow!"
date: 2005-01-28
forum: Desktop Environments
---

### Post by Sham on 2005-01-28
I have a dual Xeon with 2 Gb RAM and a 140 GB scsi hard disk. I've installed Warty and I've just installed the nvidia driver for a 128 mb fx5600.

The problem is, the desktop appears to be running reeeally slowly. Even doing something simple like a "ls -la -h" in a terminal causes the file names to ne listed in a stuttering manner.

"top" doesn't show any crazy processes running, so what could be the problem? I' totally bemused.

Cheers

---

### Post by albersag on 2005-01-28
Try i686 kernel. I think there is a related problem about having much memory than 768 MB

---

### Post by machiner on 2005-01-28
It's the tether, man - unleash the beast.

Last post was correct.

---

### Post by Sham on 2005-01-28
[QUOTE=albersag]Try i686 kernel. I think there is a related problem about having much memory than 768 MB[/QUOTE]

I am mate. 686-smp.

---

### Post by JsPr on 2005-01-28
You might want to check /proc/driver/nvidia/agp/status.
Check the AGP rate. If you can't find the status file then you don't run with AGP enabled.

---

### Post by Sham on 2005-01-28
[QUOTE=JsPr]You might want to check /proc/driver/nvidia/agp/status.
Check the AGP rate. If you can't find the status file then you don't run with AGP enabled.[/QUOTE]

Its there. Contents:

Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled


The terminal is really slow. I've been googling a bit, and other do have the same problem in Gnome, but I can't seem to find a solution. Has anyone else experienced anything like this?

---

