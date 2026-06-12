---
title: "x64 LucidLynx: Kernel panic...and I don't know why"
date: 2010-09-07
forum: Desktop Environments
---

### Post by supaneko on 2010-09-07
I recently decided to spray paint my laptop (this is not what this is about though). I took it all apart, spray painted, and reassembled perfectly. Sadly, however, I am left with a kernel panic when I boot. I am unsure if the two are related but that is the only change I know of (however, I may have installed some updates but I honestly do not recall).

The kernel panic was assumed based on the flashing caps and scroll lock lights. Finally, I thought to remove the "quiet" and "nospalsh" options from grub and I was left with the screen shown in the picture. I can not boot any live CD (tried Knoppix but it fails), except for SLAX which works perfectly fine. When I tried booting Knoppix, it fails while loading UDEV. I could not find an option to disable udev at boot for LucidLynx.

I can not boot the live CD. The option to change the CD options doesn't even appear as I am left with a kernel panic here also.

Attached is the picture of the boot message. I would post the log but I do not know how to access it as the partitions are all EXT4 and SLAX is unable to read them. :(

I have tried booting an older kernel, same issue. Tried removing each piece of hardware, same issue. I have even tried switching the memory sticks and still the same trouble. Tried without the LCD screen attached and still the same issues. :(

Everything was working fine prior to the spray paint. I have checked all wires and connections and everything is fine (didn't paint over any connectors, my PC experience is quite advanced, though I am strictly a beginner-intermediate when it comes to the lovely Linux).

Any help or ideas would be appreciated. I have searched, searched, and searched some more for about a week now and have turned up NOTHING.

Dell Inspiron 1501 running 64-Bit Ubuntu LucidLynx (no other os)
AMD TMDTL56 1.8ghz. 64-bit Dual-Core CPU
2x 1GB, 533, 128X64, 8K, 200 RAM
120gb. Hard Drive
Broadcom DW1390 miniPCI Wireless-G Adapter
ATI IGP Xpress 1150 Graphics Card

Everyone else has always done an amazing job helping me out here. SOOO...I'm giving this a try again! It's been a few years without issues so hopefully everyone's just as nice as always. Hehe. :)

---

### Post by supaneko on 2010-09-07
One thing I should note, using the memtest86+ boot option, I tested the RAM and both sticks seemed to pass just fine.

My major confusion with this is that I can boot into SLAX just fine but it seems that any Linux OS that uses UDEV (assuming SLAX does not) gives me evil scroll & caps lock flashes while loading UDEV.

Knoppix does load just fine using the noudev boot option.

I have tried to seat, reseat, unseat, and reseat again all hardware but I am still running into troubles.

---

