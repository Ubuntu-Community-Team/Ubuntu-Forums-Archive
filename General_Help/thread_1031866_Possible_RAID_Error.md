---
title: "Possible RAID Error"
date: 2009-01-05
forum: General Help
---

### Post by cdnjay on 2009-01-05
Hi there folks,

Having the error below pop up a whole bunch of times when the system is doing pretty much anything. I'm on my third boot since install of the latest version of Ubuntu Server (all updates installed.) I'm running RAID 1 using a SATA controller card and I'm guessing this error has something to do with it. One of the drives is a bit older, 160 GB, the other drive is brand new as of today, 320 GB.

[ 159.987299] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 159.987383] ata1.00: BMDMA2 stat 0x686d0009
[ 159.987443] ata1.00: cmd c8/00:40:bf:c4:ae/00:00:00:00:00/e7 tag 0 dma 32768
in
[ 159.987445] res 51/04:2f:d0:c4:ae/00:00:00:00:00/e7 Emask 0x1 (devic
e error)
[ 159.987583] ata1.00: status: { DRDY ERR }
[ 159.987638] ata1.00: error: { ABRT }

The error didn't show up at all on first boot after install, a couple times on second boot and now a whole bunch on the third boot.

Any help that could be provided would be most appreciated!

Thanks,

Jason

---

### Post by fjgaude on 2009-01-06
Assuming you are with software raid, what does this show:

```
sudo mdadm -D /dev/md0
```

Let us know how you are doing.

---

### Post by cdnjay on 2009-01-06
> **fjgaude said:**
> Assuming you are with software raid, what does this show:

```
sudo mdadm -D /dev/md0
```

Let us know how you are doing.

I'm using hardware raid. With the two drives plugged into a controller card.

Thanks though!

Jason

---

### Post by fjgaude on 2009-01-06
When in the BIOS, the raid controller shows? Likely not. Can you use other software to look into the array to see what is going on?

---

### Post by cdnjay on 2009-01-06
> **fjgaude said:**
> When in the BIOS, the raid controller shows? Likely not. Can you use other software to look into the array to see what is going on?

It doesn't show up in the bios since it's not on the motherboard.  Rather the option to enter the menu shows up before the machine attempts to boot from a drive.  The controller is a PCI card.

The menu doesn't show any particular conflicts or problems.

Thanks!

Jason

---

### Post by fjgaude on 2009-01-06
Well, you are likely dealing with drive or controller issues... anyway to test the drives individually?

---

### Post by cdnjay on 2009-01-06
> **fjgaude said:**
> Well, you are likely dealing with drive or controller issues... anyway to test the drives individually?

I went and got a new, slightly better, controller card late today and so far no problems.  It might just have been a bad/incompatible card (fingers crossed).

Thanks for your help though!  I will post the troublesome model number here when I get back to the office, if things continue to go well.

Jason

---

### Post by cdnjay on 2009-01-06
The controller card I was using (which may not be compatible with Ubuntu Server 8.10) was model number SY-SA3512-2R manufactured by SYBA.

The controller card I am now using, which still seems to work (fingers still crossed) is the SY-SA3114-4R manufactured by Creative I/O.  The model numbers look similar because I believe the chipsets are made by the same manufacturer.

Jason

---

### Post by fjgaude on 2009-01-07
Good that you located the problem.

Hope all continues to work as you wish.

---

