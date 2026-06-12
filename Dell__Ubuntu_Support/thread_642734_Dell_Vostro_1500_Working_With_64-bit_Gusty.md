---
title: "Dell Vostro 1500 Working With 64-bit Gusty"
date: 2007-12-16
forum: Dell  Ubuntu Support
---

### Post by dyssident on 2007-12-16
Thanks to this forum, I knew before ordering my new Vostro 1500 that it was possible to get everything working on 32-bit Gusty. Being blessed with a free evening and the determination to take full advantage of my first 64-bit processor, I decided to try the 64-bit version of Gusty. Most things worked right out of the box but, as frequently reported, wifi and sound did not work. Vostro fans fear not, it only took me about 10 minutes to get my system working 100%.

All of this information is [crossposted from my blog]("http://mentalthinking.blogspot.com/2007/12/dell-vostro-1500-working-with-64-bit.html").

[SIZE="4"]Wifi[/SIZE]

Followed [ndiswrapper instructions available here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"). Connection speed is 54 Mb/s; range is excellent. Havent tested WEP yet. 

For the record, `lspci -v` shows:

```

0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
        Subsystem: Dell Unknown device 0007
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at fe8fc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

Drivers for the Vostro 1500's Broadcom 4311 card are distributed with Gusty and can easily be installed with the Restricted Drivers Manager. However, these native drivers have very poor range and only connect at a max of 24 Mb/s. bcm43xx drivers are deprecated at this point according to [this wiki page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy") and will be replaced in kernel 2.6.24 by [the b43 project]("http://linuxwireless.org/en/users/Drivers/b43"). If you're intent on going as open-source as possible, follow instructions [available here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy#head-c32709cb6de40e21b91790e33d349c111fcb83ec"). 

[SIZE="4"]Sound[/size]

I did [the fix described here]("http://ubuntuforums.org/showpost.php?p=3872487&postcount=3"). Works perfectly though others, including the guy that proposed the fix in the first place, have reported problems with the headphone jack working correctly.

[SIZE="4"]Power Management[/size]

The Vostro 1500 is affected by the now notorious [hard drive churn problem]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695"). This isnt really a bug, but rather the product of a series of unfortunate choices on the part of hardware manufacturers, integrators and distro developers.

Since I'm willing to trade shorter periods on battery power for longer hardware life, I changed the power saving settings following [instructions available here]("http://ubuntuforums.org/showpost.php?p=3675960&postcount=26"). I made one major change to avoid repeated spindown, so my 99-hdd-ugly-fix.sh looked like:

```

#!/bin/bash
if on_ac_power; then
  # on AC so don't do any head parking
  hdparm -B 254 -S 0 /dev/sda
else
  # either on battery or power status could not be determined
  # so quickly park the head to protect the disk
  hdparm -B 128 -S 60 /dev/sda
fi

```

Setting -B controls how quickly the heads will be parked. Parking the heads protects your drive from bumps. This setting effects how often Load_Cycle_Count in SMART gets incremented. A value of 254 basically stops auto-parking the heads.

Setting -S controls when the hd spins down. Drive spin-down is designed to save energy. This controls how often SMART's Start_Stop_Count gets incremented. A value of 60 causes it to spin down after 5 minutes. If you want another interval, multiply the desired number of minutes by 12.

If you'd like to see all the gritty details of your harddrives health that I'm refering to, you'll need a utility to access the SMART data. Just run:

```

sudo apt-get install smartmontools
sudo smartctl -a /dev/sda

```

[SIZE="4"]Media[/size]

To get all the good illegal stuff, enable all of the Ubuntu repositories in Synaptic and then run

```
sudo apt-get install ubuntu-restricted-extras libxine1-plugins
```

Well thats it for now. I'll be updating this post with anything else interesting I run into.

---

### Post by cherry316316 on 2008-04-07
have u tried 64bit hardy on dell vostro 1500 yet ?

any good news ?

---

