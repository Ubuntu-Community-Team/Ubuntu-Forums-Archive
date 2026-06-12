---
title: "please help me (noob)"
date: 2006-01-28
forum: Desktop Environments
---

### Post by crazyhippyguy on 2006-01-28
ok, so i was trying to dual boot XP and ubuntu on my computer, i have a 80GB hd with XP on it and i have an external 160GB hd that i tried to install ubuntu onto. well, ubuntu didnt install right and GRUB was put on with it. Now i cannot even boot up because it starts up saying "Grub loading..... Error 17". My computer didn't come with a XP disc, so i dont know how to get it to work. I tried to reinstall ubuntu, but my Cd drive wont read the disc. my computer is an XPS 400 with a 3.2Ghz pentium 4+HT.  is there a way i might be able to just get rid of GRUB so it will boot correctly?

---

### Post by bikeman on 2006-01-28
First, don't panic!  Is your computer set to boot off the CD first?  If not, then you will need to change the setting in the BIOS.  When the computer first starts, look for the message about what key to press to enter setup (usually delete, escape, or one of the F# keys).  Use that and look for the menu with the boot order, set the CD drive as first.  Also, while you are in the BIOS, make sure that your PC recognizes both drives!  Although a drive may be formatted and have data, if the BIOS does not recognize it, you cannot use it for an OS (I learned that the hard way, got a GRUB error, but do not remember which error number it was).

If you just want to get Windows to boot normally, you will need to borrow a Windows XP disk, boot from the CD, enter Repair mode, and use the command fixmbr.  After that, your computer will boot directly into Windows as if the Linux stuff did not exist.  

However, if you want to fix the Linux portion, you will have to reinstall Ubuntu (probably the easier option) or try to fix it using the repair option on the Ubuntu disk.  When you say that the PC cannot read the CD - was the CD used previously, or does your PC not even look at the CD and just tries to boot from the hard drive?  If it boots from the hard drive, change the boot order as above.  If it is just a CD problem, you may need to download and burn a new CD.  Good luck!

---

### Post by crazyhippyguy on 2006-01-28
it boots from CD before HD, and if i put the CD in, it will sit there for a bit then say "cannot boot from this device" or something like that then it says to press F1 to retry or F12 to go to setup. i think ill try to borrow a XP disc for it and do the fixmbr

---

### Post by stalefries on 2006-01-28
the cd is probably bad. You might want to burn a new disc, and see if that helps.

---

### Post by crazyhippyguy on 2006-01-28
ok, i tried the XP cd, and it seemed to work at first, but then when it said "starting up windows" at the bottom, it went to a blue screen and said at the bottom:

STOP: 0x0000007E (0xC0000005,0xF748EOBF,0xF78DA208,0xF78D9F08 )

pci.sys-address F748EOBF base at F7487000, datestamp 3b7d855c

so i restarted the comp, and it did the same thing.

on the third time, it wont read the XP cd either. It says the same thing. "Selected boot device not avalible. Strike F1 for retry or F2 for setup utility"

so i decided to take out the cd and try again. This time GRUB came up saying Error 21 instead of 17. ugh......

---

### Post by crazyhippyguy on 2006-01-28
the ubuntu CD i got was one of those that you can get for free online, so i didnt think it would be bad

---

### Post by slavik on 2006-01-28
[QUOTE=crazyhippyguy]the ubuntu CD i got was one of those that you can get for free online, so i didnt think it would be bad[/QUOTE]
umm, all ubuntu CDs are free if you download the cd image ...

---

### Post by crazyhippyguy on 2006-01-28
i ment, it was one of those where they will ship a cd to you for free.

---

### Post by superhew on 2006-01-28
funny thing is, a lot of those shipit cds *are* bad. out of a box of 50, i found 32 that matched the md5sum. so, your best bet is to download the iso off the site, check the md5sum, burn & verify, and install. its the only method that works 100% for me :)

---

### Post by crazyhippyguy on 2006-01-29
ok, so i got my computer to boot up, i just reinstalled ubuntu on it, so GRUB wouldnt go crazy anymore, but i still need to uninstall ubuntu, so i need to restore my MBR first. problem is, all the sites i go to need me to have a floppy disk drive. But my computer doesnt. Is there any way that i could restore my MBR without a floppy drive and without the XP Media Center CD?

---

