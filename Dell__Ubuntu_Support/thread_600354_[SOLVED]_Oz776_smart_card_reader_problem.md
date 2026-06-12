---
title: "[SOLVED] Oz776 smart card reader problem"
date: 2007-11-02
forum: Dell  Ubuntu Support
---

### Post by Zeratul7 on 2007-11-02
I am having problems using integrated oz776 smart card reader after clean-installing gutsy (worked perfectly in feisty) on my Latitude D620.

After installing opensc and pcscd I got as far this:

opensc-tool --list-reader gives me this:
```
0      pcsc       O2 Micro Oz776 00 00
```
Looks to me that everything is ok.

But when I insert my card...
pkcs15-tool --list-certificates - result is like that:
```

reader-pcsc.c:533:pcsc_connect: SCardConnect failed: Card is unresponsive.
card.c:228:sc_connect_card: returning with: Unresponsive card (correctly inserted?)
Failed to connect to card: Unresponsive card (correctly inserted?)

```

...but  pcsc_scan tells me that card is recognized:

```

PC/SC device scanner
V 1.4.9 (c) 2001-2006, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.2
Scanning present readers
0: O2 Micro Oz776 00 00

Mon Oct 29 14:11:29 2007
 Reader 0: O2 Micro Oz776 00 00
  Card state: Card inserted, 
  ATR: 3B FE 94 00 FF 80 B1 FA 45 1F 03 45 73 74 45 49 44 20 76 65 72 20 31 2E 30 43

ATR: 3B FE 94 00 FF 80 B1 FA 45 1F 03 45 73 74 45 49 44 20 76 65 72 20 31 2E 30 43
+ TS = 3B --> Direct Convention
+ T0 = FE, Y(1): 1111, K: 14 (historical bytes)
  TA(1) = 94 --> Fi=512, Di=8, 64 cycles/ETU (55800 bits/s at 3.57 MHz)
  TB(1) = 00 --> VPP is not electrically connected
  TC(1) = FF --> Extra guard time: 255 (special value)
  TD(1) = 80 --> Y(i+1) = 1000, Protocol T = 0 
-----
  TD(2) = B1 --> Y(i+1) = 1011, Protocol T = 1 
-----
  TA(3) = FA --> IFSC: 250
  TB(3) = 45 --> Block Waiting Integer: 4 - Character Waiting Integer: 5
  TD(3) = 1F --> Y(i+1) = 0001, Protocol T = 15 - Global interface bytes following 
-----
  TA(4) = 03 --> Clock stop: not supported - Class accepted by the card: (3G) A 5V B 3V 
+ Historical bytes: 45 73 74 45 49 44 20 76 65 72 20 31 2E 30
  Category indicator byte: 45 (proprietary format)
+ TCK = 43 (correct checksum)

Possibly identified card (using /usr/share/pcsc/smartcard_list.txt):
3B FE 94 00 FF 80 B1 FA 45 1F 03 45 73 74 45 49 44 20 76 65 72 20 31 2E 30 43
        Estonian Identity Card (EstEID v1.0 cold)

```

The same card and the same reader worked in a couple of hours before in feisty. And the same card also works in the same laptop wiht gutsy but with a different USB smart card reader.

What should I do next to find the problem?

Regards,
Zeratul

---

### Post by bluedragon436 on 2007-11-02
As a weird bit of info...my smart card reader worked fine with Feisty but once installing Gutssy it quit working....but after letting it do all of its updates and stuff it now seems to work just fine....well when it wants to anyways.  Then again I have an internal card reader installed in my D610....

---

### Post by bluedragon436 on 2007-11-02
I will give an external USB a try tonight when I get home and let u know what I can figure out or if it works on its own one way or another...

---

### Post by Zeratul7 on 2007-11-04
Anyone got ideas where to look next?

---

### Post by Zeratul7 on 2007-11-08
There can't be physical problems with card or reader because they both work in Windows XP.

---

### Post by Zeratul7 on 2007-11-16
Here is an attachment example that in Feisty virtual machine this reader and card works perfectly (take a look at the result of "pkcs15-tool --list-certificates").

---

### Post by inaneframe on 2007-11-16
Make a file called "disk-restart.sh" put this into it:

```
echo 1024 > /sys/block/sdb/device/max_sectors
echo 1 > /sys/class/scsi_disk/0:0:0:0/allow_restart
echo 1 > /sys/class/scsi_disk/2:0:0:0/allow_restart
```

```
sudo mv disk-restart.sh /etc/init.d/

sudo chmod u+x /etc/init.d/disk-restart.sh

sudo nano /etc/rc.local
```

insert this into rc.local:

```
/etc/init.d/disk-restart.sh
```

Restart.

Big props to mesae for this info at [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/61235](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/61235)

I hope that it works for you.

---

### Post by Zeratul7 on 2007-12-19
Well i finally find the problem. Since Gutsy uses opensc and libopensc2 versions 0.11.1 and Gutsy 0.11.3 so I downgraded both packages to 0.11.1 on my Gutsy and now it works! I also reported the bug to opensc-project bug tracker.

---

### Post by Zeratul7 on 2008-03-17
Finally solved. I hope this fix makes it into Hardy.

Meanwhile, here is the newest libccid package with the fix: [http://launchpadlibrarian.net/12705573/libccid_1.3.5-1_i386.deb](http://launchpadlibrarian.net/12705573/libccid_1.3.5-1_i386.deb)

---

