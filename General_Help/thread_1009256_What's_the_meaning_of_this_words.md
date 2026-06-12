---
title: "What's the meaning of this words ?"
date: 2008-12-12
forum: General Help
---

### Post by rams123 on 2008-12-12
Please explain me what's the meaning of this words -

**Debian** - I know ubuntu is debian based, but what is debian  and what is the use of this ?

**i386** - When I download some thing like kubuntu there will be i386, I can understand this may be signal of 32 bit , is it correct ? Whats the meaning of this ?

**gnu/linux** - When I visit some linux related blogs there will gnu/linux in the tag line , what's gnu here ?

And finally I often see this type of words - [B]/dev/sda, /dev/sdb
,sdv[/B]. Please explain me about this.

---

### Post by theolster on 2008-12-12
**Debian** is another Linux distribution, like Red Hat's Fedora, or Novell's SUSE.  Debian is the bas of what Ubuntu is based upon, and there is much in common between the two.  Basing one distro on another saves having to write a whole new OS from scratch.

**i386** is the hardware archictecture.  For example if you were using an old Apple Mac you might use the PowerPC version.

**gnu/linux** This will take more than a sentance to explain. visit [wikipedia for GNU]("http://en.wikipedia.org/wiki/GNU")

**/dev/sda** This is a hardware device, probably an internal hard disk. Your second hard disk might be /dev/sdb.

I hope this helps.

---

### Post by lykwydchykyn on 2008-12-12
> **rams123 said:**
> Please explain me what's the meaning of this words -

**Debian** - I know ubuntu is debian based, but what is debian  and what is the use of this ?

Debian is one of the oldest and possibly the largest community Linux distros.  See [www.debian.org](www.debian.org).  Ubuntu packages mostly originate from Debian's repositories, though they are recompiled for Ubuntu.
> 
**i386** - When I download some thing like kubuntu there will be i386, I can understand this may be signal of 32 bit , is it correct ? Whats the meaning of this ?

i386 is short for Intel 386, the minimum processor you'd need to run code compiled for "i386".  If you see i586 that means you need a pentium I or newer, i686 means pentium II.  

> 
**gnu/linux** - When I visit some linux related blogs there will gnu/linux in the tag line , what's gnu here ?

see [http://www.gnu.org/philosophy/linux-gnu-freedom.html](http://www.gnu.org/philosophy/linux-gnu-freedom.html)
EDIT: actually, see this, it's more to the point: [http://en.wikipedia.org/wiki/GNU/Linux_naming_controversy](http://en.wikipedia.org/wiki/GNU/Linux_naming_controversy)
> 
And finally I often see this type of words - [B]/dev/sda, /dev/sdb
,sdv[/B]. Please explain me about this.

Those are names of hard drives or other storage devices on your system.  In unix/linux, devices are given filenames in the filesystem to identify them.  The /dev directory holds all these.

See this: [http://tldp.org/HOWTO/Partition/devices.html](http://tldp.org/HOWTO/Partition/devices.html)

---

### Post by rams123 on 2008-12-13
Thanks theolster and lykwydchykyn.

Some more doubts - 

What's difference bet /dev/hda and /dev/sda.
How to recognize ext harddrive or pendrive ? I mean any word or symbol for that ?

---

### Post by lykwydchykyn on 2008-12-13
Once upon a time there were two types of hard drives: IDE and SCSI.  Linux had two drivers, one each type of drive.  Drives loaded with the IDE driver got named "hd" and drives loaded with the SCSI driver got named "sd".

Then time went by and things like SATA and USB and Firewire came along.  For whatever reasons, support for these ended up in the SCSI driver, so they also got loaded as "sd".  

Meanwhile, the IDE driver was somewhat old, clunky, and poorly maintained.  So about a year ago, someone decided to just add IDE support to the SCSI driver and do away with the old IDE driver for good.

Hence, you'll see a lot of things in tutorials and so forth about "hda" or "hdb", but these are no longer in use (at least not in Ubuntu; a few distros still use the older kernels with the IDE driver, and some simulate the "hd" notation out of convention).  In Ubuntu, everything should be "sd" now - IDE drives, SCSI drives, SATA, USB drives, memory cards, etc.

---

