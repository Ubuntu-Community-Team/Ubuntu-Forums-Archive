---
title: "error code 0142"
date: 2009-12-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bolex100 on 2009-12-04
This morning My machine fail to find a boot sequence.  It also had trouble backing up data when I ran from a disk.

I let the machine run a self test at boot. 
 
[I]Pre-boot system assesment build 4108
Rror code 0142
Msg: Error code 2000-0142
self test unsuccessful
status 78[/I]


Does this mean that my hard drive died (suddenly and without warning.)?

---

### Post by teward on 2009-12-04
Um... well if you can't access the data on the drive from a LiveCD/LiveUSB, then its an indicator the drive is bad.  Or some other thing on your computer died.

But I have questions:

(1) what's generating the error?  The Linux kernel, or is it the BIOS?

(2) what were you doing before you booted (as in before you last shut it down)?

---

### Post by bolex100 on 2009-12-04
Its the selftest in BIOS.  It was running normally at shutdown.  I was only running Firefox.
Ive never had a drive fail like this.

---

### Post by teward on 2009-12-04
How old is the computer/drive?

Since the issue was in the BIOS self-test, then I'm going to need the BIOS version number (I can get the BIOS manufacturer info from Google), then I'm going to look up the error code to see what it means.

I'm assuming this is your Inspiron listed in your signature?

If it is, then I've got something I need you to do:
[quote=Dell Support Forums]To confirm, F12 at powerup.  Boot to the Dell diagnostics and run the extended -- not just the quick - hard drive test.[/quote]

The bad thing is if the diagnostics don't exist, you're stuck.  But from what I can tell the error code 2000-0142 (full error code) on the Inspiron 1525 means your drive is dying or dead.  Still, run the above procedure and tell me what it does/says.

---

### Post by bolex100 on 2009-12-05
It was the compltete F12 diagnostics.  Now when I try it says that it has a log of failure on the drive and simply skips the test!  
I give up.  New thread time.

---

### Post by teward on 2009-12-05
The solution to this is to contact Dell and see if your system is under warranty.  If it is, they'll replace the drive.  If it isn't, you're stuck having to buy a new hard drive.  Not much else past this that I or the other Ubuntu forums people can do.

---

### Post by doleron on 2011-05-11
> **EvilPhoenix said:**
> The solution to this is to contact Dell and see if your system is under warranty.  If it is, they'll replace the drive.  If it isn't, you're stuck having to buy a new hard drive.  Not much else past this that I or the other Ubuntu forums people can do.

Sorry, you are wrong. There are too many things to do. For example, I sugest run Ubuntu Live CD, try mount the data partition and, at least, save some important data. Others commands, like fdisk, can be tryied. Order another HD only if all repair oportunities fail.

---

