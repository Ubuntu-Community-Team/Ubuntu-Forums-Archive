---
title: "Sound isn't working after recent updates"
date: 2009-03-20
forum: General Help
---

### Post by RonB123123 on 2009-03-20
At first I thought sound wasn't working in flash until I was unable to hear music played using Rhythmbox.

How can I fix this?

---

### Post by mister_p_1998 on 2009-03-20
Mine too, every time they do a kernel update it kills the sound, either choose the previous kernel, or wait, it'll come back on in a few days.
Steve

---

### Post by RonB123123 on 2009-03-22
I tried my previous kernel: Ubuntu 8.10, kernel 2.6.27-9-generic

but I got the same problem. Could it be the new updates to gstreamer?

---

### Post by redenex on 2009-03-22
oh! so is this a kernel problem? I bought a new laptop 4 days ago and installed 64 bit Ubuntu and I thought it was a 64 bit problem!! Good to see that it is not.

---

### Post by sandyd on 2009-03-22
> **redenex said:**
> oh! so is this a kernel problem? I bought a new laptop 4 days ago and installed 64 bit Ubuntu and I thought it was a 64 bit problem!! Good to see that it is not.
could you both to 
```

sudo lspci

```

i just encountered the same problem, ubuntu somehow wiped up my /etc/modules file.

that stopped m my sound driver from loading.
i added the sound driver back into /etc/modules and tada! sound back again :).

---

### Post by sandyd on 2009-03-22
> **mister_p_1998 said:**
> Mine too, every time they do a kernel update it kills the sound, either choose the previous kernel, or wait, it'll come back on in a few days.
Steve
it kills the sound cuz they seem to wipe up /etc/modules each kernel update

or at least for me they do

---

### Post by RonB123123 on 2009-03-22
My sound seems to only work with my speakers plugged in.

I looked at my /etc/modules file and this is what it contained:
> 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2


also this is what the command "sudo lspci" gave me in the terminal:
> 
$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
09:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


Any way to fix my sound without my speakers or head phones?

~Ron

---

### Post by cpthk on 2009-03-22
same thing here, any solution?

Thanks.

---

### Post by RonB123123 on 2009-04-04
Problem is still there. So is there any way to fix it?

---

### Post by namur on 2009-04-07
I just installed the recommended update ( a rather lengthy process).
Next, I restarted my computer (Dell Inspiron 6000-Ubuntu 8-10)

And I was rather taken aback when I discovered that I have no more sound.
No music. Can't play a music file

When I click the Icon on the upper right panel, I get an error message:
"The right GStreamer plugin is not installed"

Now, I am 100% sure everything was OK BEFORE the update.
So my conclusion is that there must be a bug in the updates ?

Has anyone the same problem?

How to fix it ?

Thank you in advance
Best regards

---

### Post by JECHO on 2009-06-04
same problem

---

