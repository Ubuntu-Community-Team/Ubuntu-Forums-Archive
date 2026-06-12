---
title: "Latitude D630 - optical drive gone after update"
date: 2007-06-18
forum: Dell  Ubuntu Support
---

### Post by apel_2804 on 2007-06-18
Hi,

for 1,5 weeks or so I installed an security update. After a reboot I cant mount any DVD/CD cause the mountpoint /dev/hda is gone. It's Intel 965 based. And I mean the internal DVD/RW. I installed Feisty with this internal drive!  It's also not listed in "Hardware Information". Any ideas?

---

### Post by carcioni on 2007-06-18
I'm not sure about the D series machines, but my M20 CD/DVD RW shows up as /dev/cdrom not hda, but that is probably just a mapping issue with respect to IDE devices. 

Can you do a successful 'sudo mount /dev/cdrom /media/cdrom'. I am just wondering if the drive was remapped to another device node after the update for some odd reason. My disks show up a /dev/sda etc., so I expect I have a different disk controller architecture then the D series, which would account for my /dev/cdrom device.

Does 'lspci' or anything along that line show your DVD drive in any way?

Only other things I can think of immediately are the usual 'Is it plugged in?' type questions. If the drive is removable, you may want to try taking it out and putting it in again to see if it is physically disconnected or something. Do the lights on the drive go on and off during a reboot/reset ?
Is is enabled through the BIOS correctly?

Cheers
D

---

### Post by apel_2804 on 2007-06-18
It's plugged in. It works fine in Windows also it respondse pressing eject button.
lspci:
00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation Mobile SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by carcioni on 2007-06-18
Hmmm ... looks like you are not the only one.

[http://ubuntuforums.org/showthread.php?p=2811336](http://ubuntuforums.org/showthread.php?p=2811336)

Cheers
D

---

### Post by apel_2804 on 2007-06-18
Ah sorry there was allready a thread... I have the same problem, I cant use the old kernel cause then my intel card wont work...

---

### Post by carcioni on 2007-06-18
Just for clarification, which Intel card? The network card, the display card, or the host bridge. I am assuming it is the graphics card but ...

Is the driver that is acting up the same one that is available from : [http://www.intellinuxgraphics.org](http://www.intellinuxgraphics.org) ?

Don't specifically see this particular Dell model, but the same card may be used elsewhere.

Cheers
D

---

### Post by apel_2804 on 2007-06-19
the display card, it's an x3100/965 chipset and it need the newer kernel

---

### Post by cnshzj007 on 2007-06-20
I have the same problem with my D630.

---

### Post by Voland666 on 2007-06-20
I have this problem also. Can work it around in this way:
- Open a terminal
- write
```
sudo modprobe -v ide-generic
```

you should get /dev/hd(a-b-c-d) (primary/secondary master/slave), /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw depending on your configuration. The drive should also be visible in computer:/// and inserted discs should be automounted.

- If it worked, write in the terminal
```
sudo gedit /etc/modules
```

- add this line in it and save
```
ide-generic
```

Modifying /etc/fstab accordingly might be needed.
Please notice that ide-generic doesn't give you any DMA mode (and this is bad). This is just a temporary workaround, I think something should be fixed in the kernel...

---

### Post by apel_2804 on 2007-06-20
Thank's Voland! It's good to know that I'm not the only person trying to run Ubuntu on D630! Maybe we schould open an D630 thread... there are still several issues left on my
D630: sound problems, the intel gaphics problem (fixed with workaround) and the dvd drive... what's coming next? But maybe it's only a question of time... this intel centrino technology is too new!

---

### Post by cnshzj007 on 2007-06-21
> **apel_2804 said:**
> Thank's Voland! It's good to know that I'm not the only person trying to run Ubuntu on D630! Maybe we schould open an D630 thread... there are still several issues left on my
D630: sound problems, the intel gaphics problem (fixed with workaround) and the dvd drive... what's coming next? But maybe it's only a question of time... this intel centrino technology is too new!

That's a wonderful idea: Open a D630 thread.
Looking for it!

---

### Post by apel_2804 on 2007-06-22
anyone else who want an D630 thread?

---

### Post by JMAllen on 2007-06-23
You can count me in as another D630 owner with a few X3100 and CDRW issues. 

A D630 thread would be great.

---

### Post by apel_2804 on 2007-06-23
here it is: [http://ubuntuforums.org/showthread.php?t=481651](http://ubuntuforums.org/showthread.php?t=481651)

---

### Post by davidmorawski on 2007-07-12
I realize I'm bringing this thread back from the dead, but bear with me.
> **Voland666 said:**
> Please notice that ide-generic doesn't give you any DMA mode (and this is bad). This is just a temporary workaround, I think something should be fixed in the kernel...
Would it be possible for one to recompile the kernel with IDE support? Is there a non-generic module that might allow DMA mode?


Dave

---

### Post by davidmorawski on 2007-07-23
I believe this thread can be marked SOLVED :) See [here]("http://ubuntuforums.org/showpost.php?p=3058302&postcount=69") for the fix (with DMA!).


Dave

---

