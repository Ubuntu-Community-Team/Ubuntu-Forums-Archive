---
title: "Dell 530s won't boot into Ubuntu 8.04"
date: 2008-06-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by putertopia on 2008-06-06
Alright, I'm a complete Linux noob.  I consider myself an advanced Windows user, and I am an HP authorized service technician, but I cannot for the life of me figure out why I can't CD boot into Ubuntu.

Took a pic, comes to the Ubuntu 8.04 loading splash screen, then pops to this screen after a bit:

[IMG]http://i236.photobucket.com/albums/ff207/putertopia/random/104_1705.jpg[/IMG]

What's my next move?

---

### Post by forger on 2008-06-06
hm.. doesn't dell support ubuntu?

You're trying to boot from the live cd?
1) check the downloaded cd with the md5:
[http://releases.ubuntu.com/hardy/MD5SUMS](http://releases.ubuntu.com/hardy/MD5SUMS)
2) reburn a new cd at low speeds, i.e. 1x or 4x
3) unplug the hard drives, try run ubuntu live environment

or have you installed hardy already and doesn't boot from the hard drive?
1) specify if you did anything before getting problems

---

### Post by putertopia on 2008-06-06
Checked the hash last night, came out fine.  Tried burning a new disk again for the heck of it... does the same exact thing.  Ubuntu live environment is off the CD, correct?  I can try unplugging the hdd(s).  

I basically got this sytem dirt cheap (less than $100) and I now dub it my experimental machine lol.  I have a Toshiba notebook that I would like to run Ubuntu on, but when booting off the CD, the display artifacts a bit and I haven't gotten around to trying to make my Atheros wifi card work yet.  I'm trying to work around Vista, and I would like to do it legally... and this seems to be the best way to do it.

---

### Post by forger on 2008-06-06
Yeah, live environment = boot off from cd, try unplug the hard drives to see the outcome :)

are the drives ATA (PATA) or SATA?

---

### Post by forger on 2008-06-06
It could be due to this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153702](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153702)

also see
[http://ubuntuforums.org/showthread.php?t=765195&page=7](http://ubuntuforums.org/showthread.php?t=765195&page=7)
and this comment
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153702/comments/52](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153702/comments/52)

---

### Post by putertopia on 2008-06-06
Yep, I'm in Ubuntu.  It was the IDE>RAID thing.  I saw that in another post and played around with it in the BIOS just to see if I can get it booted.  Now I need to set it back to IDE more than likely for windows to boot properly.  I guess I'll have to figure out first off how to write that script and where, and then how to execute it.

I'm going to partition the drive and install Ubuntu on one of the drives - you can dual boot with Ubuntu and Windows Vista Home Premium, correct?

---

### Post by putertopia on 2008-06-06
Alright.  I added "all_generic_ide floppy=off irqpoll" to the F6 option thinger it worked great.  Now... all I need to know is if I can dual boot this thing?

---

### Post by forger on 2008-06-07
the installer and grub should detect the other operating system automatically upon installing the system

---

### Post by lunixgeek on 2008-09-21
These boot options were quite helpful and worked for me.
I got to see the livecd work for the first time on this Dell machine.

My question then is, if I go ahead and install Ubuntu will I need those
boot options after install on the first boot off the harddrive?

---

