---
title: "? Dual Booting XP with Ubuntu 9.04 ?"
date: 2009-06-06
forum: General Help
---

### Post by AnimeFreak on 2009-06-06
ok I want dual boot xp with 9.04

i have 2 80 gig hard drives 

Slave has Ubuntu 9.04 

Master is blank = i want xp on here

will the grub boot loader be affected?

plz help

---

### Post by michy99 on 2009-06-06
Yes the boot loader will be affected, but you can fix it afterwards. The easiest way is with the Supergrub Disk.

---

### Post by AnimeFreak on 2009-06-06
> **michy99 said:**
> Yes the boot loader will be affected, but you can fix it afterwards. The easiest way is with the Supergrub Disk.


What is that 



i am a noob 
i beg for patience

---

### Post by Krupski on 2009-06-06
> **AnimeFreak said:**
> ok I want dual boot xp with 9.04

i have 2 80 gig hard drives 

Slave has Ubuntu 9.04 

Master is blank = i want xp on here

will the grub boot loader be affected?

plz help

A nice way to do it is to use the Windows "NTLDR" boot manager to boot up both Windows and Ubuntu.

Here's how to do it... if you need more explanation, please let me know.

(1) Install Windows XP on the "master" drive first.

(2) Install Ubuntu on the "slave" drive next.

(3) At the end, say "yes" to where Grub asks "install to the master boot record".

(at this point, your Windows XP boot loader is hosed.... but don't worry we'll fix it).

(4) Boot up Ubuntu and make a copy of the Windows master boot record (which is actually now Grub). Do it like this:

```

sudo dd if=/dev/sda of=linux.bin bs=512 count=1

```

(5) COPY the new file "linux.bin" to a floppy or to a USB stick... whatever to save it for later.

(6) Reboot into the Windows XP install CD. Choose "Repair using the recovery console".

(7) Log into the Windows XP administrator account.

(8 ) Replace the Windows boot files like this:

```

C:\> fixboot
C:\> fixmbr
C:\> exit

```

(9) Your Windows XP should boot up normally again. Once in Windows, open a command line window (run CMD.EXE)

(10) Unhide your boot.ini file:

```

C:\> attrib -r -h -s -a boot.ini

```

(11) ADD this line to the end of your boot.ini file:

```

C:\linux.bin="Boot UBUNTU"

```

(12) Re-hide your boot.ini file:

```

C:\> attrib +r +h +s +a boot.ini

```

(13) Lastly, take that "linux.bin" file you made in Ubuntu and copy it to the root directory of your Windows XP drive.


That's it! Upon next bootup, you should see a choice to boot Windows or Ubuntu.

Good luck!

-- Roger

---

### Post by mmarquardt on 2009-10-07
This seems like very good information, but it doesn't work for me because I think I have an unusual installation of windows xp.  I had a dual boot windows me and windows xp on a single 60 gigabyte drive.  I then added a 160 gigabyte drive as a slave drive.  I installed ubuntu successfully on the 160 gigabyte drive from the ubuntu live cdrom, but I cannot boot the drive I think because the bios on my machine does not recognize drives larger than 80 gigabytes so I get an error 18 when grub tries to boot anything.  I can still boot xp with a boot floppy I made, but I cannot restore the boot process on the master drive which is C.  XP is on D.  I cannot boot the drive with ubuntu with a master boot manager floppy though I think xp will boot from there also.  I cannot install the windows recovery console in xp I think due to the grub problem.  I cannot start the windows recovery console from the xp install cdrom because of the administrative password problem that I gather may be a bug in early versions of the windows xp cdrom.  Is there any way to boot into the ubuntu system on the hard drive from the ubuntu live cdrom without using grub?  Is there any other way to boot ubuntu on the hard drive without using grub?  Any help is appreciated.  Thanks.

---

