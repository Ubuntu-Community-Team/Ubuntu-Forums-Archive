---
title: "Upgrade to 8.10 broke dual monitor setup"
date: 2008-11-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kgish on 2008-11-17
I have a Dell Latitude D620 which worked just fine with an external monitor attached via a docking station.

Unfortunately, once I upgraded from 8.04 to 8.10 my xorg.conf chokes the system and causes everything to hang on boot up.

The only solution was to remove the xorg.conf, and the attached external monitor is now simply a low resolution mirror of the laptop screen.

Stand-alone laptop works just fine.

Can anyone help me?

$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

---

### Post by tolmeda on 2008-11-19
I've got the same problem with my HP laptop running the Intel 945GM graphics card. I've read that it's a problem with the new intel driver which has replaced the i810 driver in Intrepid.

I haven't been able to get even a very trimmed down version of my dual screen xorg.conf working.

Next step is to play around with the xrandr tool referenced [here]("http://snippets.dzone.com/posts/show/6386").

---

### Post by tolmeda on 2008-11-19
Here is [the answer]("http://navetz.com/v/132/Simple-dual-monitor-setup-with-XrandR-in-Ubuntu-Linux") [navetz.com].

My laptop has a resolution of 1280x800 while my external LCD is 1280x1024. The intel driver can only handle a total width (or height) less than 2048 so I had to stack them, LCD on top of laptop.

In xorg.conf, I modified the Screen section to look like this:
```

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
                 Modes        "1280x1824" "1280x800"
                 Virtual      1280 1824
        EndSubSection
EndSection

```

Restarted X, then ran the following:
```
xrandr --output LVDS --mode 1280x800 --output VGA --mode 1280x1024 --above LVDS
```

Worked beautifully!

Now, if I could only find a 1280x1824 desktop image...

---

### Post by Chen Jun on 2008-12-04
I have same issue, it seems 8.10 did not support "Virtual 2560 1024" in xorg.conf. I have decided not to upgrade to 8.10.

---

