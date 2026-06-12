---
title: "Boot error:   (unetbootin)"
date: 2009-05-29
forum: General Help
---

### Post by tosunbd on 2009-05-29
lspci
```

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:02.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

```

After extracting ubuntu9.04.iso in a 2GB pendrive using unetbootin, it is not booting from pendrive.
"Boot error"
Someone please help.

---

### Post by shel-hall on 2009-05-29
I had a 4GB USB key decide to quit booting, even when it was properly formatted and the boot flag set. After much fooling around, I managed to restore it by using the key manufacturer's "Remove U3" repartitioning and reformatting tool. Unfortunately, it's a WinXP app. I got it from a link on the U3.com website ([http://www.u3.com/support/default.aspx#CQ3](http://www.u3.com/support/default.aspx#CQ3)), I think.

After running the U3 tool (which doesn't actually care if the U3 stuff is on the key), I used Ubuntu's "gparted" to create an ext2 partition on the key. After that, I was able to re-load 8.10 on the key, boot, run, etc.  I later re-formatted it (using the same tool) and put UNR 9.04 on the key, and, again, no problems.

-Shel

---

