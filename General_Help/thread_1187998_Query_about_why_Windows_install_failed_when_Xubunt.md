---
title: "Query about why Windows install failed when Xubuntu installed"
date: 2009-06-15
forum: General Help
---

### Post by Total Noob on 2009-06-15
I have an old laptop; tried to reinstall Windows 95 from original purchased disk, but computer would not boot from disk, instead loading the Linux that was already there.

Later discovered it was not a Bios issue; Linux based CD's booted just fine. So then I thought it might be an MBR or GRUB issue. But DOS recovery and boot CD's intended to fix MBR didn't work either.

Is it just a coincidence Or is there something funky between Linux and the Bios that shut out the microsoft stuff?

Thanks.

---

### Post by Celauran on 2009-06-15
If other bootable disks are booting fine, I'd have to say it's your Win95 disk that's wonky.

---

### Post by JKyleOKC on 2009-06-15
When Win95 came out, booting from CD was not yet an option. Consequently it was necessary to boot from a floppy (with CD support) and then run SETUP.EXE from the CD. Not until Win98 was the CD itself bootable. This is quite likely the reason for your problem.

---

### Post by Total Noob on 2009-06-16
Dear JKyle:

  That sounds like the answer; I never before tried to install Win95 on a laptop, always booting from a floppy in a desktop or tower.

  How would I get to a DOS prompt using a laptop with no floppy drive? When I tried, I got a GRUB error from the Debian that was there before.

  Thanks.

---

### Post by mk1w86 on 2009-06-16
You could try FreeDOS

[http://www.freedos.org/](http://www.freedos.org/)

---

