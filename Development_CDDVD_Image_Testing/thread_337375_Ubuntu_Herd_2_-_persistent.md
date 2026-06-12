---
title: "Ubuntu Herd 2 - persistent"
date: 2007-01-12
forum: Development CD/DVD Image Testing
---

### Post by jerrylamos on 2007-01-12
image 20070111.1
md5sum checked O.K.

1.Why is USB listed as /dev/sdc1?  On dapper, I get /dev/sda1

2. Using existing USB drive with 3 partitions, fdisk had difficulties deleting and writing new partition.  I had to shutdown so the new partition would show properly.  I haven't had that trouble with dapper.

3. Shutdown has worked a couple of times.  It doesn't usually, just sits there after reloading CD and pushing enter.

4. Booting persistent, casper-rw icon shows on desktop.  On dapper it doesn't.  My experience, in persistent, best not mess with the casper-rw USB.  Why does casper-rw show on Feisty but not Dapper?  I like Dapper hiding persistent USB.

5. Feisty persistent worked for adding user, bookmarks, loading Adobe flashplayer 9 beta from Adobe site, loading Realplayer10GOLD from Realplayer site.  BBC news video used Realplayer O.K. checked after re-booting persistent.

6.  I don't care for the look and feel of the Feisty splash screen.  It just sits there with little action, except for some very tiny dark blue text on a black background I can hardly read.  Dapper is much much better, giving a few lines of what's being loaded, in a text large enough to read, and frequent enough to let me know it is still alive.

By the way, the Christmas Edition 2006 DVD is great for checking out what packages I want to install.

Thanks for the opportunity.  Jerry:-|

---

### Post by jerrylamos on 2007-01-18
](*,) Oops.  Feisty Herd 2 fdisk of /dev/sdc to create persistent USB wiped out /dev/hda partition table, trashing the dual boot ubuntu/windows.  I've been recovering ever since.  I had most but not all of home backed up.

-- I've no idea why Feisty Herd 2 calls the USB /dev/sdc while ubuntu Christmas 2006 (which I thought was a Feisty Herd 1), calls it /dev/sda.  6.06.1 also calls the USB /dev/sda.

Shades of Red Hat 7.2, 8, and 9 which would frequently trash the dual boot partition table when I thought I was just running.  I suspect either the boot process or fsck's periodic checks, so I abandoned linux for years.

Ubuntu has been fine from 5.10, 6.06.1, 6.10, ubuntu xubuntu kubuntu and christmas 2006 Feisty (herd 1?) CD Live, install, and persistent so I got lulled into a sense of confidence.  Wrong.

Cheers, Jerry Amos

---

### Post by pochu on 2007-01-19
> **jerrylamos said:**
> ](*,) Oops.  Feisty Herd 2 fdisk of /dev/sdc to create persistent USB wiped out /dev/hda partition table, trashing the dual boot ubuntu/windows.  I've been recovering ever since.  I had most but not all of home backed up.

-- I've no idea why Feisty Herd 2 calls the USB /dev/sdc while ubuntu Christmas 2006 (which I thought was a Feisty Herd 1), calls it /dev/sda.  6.06.1 also calls the USB /dev/sda.

Shades of Red Hat 7.2, 8, and 9 which would frequently trash the dual boot partition table when I thought I was just running.  I suspect either the boot process or fsck's periodic checks, so I abandoned linux for years.

Ubuntu has been fine from 5.10, 6.06.1, 6.10, ubuntu xubuntu kubuntu and christmas 2006 Feisty (herd 1?) CD Live, install, and persistent so I got lulled into a sense of confidence.  Wrong.

Cheers, Jerry Amos
Hi.

Who has tell you that Ubuntu Christmas Edition was Feisty? That's totally wrong. [The Ubuntu Christmas Edition is based on Edgy.]("http://ubuntusoftware.info/faq.html#release")

And if you have problems with Feisty... that's absolutely normal. Feisty is currently in development, so it will probably break your system. So don't expect a stable system.

If you want/need an stable system, install 6.06 or 6.10, because, as you've said, they won't give you any problem.

But, if you are going to test Feisty, you should know that until its final release on April 2007, it may, and, believe me, it will have bugs, some of them critical, that won't let you work.

We are testers. We test the development version of Ubuntu (and of any program) to find bugs, and inform the developers about them, in order to have a good new version, without bugs. If we hadn't done this, Breezy (5.10), Dapper (6.06), Edgy (6.10), and all the software you use, would have given you a lot of problems.

So if you want to be a tester, I say to you welcome! But if you don't want, take a stable version of the distro and don't come here saying Feisty isn't a good version.

That's all.

Regards
Pochu

---

### Post by jerrylamos on 2007-01-22
Well, I'd expect Feisty to be up to full quality when it is released.  Right now, there may be some rough corners which is why I'm running it.

Wicki says do an fdisk before formatting the usbdisk,

"Ubuntu Hacks" just says do a mkfs.ext3 omitting the fdisk.

I did just the mkfs, persistent ran fine, On a 2GHZ IBM NetVista with XP, installed flash player 9 beta and Real Player 10GOLD onto casper-rw.

YouTube came up O.K.  With RealPlayer reception of the Hillary Clinton town meeting varied, sometimes O.K. sometimes a bit shaky.  I think the internet was pretty loaded down at 7pm.

With 1GB memory and doing internet, Feisty persistence was pretty much transparent so I forget I'm not running off the hard disk.

I prefer erasing "quiet" on booting from CD so I can at least see something is happening. Message traffic is O.K. but font is tiny, dark blue on black.  I'll have to look into that.

Cheers, Jerry Amos.

---

