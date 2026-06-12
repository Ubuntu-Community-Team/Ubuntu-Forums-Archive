---
title: "Make something recognize GPU (Ubuntu inperticular)"
date: 2008-12-14
forum: General Help
---

### Post by inxygnuu on 2008-12-14
Hello, I bought a sony not too long ago (thrift store, long story) and I know it has an Nvidia graphics card, but I am not sure which model. Nothing will recognise it, and I want compiz, and other effects on it. Is there a software program that will recognise it? (not even windows will!)

---

### Post by Ng Oon-Ee on 2008-12-15
You could just try installing one of the legacy drivers from Nvidia (use EnvyNG, that's the easiest). You could also google the model number for your Sony to find out what GC it is normally packaged with, this hardly changes (most of the time, my ASUS for example comes with Nvidia 9300M and ATI Radeon 3450 flavours) for the same model.

---

### Post by inxygnuu on 2008-12-15
Thanks! Now I need a driver for the "Nvidia geforce 6200", or more perticularly, how to install it. On Nvidia's page, it seems like an advanced GPU.:)

---

### Post by oldos2er on 2008-12-15
If you're running Gnome, go to System, Administration, Hardware Drivers to enable the Nvidia driver.

---

### Post by inxygnuu on 2008-12-15
> **oldos2er said:**
> If you're running Gnome, go to System, Administration, Hardware Drivers to enable the Nvidia driver.

It wont show the driver. that is the reason I am posting this thread.

---

### Post by inigomontoya on 2008-12-15
Please enter this into the terminal and post the output: 

```
lspci -nn | grep VGA
```

---

### Post by inxygnuu on 2008-12-15
> 01:00.0 VGA compatible controller [0300]: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] [10de:002d] (rev 15)


Any ideas?

---

### Post by inigomontoya on 2008-12-15
If you want proprietary drivers the latest version is 71.86.07 and is available here: [http://www.nvnews.net/vbulletin/showthread.php?t=122140](http://www.nvnews.net/vbulletin/showthread.php?t=122140)

You have a Riva TNT2 not a Geforce 6200.  Your card is a few generations older.

I'm unsure if compiz works with it.

---

### Post by inxygnuu on 2008-12-15
> **inigomontoya said:**
> If you want proprietary drivers the latest version is 71.86.07 and is available here: [http://www.nvnews.net/vbulletin/showthread.php?t=122140](http://www.nvnews.net/vbulletin/showthread.php?t=122140)

You have a Riva TNT2 not a Geforce 6200.  Your card is a few generations older.

I'm unsure if compiz works with it.

The link that you gave leads to another Link, that leads to just a big webpage with the code. I copied it into gedit, and saved it as "N.run", but it gives a checksum error. Is there a link where I can get the actual file?

---

### Post by inxygnuu on 2008-12-15
and according to a Ubuntu page, that driver is in compatible with 3d acceleration. Is there way to manually enable it?

---

### Post by inigomontoya on 2008-12-15
Here is the most direct link possible: [ftp://download.nvidia.com/XFree86/Linux-x86/71.86.07/NVIDIA-Linux-x86-71.86.07-pkg0.run](ftp://download.nvidia.com/XFree86/Linux-x86/71.86.07/NVIDIA-Linux-x86-71.86.07-pkg0.run)

---

### Post by inxygnuu on 2008-12-15
is there a way to turn that into a valid .run file?

---

