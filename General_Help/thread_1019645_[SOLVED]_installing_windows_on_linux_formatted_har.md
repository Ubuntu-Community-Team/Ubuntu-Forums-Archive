---
title: "[SOLVED] installing windows on linux formatted hard drive"
date: 2008-12-23
forum: General Help
---

### Post by lun on 2008-12-23
Installing windows on linux formatted hard drive.  I have read about this in multiple other posts and have followed their instructions, but still I cannot get a NTFS partition that windows will recognise.

here is the output of sudo fdisk -l:

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3ffc3ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            3163       29270   209712510   83  Linux
/dev/sda2           29271       30401     9084757+   5  Extended
/dev/sda3   *           1        3162    25398733+   7  HPFS/NTFS
/dev/sda5           29271       30401     9084726   82  Linux swap / Solaris

```

First I tried making the NTFS following the ext3 - windows installer did not recognise any hard  drive.  Then I tried putting the NTFS *first*, (took 6 hours to move the ext3 behind the NTFS) - still windows installer does not recognise there being any hard drive.  I changed the flag of the partition to boot (think that this has no effect anyway, but worth a try).  I essentially did the same as this tutorial:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

No windows recognition of there being *any* hard drive in this computer (lenovo ideapad y510).

Also as a side question, what is the extended partition?  It is the same size as the swap, but I am unsure of its purpose.

Thanks
nick

---

### Post by Titan8990 on 2008-12-23
If this is a computer that came pre-installed with Vista and you are trying to install XP, it may never detect your drives.

---

### Post by lun on 2008-12-23
That is the case.  I wish it was not, but it is.  Would the xp installer recognise the hard drive if it was still formatted with vista?  Why does this happen?  Would vista recognise an NTFS created by gparted?

This is really disappointing news :sad:

---

### Post by Carl Hamlin on 2008-12-23
> **Titan8990 said:**
> If this is a computer that came pre-installed with Vista and you are trying to install XP, it may never detect your drives.

-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

Ayup. I had this problem on an Acer Extensa 5620 that a client wanted Vista replaced with XP on.

XP just plainly couldn't see the drive. Period.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklRGlUACgkQyLm4ydrABveP5QCg58CSWNWnt8rzX8sl+qwKLtjh
QqIAn3//U/jfsjVhHvMiIdtMUTHldy0t
=DmXt
-----END PGP SIGNATURE-----

---

### Post by Titan8990 on 2008-12-23
> That is the case. I wish it was not, but it is. Would the xp installer recognise the hard drive if it was still formatted with vista? Why does this happen? Would vista recognise an NTFS created by gparted?

This is really disappointing news 


It is because a few companies are producing computers with hardware that only runs on Vista. It my be possible to load the SATA controller drivers via a floppy (F6 during Windows install startup).


My friend who had this issue even tried writting all zeros to the drive with no luck.

Anyways, if you were to get it going in XP, there is a good chance you will lack essential drivers such as NIC drivers.

---

### Post by lun on 2008-12-23
The only version of vista they have in stock here at school is upgrade, no full install.  Do you know if you can request an windows install disk from the manufacturer you bought your laptop?  I also thought about the possible lack of drivers if I installed xp, but figured I would try it.

Thanks for the replies.

---

### Post by Titan8990 on 2008-12-23
> Do you know if you can request an windows install disk from the manufacturer you bought your laptop?


Most of the time you can. If it is not under warranty they may charge you shipping and handling.

---

### Post by dagnabit dang doohickey on 2008-12-23
[Resolving "Setup did not find any hard disk drives" during Windows XP Installation]("http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/")

---

### Post by Titan8990 on 2008-12-23
> **dagnabit dang doohickey said:**
> [Resolving "Setup did not find any hard disk drives" during Windows XP Installation]("http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/")


That appears to be a long complicated way of accomplishing the "hit F6 and load drivers from floppy" for people without a floppy drive.

---

### Post by lun on 2008-12-23
> 
That appears to be a long complicated way of accomplishing the "hit F6 and load drivers from floppy" for people without a floppy drive.

...which is me.

Thanks for the responses - I now know what my problem is.  I will try getting the installation disk from Lenovo.  Should I mark this as solved? :???:

nick

---

### Post by dagnabit dang doohickey on 2008-12-23
What is this "floppy drive" thing you speak of?
:)

---

### Post by balaknair on 2008-12-23
[http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/](http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/)

Since the problem is missing SATA drivers for XP, wouldn't disabling SATA control from BIOS make XP see the hard drive? After installing XP and installing the drivers you could just reset the SATA settings to default.

---

### Post by lun on 2008-12-23
> 
Since the problem is missing SATA drivers for XP, wouldn't disabling SATA control from BIOS make XP see the hard drive? After installing XP and installing the drivers you could just reset the SATA settings to default.

Did the trick.  Turned AHCI to compatible and xp recognised the NTFS partition.  FAQ number 4 here:

[http://forums.lenovo.com/lnv/board/message?board.id=ideaPad&thread.id=488](http://forums.lenovo.com/lnv/board/message?board.id=ideaPad&thread.id=488)

Thanks to everyone who has helped out.  I now have a 'nice' install of windows.

Cheers
nick

---

### Post by balaknair on 2008-12-23
Great
Glad to help.

---

