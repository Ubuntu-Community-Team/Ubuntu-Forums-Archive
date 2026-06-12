---
title: "How do I get rid of Ubuntu?"
date: 2009-05-30
forum: General Help
---

### Post by Crazy Joe Divola on 2009-05-30
I've been reading various threads on the forum that discuss this topic (it seems to be a common occurrence) but none of them have answered my questions, or worked for me at all. 

I had been using an older Dell laptop (CD drive, no floppy) to play around with various Linux distros, thing is, I need to get Windows back on this machine now. The thing will simply not boot into the XP Set up from the CD, but instead, is cut off by the Grub. It was never a dual-boot or anything like that, and I have absolutely no problem with getting rid of the entire Ubuntu partition, I just have no idea how to do it. I tried cfdisk, and it did not work.

---

### Post by kestrel1 on 2009-05-30
Boot with the live Ubuntu CD & use Gparted to remove the ubuntu partitions & leave the entire drive as free space. Once you apply this & then use the Windows CD you should be up & running.

---

### Post by jimbob on 2009-05-30
You should be able to catch the BIOS immediately upon boot start with one of the Fx keys and change the boot order to boot from the cd BEFORE it even gets to the Grub menu.

---

### Post by Crazy Joe Divola on 2009-05-30
> **kestrel1 said:**
> Boot with the live Ubuntu CD & use Gparted to remove the ubuntu partitions & leave the entire drive as free space. Once you apply this & then use the Windows CD you should be up & running.

I will give that a try. If I have any further problems I will post them. Thanks for the reply.

---

### Post by kestrel1 on 2009-05-30
> **jimbob said:**
> You should be able to catch the BIOS immediately upon boot start with one of the Fx keys and change the boot order to boot from the cd BEFORE it even gets to the Grub menu.
I have found that if the entire drive is allocated to Ubuntu or Linux of any type that the Windows CD will not boot as it complains about the drive. Can't remember what at present, but essentially it thinks the drive is bad.

---

### Post by ugm6hr on 2009-05-30
> **kestrel1 said:**
> I have found that if the entire drive is allocated to Ubuntu or Linux of any type that the Windows CD will not boot as it complains about the drive. Can't remember what at present, but essentially it thinks the drive is bad.

Indeed, XP installers refuse to recognise any ext formatted partitions.

However, this is not the problem here; you should still be able to boot from the CD.

If you have installed and played with LiveCDs, you should know how to boot from a CD.

Nevertheless, try formatting the HD with GParted to FAT and try again.  Or use ActiveKillDisk (or similar disk wiping tool).

---

### Post by kestrel1 on 2009-05-30
> **ugm6hr said:**
> Indeed, XP installers refuse to recognise any ext formatted partitions.

However, this is not the problem here; you should still be able to boot from the CD.

If you have installed and played with LiveCDs, you should know how to boot from a CD.

Nevertheless, try formatting the HD with GParted to FAT and try again.  Or use ActiveKillDisk (or similar disk wiping tool).
Personally I wouldn't bother formatting the drive to FAT, just leave it blank & let Windows format the drive to NTFS when it needs to. I have always found that the best way. Just my opinion of course.

---

### Post by lisati on 2009-05-30
[http://ubuntuforums.org/showthread.php?p=7373453](http://ubuntuforums.org/showthread.php?p=7373453)

---

### Post by meho_r on 2009-05-30
> **kestrel1 said:**
> I have found that if the entire drive is allocated to Ubuntu or Linux of any type that the Windows CD will not boot as it complains about the drive. Can't remember what at present, but essentially it thinks the drive is bad.

Strange, I had Mandriva with ext4 and had to replaced it with WindowsXP for testing purposes. Boot from CD went OK and it even recognized all partitions (though as "unknown", but there were there). I deleted them and install WinXP with no problem.

@OP: Beside other tips, check your WinXP disc if it's OK and is bootable.

---

### Post by kestrel1 on 2009-05-30
> **meho_r said:**
> Strange, I had Mandriva with ext4 and had to replaced it with WindowsXP for testing purposes. Boot from CD went OK and it even recognized all partitions (though as "unknown", but there were there). I deleted them and install WinXP with no problem.
Luck of the draw I suppose. :lolflag:

---

### Post by c1rcu1t on 2009-05-30
GParted always worked for me when in this situation

---

