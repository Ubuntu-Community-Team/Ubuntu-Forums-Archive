---
title: "Computer speed randomly died."
date: 2009-05-06
forum: General Help
---

### Post by triunenature on 2009-05-06
Ok, so ive been having major issues since i upgraded to 9.04

But this is new.. my computer speed has been reduced to nothing...

I mean, it can't even keep up with me typing...

I don't even know where to begin.

The last thing i installed, was:

```

omega@omega-Main:~$ sudo apt-get install compiz compizconfig-settings-manager

```

Which reloved another issue i was having.

I really don't know where to begin... i havn't a clue... Ubuntu has always run very quickly... so this is kinda wierd

---

### Post by triunenature on 2009-05-06
```

top

```

xorg is using a MASSIVE amount of my computer cpu.  97% - 99% (and its not going down, just staying there.  I confermed with system monitor.

That cant be right

---

### Post by skymera on 2009-05-06
Whatr is your graphics card?

Have you installed the correct driver?

---

### Post by triunenature on 2009-05-06
> **skymera said:**
> Whatr is your graphics card?

Have you installed the correct driver?

Thats a good question, what is my graphics card... 

Um... how can i tell via Ubuntu?

---

### Post by Shunsuke_01 on 2009-05-06
> **triunenature said:**
> Thats a good question, what is my graphics card... 

Um... how can i tell via Ubuntu?

If it's an NVIDIA card, you need to install the restricted drivers.

---

### Post by triunenature on 2009-05-06
How can i tell what my driver is? 

does this help anything?

```

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
05:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
05:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)

```

Come to think of it, i dont think this computer has a graphics card... i think it has a graphics chip

---

### Post by skymera on 2009-05-06
You have an Intel chip.

The Intel chips are buggy with 9.04. This was in the release notes.

Try this:
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by triunenature on 2009-05-06
Sweet thank you.  Patch fixed it all

Yea, im using a chip not a card, due to the fact this computer was...well free...

Thanks a bunch

---

### Post by skymera on 2009-05-06
I'm glad it worked.

I wasn't entirely sure, at least we all know now :)

---

