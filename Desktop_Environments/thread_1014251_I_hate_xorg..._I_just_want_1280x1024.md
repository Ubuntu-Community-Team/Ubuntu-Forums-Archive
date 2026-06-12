---
title: "I hate xorg... I just want 1280x1024"
date: 2008-12-17
forum: Desktop Environments
---

### Post by Underpants on 2008-12-17
I'd like to state that for years and years I've always hated xorg.

I've got 8.10 on an intel motherboard, it's an 845 chipset I think. I have a 1280x1024 that I need to configure.

I have run the command:
sudo dpkg-reconfigure -phigh xserver-xorg

Which yields the following xorg.conf file.



```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```


That's pathetic. What do I need to do to get the right driver and resolution in there?

---

### Post by cdtech on 2008-12-17
Let's start by finding out exactly which card you have. Could you post the output of:
```
lspci
```
See if we can get this thing worked out for ya......

---

### Post by Underpants on 2008-12-17
```

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 82)

```

---

### Post by cdtech on 2008-12-17
You'll need to manually edit your "xorg" file to include the below configuration. Be sure to correct to your flavor (hz sync, ect...). See if this gets you going.
```
Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset
Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        ModelName       "**Dell 1024x768 Laptop Display Panel**"
        HorizSync       **31.5 - 48.5**
        VertRefresh     **59.0 - 75.0**
        Option          "DPMS"
EndSection

Section "Device"
        Identifier      "Videocard0"
        Driver          "i810"
        VendorName      "Videocard vendor"
        BoardName       "Intel 845"
        VideoRam                        10000
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset
Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubsection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "**Synaptics Touchpad**"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

---

### Post by Underpants on 2008-12-17
That threw poopbuntu into low graphics mode.

---

### Post by cdtech on 2008-12-17
Let's see the output of your log file:
```
cat /var/log/Xorg.0.log > xlog.txt
```
Then just link the text file for viewing....

---

### Post by Underpants on 2008-12-17
I'm just going to throw an nvidia card in the box. I searched around and found other people with the same card, and 10 pages deep into the thread with no results...

:) 

thanks for your help!

---

