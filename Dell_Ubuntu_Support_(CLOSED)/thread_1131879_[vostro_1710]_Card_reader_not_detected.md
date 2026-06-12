---
title: "[vostro 1710] Card reader not detected"
date: 2009-04-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by durand on 2009-04-21
Hi,
I decided to try out the card reader at the front of my laptop and it doesn't seem to do anything. lspci doesn't show anything related and it doesn't seem to work in Vista either. I'm not actually sure if I even ordered a card reader as it doesn't even show up on my order receipt so I'm a bit confused about what to do.

Are the card readers optional on vostros? I've checked the dell website and it does show up on the flash presentation here: [http://www1.euro.dell.com/content/products/featuresdetails.aspx/vostronb_1710?c=uk&l=en&s=bsd&cs=ukbsdt1&~lt=popup](http://www1.euro.dell.com/content/products/featuresdetails.aspx/vostronb_1710?c=uk&l=en&s=bsd&cs=ukbsdt1&~lt=popup) so is there anything else that I can do? Should I complain to dell yet?

---

### Post by durand on 2009-04-21
Just after posting that, I realised that I might have to change some bios setting. And I was right. The slots now get detected by lspci however dmesg throws some errors. The card can be seen in Computer but it fails to mount.

dmesg:

> [  313.663524] mmc0: unrecognised SCR structure version 15
[  313.663545] mmc0: error -22 whilst initialising SD card
[  499.380536] mmc0: new high speed SD card at address b368
[  499.381294] mmcblk0: mmc0:b368 SD    952 MiB 
[  499.381393]  mmcblk0: p1


I have no idea what they mean though..

---

### Post by cubicdau on 2009-05-15
hy durand,

as i finally got some spare time to think about fixing the remaining aspects of my on year old vostro 1510, is stumbled across your post.

Up until now, i never managed to see the card inserted at all. So main point for me was to enable it in bios ...

having done this i got a mmc0: error -110 whilst initializing. So, i took out the card and reapplied it. This time i got the error for mmcblkd0.

I had a look via ls - la /dev/mm* and what happened was:
```

brw-rw---- 1 root plugdev 179, 0 2009-05-15 13:28 /dev/mmcblk0
brw-rw---- 1 root plugdev 179, 0 2009-05-15 13:28 /dev/mmcblk0p1

```

so, a simple
```

mount /dev/mmcblk0p1 /any/where

```

got me access to the data stored on the card.

All this was performed on 8.10, kernel 2.6.27-14

---

### Post by durand on 2009-05-15
Cool, I managed to get it to work as well. Sorry, I completely forgot about this thread! This worked perfectly: [http://www.arsgeek.com/2007/04/30/get-your-ricoh-sd-card-reader-working-in-ubuntu/](http://www.arsgeek.com/2007/04/30/get-your-ricoh-sd-card-reader-working-in-ubuntu/)

And you don't even need to mount it manually.

---

### Post by pararoly on 2010-01-16
Hello!

I found this thread very useful.  It helped me make some progress in getting my own card reader working. However, I am now stuck.

This is what I did...

Followed [these]("http://www.arsgeek.com/2007/04/30/get-your-ricoh-sd-card-reader-working-in-ubuntu/") instructions as posted by durand. After which, the card reader was listed by lspci ...

```
06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
06:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
06:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
```dmesg listed the following errors...

```
[   13.330827] mmc0: error -84 whilst initialising SD card
[   95.593345] mmc0: error -84 whilst initialising SD card
[  252.041013] mmc0: error -84 whilst initialising SD card
```Any bright ideas? 
Many thanks
Roland

---

### Post by durand on 2010-01-16
Here you go: [http://filthypants.blogspot.com/2009/03/ubuntu-904-jaunty-jackalope-on-acer.html](http://filthypants.blogspot.com/2009/03/ubuntu-904-jaunty-jackalope-on-acer.html)
That fix apparently works on dells as well as it says here: [http://www.mydellmini.com/forum/dell-mini-9-hardware-issues-problems/6365-sdhc-card-problem-after-upgrading-jaunty-9-04-a.html](http://www.mydellmini.com/forum/dell-mini-9-hardware-issues-problems/6365-sdhc-card-problem-after-upgrading-jaunty-9-04-a.html)

---

### Post by gabo.cr on 2010-01-16
I had the same problem in another Thread with no luck.
Thank you guys, I will try this also.

---

### Post by pararoly on 2010-01-17
Thank you for your reply Durand - I will give that a go a little later today.
Best wishes :D
Roland

---

