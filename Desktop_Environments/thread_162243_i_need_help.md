---
title: "i need help"
date: 2006-04-18
forum: Desktop Environments
---

### Post by runefreak on 2006-04-18
i have a compaq presario 5020 400mhz processor and 195 mb of ram with an intagrated ad1881 soundmax chip i cant find a driver for linux only windows 98 
i can`t figure out alsa any ideas?

---

### Post by taurus on 2006-04-18
Have you tried out the LiveCD version to see if it can find your soundcard?  Chances are Ubuntu will find everything on your system so you can always test it out first with the LiveCD or go for the install right away if you want...

---

### Post by runefreak on 2006-04-18
no good i did the live cd thing and reinstalled ubuntu twice and even redownloaded it 
and burned it to cd again it wont find my soundcard
](*,)

---

### Post by runefreak on 2006-04-18
this is rediculous that i can`t seem to get any help with this problem
this os is a joke i was better off with me

---

### Post by towsonu2003 on 2006-04-19
try ```

lspci -v
``` and identify your sound card to try to find a driver for it. paste output here if in doubt. 

also see this: [http://kmuto.jp/debian/hcl/index.cgi](http://kmuto.jp/debian/hcl/index.cgi)

> this os is a jokethis will significantly decrease others' willingness to help you...

---

### Post by runefreak on 2006-04-19
sorry just very irritated i have messed with this thing day and night for two days 
with no success and very little help even though i have all but begged for it
i am a complete noob and people keep rattleing off things to me that either have nothing to do with what i am trying to do or are completely over my head and refuse to explain them simply to me .oh here is what i found  ](*,)        0000:00:00.0 Host bridge: Intel Corp. 440LX/EX - 82443LX/EX Host bridge (rev 03)        Flags: bus master, medium devsel, latency 64
        Memory at 50000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corp. 440LX/EX - 82443LX/EX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: 40000000-410fffff

0000:00:03.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
        Subsystem: Linksys: Unknown device 0574
        Flags: bus master, medium devsel, latency 66, IRQ 11
        I/O ports at 2400 [size=256]
        Memory at 41100000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:14.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:14.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        I/O ports at 2020 [size=16]

0000:00:14.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 2000 [size=32]

0000:00:14.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9

0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc) (prog-if 00 [VGA])
        Subsystem: Compaq Computer Corporation Rage LT Pro (Compaq Presario 5240)
        Flags: bus master, VGA palette snoop, stepping, medium devsel, latency 66, IRQ 11
        Memory at 40000000 (32-bit, non-prefetchable) [size=16M]
        I/O ports at 1000 [size=256]
        Memory at 41000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

---

### Post by towsonu2003 on 2006-04-19
I don't see an audio card in that output :confused: does anyone reading this thread sees it??? As far as I know, it was supposed to say something like "audio controller" ](*,) checked google.com/linux and it seems lspci should have reported it... 

