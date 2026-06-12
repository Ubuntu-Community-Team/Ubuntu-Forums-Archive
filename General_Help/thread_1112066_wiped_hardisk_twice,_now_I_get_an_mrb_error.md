---
title: "wiped hardisk twice, now I get an mrb error"
date: 2009-03-31
forum: General Help
---

### Post by Vincenso Andolini on 2009-03-31
Hello all,

I endeavoured to flatten windows permanently on my computer. This is a process I had completed recently on another computer with no problems. On the computer in question I used Hiren's Boot Cd with Acronis Disk Director and wiped the hardisk twice over. Now when I try to boot from a cd, an Ubuntu cd, the computer (BIOS?) does not allow it and says "MBR ERROR".

I can press F12 upon startup to access Hirens Boot CD but I cannot boot from an Ubuntu disc. I want to install Ubuntu.

Does anybody know how I can fix this? I assume that the hardisk has a corruption in the master reboot file (?), but I am new to working with hardisks in this manner so I am not sure what to do.

All help is appreciated.

Vincenso

---

### Post by kanikilu on 2009-03-31
> **Vincenso Andolini said:**
> Hello all,

I endeavoured to flatten windows permanently on my computer. This is a process I had completed recently on another computer with no problems. On the computer in question I used Hiren's Boot Cd with Acronis Disk Director and wiped the hardisk twice over. Now when I try to boot from a cd, an Ubuntu cd, the computer (BIOS?) does not allow it and says "MBR ERROR".

I can press F12 upon startup to access Hirens Boot CD but I cannot boot from an Ubuntu disc. I want to install Ubuntu.

Does anybody know how I can fix this? I assume that the hardisk has a corruption in the master reboot file (?), but I am new to working with hardisks in this manner so I am not sure what to do.

All help is appreciated.

Vincenso It sounds like your Ubuntu CD is defective or otherwise not bootable. It's not finding a bootable medium in the drive and skipping to try to boot off the hard disk, but that gives an MBR error, naturally, because there is no OS on the hard drive.

I would try re-downloading and burning a new Ubuntu CD.

When you download it again, it's probably worth checking the MD5 of the downloaded ISO:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

And compare it to the MD5 listed here that corresponds to the one you downloaded:

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by lindsay7 on 2009-03-31
Take a look at this and see if this helps. 

[http://support.microsoft.com/kb/69013](http://support.microsoft.com/kb/69013)

---

### Post by kanikilu on 2009-03-31
> **lindsay7 said:**
> Take a look at this and see if this helps. 

[http://support.microsoft.com/kb/69013](http://support.microsoft.com/kb/69013) He's trying to install Ubuntu, fdisk /mbr and fixmbr are used to fix the MBR for Windows. They aren't going to help here, since there is no MBR or Windows to fix (the drive was formatted).

---

