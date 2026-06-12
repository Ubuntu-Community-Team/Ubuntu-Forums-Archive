---
title: "Dell XP dual boot issue"
date: 2010-09-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by 2sondad on 2010-09-10
I'm sure this has been asked before but I cannot find the correct answer for my situation.

I have a Dell Inspiron 6000 with XP on it.  I dual installed 10.04 and had an issue with the dual boot.  I went to reinstall Ubuntu and it was deleted. That partition was gone.

Now I only have the XP partition but when I boot I get "grub rescue".
I tried to use the Live CD but it won't boot.

Any help is appreciated.

---

### Post by oldfred on 2010-09-11
Welcome to the forums.

Did you install with wubi the first time? It does not have partitions, just a file inside windows.

To get CD to boot you have to have CD/DVD set in BIOS to boot first and a bootable liveCD. Did you burn CD at slowest speed your CD writer allows and do a mdsum to make sure the download was good?

To get XP to boot you can use a windows XP disk and run from repair console fixMBR. Or from a Ubuntu liveCD :

Restore basic windows style boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want lilo installed to the MBR

---

### Post by 2sondad on 2010-09-11
It was a complete install on a partitioned drive.  It was not installed within Windows.  I have changed the BIOS to only boot from the CD/DVD drive and I have tried booting with both an XP disk and an Ubuntu disk.  (Not one I burned myself, but the one that Canonical shipped.)

Either way, I get a message that says "no partition" then "grub rescue".

---

### Post by oldfred on 2010-09-11
Those error messages sound more like they are from the hard drive, but no partition does not sound good. But some BIOS want a boot flag on a primary partition. Grub rescue says grub is installed to the MBR but cannot find grub.cfg or the grub partition.

Has your CD stopped working? Two disks not working would mean either the setting did not stick or it is not working. Some do require both BIOS and the one time boot key to also select CD to choose it.

---

### Post by 2sondad on 2010-09-11
I guess I will try making a USB "LIVE" and try booting from that.  As far as I know the CD drive works.  I hadn't used that particular laptop in about 2 years.  It had an XP issue that I had finally fixed.   I wanted to only install Ubuntu but I kept XP because I had some programs I wanted my 8 year old to start using to help him in school.

---

### Post by 2sondad on 2010-09-13
Here's what worked for me and I highly suggest it to others.  On 10.04 I made my USB stick "live" and then I changed my software sources to include CD under Administration.

I then did 3 things in the terminal.

1.  sudo apt-get update
2.  sudo apt-get install lilo                      (which is on the live CD)
3.  sudo lilo -M  /dev/sda mbr

Life is good.

---

