---
title: "Installing from a USB stick, no CDROM or Bootable USB"
date: 2009-02-02
forum: General Help
---

### Post by MikeSz on 2009-02-02
Ok, Heres a question I am 99.9% sure I already know the answer to though I thought I would throw it out there to see if anyone had any inspiring ideas.

I have acquired a Clevo 2200T laptop, which would be perfectly usable though unfortunately it has a problem with its CD-ROM drive.  I want to install Ubuntu on it, as at the moment it has only version of XP which doesnt let you run programs (as you can only log in as a guest, therefore no admin privileges - its been on a work network)

I've put 8.10 on a USB stick, and I want to try and install it on the laptop (in a nutshell).  I've tried flashing the BIOS so that it boots from USB - not easy to find a flash for this laptop and I cant think of anyway of getting into XP that lets you run programs.  I have got several boot disks on Floppy though not sure how to run a linux setup from what is effectively a slim version of MS-DOS running from RAM-DRIVE.  

Whilst I have now pretty much concluded that I am stuffed and will just have to bin this thing, I nonetheless think this is a matter of pride now and dont want to give in - So, any brainwaves out there as to how this could be done?

---

### Post by caljohnsmith on 2009-02-02
If you can boot a floppy, I would suggest installing the [PLoP boot manager]("http://www.plop.at/en/bootmanager.html#runflp") to the floppy, because there is a good chance PLoP can boot your Ubuntu USB drive. PLoP is unlike other boot managers in that it has its own built-in USB drivers, so PLoP can often boot USB drives even when the BIOS does not support booting USB devices. How about giving that a shot and let me know how it goes.

---

### Post by ieee488 on 2009-02-02
Do you know what are the specs on the laptop?

If is a P2, Puppy Linux may be more appropriate.

Anyhow, [http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html) may be of use.

---

### Post by MikeSz on 2009-02-02
Thanks for those.  I will give Plop a go then try Puppy.  I am having to use my iMac and a USB pendrive so will have to do some swapping about but Il post what happens if anything. 

The specs, from what I can gather, is that its a P2 1.2Ghz & 256Mb Ram.  It has a 60Gb hard disk and this infernal version of XP installed.  

Anyway....back to work!

---

