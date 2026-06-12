---
title: "Non-System disk or disk error -- is there any way to recover ?"
date: 2012-02-24
forum: Desktop Environments
---

### Post by jeff7201 on 2012-02-24
I have a relatively old HP laptop, Centrino 1.5Ghz that came with Win XP.  I installed Ubuntu 10 and happily used it.  Upgraded to 11.10 and happily used it.

I had the bright idea to uninstall Ubuntu and re-install XP.  I followed some directions I found online, not well enough it seems.

I remember booting from my Ubuntu CD, using the file system tool to try to reformat the HD.  It returned error messages.
I was able to set the main partition on my disk (+/-58Gb) from ext4 to NTFS using a drop down box and then I shut down.  There were a couple Gb of ext partition left which I thought were temp space that the Ubuntu CD had borrowed.  

I THOUGHT I was going to then boot from my XP install CD and install.  But I immediately got "Non-System disk or disk error replace and strike any key when ready"

I get the same message whether I use my Ubuntu install CD, or my Windows CD.

I am guessing that rather than reformatting my drive as NTFS, I have told an ext4 drive that it is NTFS and scrambled its brain so it will not work.

Anyone have any ideas on how to undo the havoc I have wrought ?

---

### Post by gldearman on 2012-02-25
If you put in the Ubuntu install CD, and try to boot, and you get a non-system disk error, then that means your computer either isn't recognizing the CD as bootable, or isn't checking for a bootable CD before booting from the hard drive.

If your XP install CD is also not bootable, then likely it is the latter.

Can you get into your BIOS setup and make sure that the computer is set to boot from the CD drive before checking for a bootable hard disk?

---

### Post by jeff7201 on 2012-02-26
WAAAAAHHHHHHHOOOOOOOOOO!

I went into the BIOS and looked and it appeared to be checking for Optical Drive First, then Hard Drive.  But, just to be safe, I turned off quickboot and explicitly asked it to look to the optical drive first.

My old Ubuntu 10 installer works, but both my Win XP and Ubuntu 11.10 installer disks get the same disk error.

I am beginning to think that when I made the XP and Ubuntu 11.10 install disks on my Dell Studio / Win 7 laptop with Roxio software, I may have downloaded the .iso files, but not finalized the disks as bootable!

In any case, THANK YOU THANK YOU THANK YOU for taking the time to offer comments and make me think and look again.

I am reinstalling Ubuntu now off my v10 install CD and all appears to be proceeding normally.

):P

---