try "scanpci" instead of "lspci", as I found the following:
> 
It's easy to find out what bus-resources have been assigned to devices on the PCI bus with the "lspci" and/or "scanpci" commands The options -v or -vv will show more detail. In some cases, "scanpci" will find a device that "lspci" can't find. That's because "scanpci" directly searches for devices on the pci bus (via the configuration space) and doesn't use data obtained by the kernel (where it could be wrong due to a kernel bug --I've just found such a case).at [http://tldp.org/HOWTO/Plug-and-Play-HOWTO-6.html](http://tldp.org/HOWTO/Plug-and-Play-HOWTO-6.html)

see man page of scanpci (type command: man scanpci) to learn how to use it, as I don't have my ubuntu here to check it out :)

Here is a dreaded question for you: does it work in Windows (if dual booting, boot to windows and play a song)

---

### Post by runefreak on 2006-04-19
yes it worked perfectly with windows and no i am not dual booting that is what
is so frustrating it worked fine with windows and now it doesnt

---

### Post by towsonu2003 on 2006-04-19
try scanpci (see my last post), hopefully it's gonna give some useful output...

---

### Post by runefreak on 2006-04-19
mark@ubuntu:~$ scanpci
bash: scanpci: command not found

see why i am getting irritated?lol

---

### Post by towsonu2003 on 2006-04-19
what does these two output?
```

lspci -vv -M
lspci -vv -M -H1

```
I don't know what they do, I found them here: [http://www.ussg.iu.edu/hypermail/linux/kernel/0501.1/2564.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0501.1/2564.html)

[quote]mark@ubuntu:~$ scanpci
bash: scanpci: command not found[/quote
so we don't have scanpci? interesting.

---

### Post by runefreak on 2006-04-19
this is what came up.here is the first one...pcilib: Cannot open /sys/bus/pci/devices/0000:f1:0d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f1:0e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f1:0f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f1:10.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f1:11.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f1:12.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f1:13.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f1:14.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f1:15.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f1:16.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f1:17.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f1:18.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f1:19.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f1:1a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f1:1b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f1:1c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f1:1d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f1:1e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f1:1f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:00.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:01.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:02.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:03.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:04.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:05.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:06.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:07.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:08.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:09.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:0a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:0b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:0c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:0d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:0e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:0f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:10.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:11.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:12.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:13.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:14.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:15.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:16.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:17.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:18.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:19.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:1a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:1b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:1c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:1d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:1e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f2:1f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:00.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:01.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:02.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:03.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:04.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:05.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:06.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:07.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:08.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:09.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:0a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:0b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:0c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:0d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:0e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:0f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:10.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:11.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:12.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:13.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:14.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:15.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:16.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:17.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:18.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:19.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:1a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:1b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:1c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:1d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:1e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f3:1f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:00.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:01.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:02.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:03.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:04.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:05.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:06.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:07.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:08.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:09.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:0a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:0b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:0c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:0d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:0e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:0f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:10.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:11.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:12.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:13.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:14.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:15.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:16.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:17.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:18.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:19.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:1a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:1b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:1c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:1d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:1e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f4:1f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:00.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:01.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:02.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:03.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:04.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:05.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:06.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:07.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:08.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:09.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:0a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:0b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:0c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:0d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:0e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:0f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:10.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:11.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:12.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:13.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:14.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:15.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:16.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:17.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:18.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:19.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:1a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:1b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:1c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:1d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:1e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f5:1f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:00.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:01.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:02.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:03.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:04.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:05.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:06.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:07.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:08.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:09.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:0a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:0b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:0c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:0d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:0e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:0f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:10.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:11.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:12.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:13.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:14.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:15.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:16.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:17.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:18.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:19.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:1a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:1b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:1c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:1d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:1e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f6:1f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:00.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:01.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:02.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:03.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:04.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:05.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:06.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:07.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:08.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:09.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:0a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:0b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:0c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:0d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:0e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:0f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:10.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:11.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:12.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:13.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:14.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:15.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:16.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:17.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:18.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:19.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:1a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:1b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:1c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:1d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:1e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f7:1f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:00.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:01.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:02.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:03.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:04.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:05.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:06.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:07.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:08.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:09.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:0a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:0b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:0c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:0d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:0e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:0f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:10.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:11.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:12.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:13.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:14.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:15.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:16.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:17.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:18.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:19.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:1a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:1b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:1c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:1d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:1e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f8:1f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:00.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:01.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:02.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:03.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:04.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:05.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:06.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:07.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:08.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:09.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:0a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:0b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:0c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:0d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:0e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:0f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:10.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:11.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:12.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:13.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:14.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:15.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:16.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:17.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:18.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:19.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:1a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:1b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:1c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:1d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:1e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:f9:1f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:00.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:01.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:02.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:03.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:04.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:05.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:06.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:07.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:08.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:09.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:0a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:0b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:0c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:0d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:0e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:0f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:10.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:11.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:12.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:13.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:14.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:15.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:16.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:17.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:18.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:19.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:1a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:1b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:1c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:1d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:1e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fa:1f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:00.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:01.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:02.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:03.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:04.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:05.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:06.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:07.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:08.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:09.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:0a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:0b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:0c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:0d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:0e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:0f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:10.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:11.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:12.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:13.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:14.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:15.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:16.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:17.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:18.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:19.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:1a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:1b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:1c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:1d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:1e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fb:1f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:00.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:01.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:02.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:03.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:04.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:05.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:06.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:07.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:08.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:09.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:0a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:0b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:0c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:0d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:0e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:0f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:10.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:11.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:12.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:13.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:14.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:15.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:16.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:17.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:18.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:19.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:1a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:1b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:1c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:1d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:1e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fc:1f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:00.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:01.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:02.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:03.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:04.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:05.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:06.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:07.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:08.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:09.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:0a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:0b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:0c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:0d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:0e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:0f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:10.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:11.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:12.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:13.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:14.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:15.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:16.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:17.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:18.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:19.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:1a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:1b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:1c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:1d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:1e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fd:1f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:00.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:01.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:02.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:03.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:04.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:05.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:06.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:07.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:08.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:09.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:0a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:0b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:0c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:0d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:0e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:0f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:10.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:11.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:12.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:13.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:14.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:15.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:16.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:17.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:18.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:19.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:1a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:1b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:1c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:1d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:1e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:fe:1f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:00.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:01.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:02.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:03.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:04.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:05.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:06.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:07.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:08.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:09.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:0a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:0b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:0c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:0d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:0e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:0f.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:10.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:11.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:12.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:13.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:14.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:15.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:16.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:17.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:18.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:19.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:1a.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:1b.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:1c.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:1d.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:1e.0/config
pcilib: Cannot open /sys/bus/pci/devices/0000:ff:1f.0/config

Summary of buses:

00: Primary host bus
        01.0 Bridge to 01-01
01: Entered via 00:01.0
mark@ubuntu:~$
Display all 2116 possibilities? (y or n)
:
!
./
[
[[
]]
{
}
411toppm
822-date
a2p
accept
accessdb
aconnect
acpi
acpi_available
acpid
acpi_fakekey
acpi_listen
acroread
activation-client
addgroup
addr2line
add-shell
--More--

---

### Post by runefreak on 2006-04-19
here is the second...mark@ubuntu:~$ sudo lspci -vv -M -H1
0000:00:00.0 Host bridge: Intel Corp. 440LX/EX - 82443LX/EX Host bridge (rev 03)        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 64
        Region 0: Memory at 50000000 (32-bit, prefetchable)
        Capabilities: [a0] AGP version 1.0
                Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3- Rate=x1,x2
                Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>

0000:00:01.0 PCI bridge: Intel Corp. 440LX/EX - 82443LX/EX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: 40000000-410fffff
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-

## 00.01:0 is a bridge from 00 to 01-01
0000:00:03.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
        Subsystem: Linksys: Unknown device 0574
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 66 (63750ns min, 63750ns max), Cache Line Size: 0x08 (32 bytes)        Interrupt: pin A routed to IRQ 11
        Region 0: I/O ports at 2400
        Region 1: Memory at 41100000 (32-bit, non-prefetchable)
        Capabilities: [c0] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:00:14.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

0000:00:14.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Region 4: I/O ports at 2020

0000:00:14.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin D routed to IRQ 11
        Region 4: I/O ports at 2000

0000:00:14.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-

0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc) (prog-if 00 [VGA])
        Subsystem: Compaq Computer Corporation Rage LT Pro (Compaq Presario 5240)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 66 (2000ns min), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at 40000000 (32-bit, non-prefetchable)
        Region 1: I/O ports at 1000
        Region 2: Memory at 41000000 (32-bit, non-prefetchable)
        Capabilities: [50] AGP version 1.0
                Status: RQ=256 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3- Rate=x1,x2
                Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>
        Capabilities: [5c] Power Management version 1
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-


Summary of buses:

00: Primary host bus
        01.0 Bridge to 01-01
01: Entered via 00:01.0

---

### Post by towsonu2003 on 2006-04-19
nope, still not seeing an audio card in there. Sorry can't help with this. Try googling for your card until someone with more experience comes along and checks this out. 

if no replies in a week, post again (new thread) while including card in title...

sorry...

For info, here's **my** audio card in lspci -v: 

```

0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
        Subsystem: Hewlett-Packard Company: Unknown device 006b
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 5
        Memory at d0003000 (32-bit, non-prefetchable) [size=256]

```this is what the output should have looked like, as far as I know...

---

### Post by runefreak on 2006-04-20
is there no one who knows how to redetect a soundcard?

---

### Post by towsonu2003 on 2006-04-20
there are too many replies to this for others to check it out. open a new thread in a couple of days with title:
lspci can't detect ad1881 soundmax sound card (or similar)
and some descriptive info and what you tried so far in the text...

---

### Post by runefreak on 2006-04-20
thanks a lot for all your help anyway i really appreciate it i am seriously thinking about going back to windows i had way less problems

---

### Post by towsonu2003 on 2006-04-20
[QUOTE=runefreak]thanks a lot for all your help anyway i really appreciate it i am seriously thinking about going back to windows i had way less problems[/QUOTE]
well, linux is hard especially when it comes to this hardware issues. I would do a dual boot to allow some time both for the computer to resume its functionality and for you to find a way to fix this issue. 

I still think a new thread may get some assistance to you... just don't forget to note what you tried up until now... 

PS. Offtopic personal note: it took me three **months** (six-seven distros, decided to ditch linux twice) to understand and configure my stupid winmodem, so I understand the frustration perfectly well. 

Oh yes, distros... try other distros to see whether they can configure your souncard. if they can, you can find out how they do that and use it in an ubuntu installation (or stick with that distro). the ones I would recommend are suse, centos, knoppix (live cd but very famous for its hardware recognition), fedora, and maybe dyne:bolic or geexbox which specialize on audio, which should make them better at configuring sound -not sure-. 

**oh just remembered**try passing acpi=off and / or apm=off (combination, one, than the other, than both if all fails) on boot and reboot. To do this, backup than open your grub configuration file and add these arguments:
```

sudo cp /boot/grub/menu.list /boot/grub/menu.list.backup1
sudo gedit /boot/grub/menu.list
[code] and put those arguments at the end of your appropriate kernel line. Example: 
here is the kernel line I use:
[code]
title           Ubuntu, kernel 2.6.12-10-686
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-686
savedefault
boot

```
and here is the arguments would go:
```

title           Ubuntu, kernel 2.6.12-10-686
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash **acpi=off** **apm=off**
initrd          /boot/initrd.img-2.6.12-10-686
savedefault
boot

```
don't forget, you'll be trying them one by one first.

---

