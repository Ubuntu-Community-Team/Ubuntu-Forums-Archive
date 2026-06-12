---
title: "&quot;Loading hardware drivers&quot; on boot takes very long"
date: 2006-09-20
forum: Desktop Environments
---

### Post by weissed on 2006-09-20
Hi,
I noticed that my boot takes very long, and one step of them all is the one taking very much time: "Loading hardware drivers". It takes around 20-30 seconds.

Any idea how I could make this work faster? What could be the reason?

Thanks,
Eduard

---

### Post by asthro on 2007-11-01
I'v got the same problem on my Laptop, more than a minute is required to "load hardware drivers", so i'm getting bored with it...
I'm not sure, I'm trying to check some ways. Perhaps some of my drivers, which are proprietary, are not loaded. 
I will try to deactivate the hardware(old 56k internal modem) and see if I can win a lot of seconds.

---

### Post by asthro on 2007-11-01
Still me... Disabling internal modem doesn't work, either installing drivers ! 
So iTried to look the dmesg command , and i saw two bottlenecks :

[   26.874066] EXT3-fs: mounted filesystem with ordered data mode.
[   49.972000] Marking TSC unstable due to: possible TSC halt in C2.

and 

[   66.040000] ata3.01: failed to IDENTIFY (I/O error, err_mask=0x2)
[   96.708000] ata3.00: qc timeout (cmd 0x91)
[   96.708000] ata3.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x4)
[  127.376000] ata3.00: qc timeout (cmd 0x91)
[  127.376000] ata3.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x4)
[  127.376000] ata3.00: limiting speed to UDMA7:PIO5
[  158.044000] ata3.00: qc timeout (cmd 0x91)

those are the big ones... some other little ones could be improved later. So I'm exploring those ways ...

Stay tuned for more happydays !

---

### Post by asthro on 2007-11-01
I tried to configure starting services with [  sysv-rc-conf ]("http://ubuntuforums.org/showthread.php?t=89491"). It improves efficiently my bootup time, but didnt reduces my bottlenecks : 
> [   40.980000] ata3.01: failed to IDENTIFY (I/O error, err_mask=0x2)
[   71.648000] ata3.00: qc timeout (cmd 0x91)
[   71.648000] ata3.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x4)
[  102.316000] ata3.00: qc timeout (cmd 0x91)
[  102.316000] ata3.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x4)
[  102.316000] ata3.00: limiting speed to UDMA7:PIO5
[  132.984000] ata3.00: qc timeout (cmd 0x91)


still investigating !

---

### Post by asthro on 2007-11-01
Finally, I found that some CD/DVD burner could hang a bit while booting. But i've got no such device on my laptop... :-(
So I wonder what should react as a soting device : HardDrvie ? no, all is ok
CardReader,... OMG ! My brand new PCMCIA card reader ! I forgot it... 
After rebooting without this card plugged, all was ok...
So for me, I have to find the correct drivers...

If it can help

---

