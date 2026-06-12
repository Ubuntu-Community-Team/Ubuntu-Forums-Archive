---
title: "[Quad Boot] Predict what will happen?"
date: 2009-05-30
forum: General Help
---

### Post by S-Fraz on 2009-05-30
Currently I'm triple booting Vista, Windows 7, and Ubuntu. I want to add XP to the list.
Here is my drives structures, currently:

+=== Disk 1 ===+
||{ Partitions:
| 1. RECOVERY [Has some XP files. Came with computer]
| 2. Vista OS
| 3. Linux OS
| 4. Linux Swap
||}
+==============+

+=== Disk 2 ===+
||{ Partitions:
| 1. Global Files [I just use it for anything, no OS installed]
| 2. Unallocated [This is where I want to install XP]
| 3. Windows 7 OS
||}
+==============+

The first OS I had installed was Vista. I then installed Ubuntu with GRUB. This had me dual booting. I then installed Windows 7.
After installing Windows 7 I was unable to boot Ubuntu (I could boot Vista as Windows 7 came with a boot loader. It just didn't support Linux).

To fix this I went into Ubuntu's live cd and re-wrote GRUB to the MBR. After this I could then boot Vista, Ubuntu, and Windows 7. BUT, not all by GRUB. Windows 7 also installed a boot loader.
My GRUB Boot loader is something like this:

Ubuntu Hardy (Version number...)
Windows 7 and Vista
Windows XP install [This is the recovery drive]

If I go to Ubuntu Hardy, it loads the OS right up. If I go to Windows 7 and Vista, it doesn't. In stead it loads Windows 7's boot loader, which then allows me to boot Vista or Windows 7.

Make sense? I'm guessing GRUB is stage 1 and Windows boot loader is 2? Not sure.

Anyway, what I'm wanting to do is install XP on partition 2 of disk 2. I'm predicting it to over write GRUB and leave XP only boot-able. This is fine as I can go back to the Ubuntu live cd and re-write GRUB. But now I'm wondering if XP will also over-write the windows 7 loader. If that happens I would no longer be able to boot Windows 7 nor Vista. I would then have to re-write the Windows 7 boot loader and bla bla bla, it gets complicated. Would XP over-write both GRUB and win7 loader?

Hopefully I made some sense and gave enough information.
Thanks.

---

### Post by xavierp94 on 2009-06-06
> **S-Fraz said:**
> Currently I'm triple booting Vista, Windows 7, and Ubuntu. I want to add XP to the list.
Here is my drives structures, currently:

+=== Disk 1 ===+
||{ Partitions:
| 1. RECOVERY [Has some XP files. Came with computer]
| 2. Vista OS
| 3. Linux OS
| 4. Linux Swap
||}
+==============+

+=== Disk 2 ===+
||{ Partitions:
| 1. Global Files [I just use it for anything, no OS installed]
| 2. Unallocated [This is where I want to install XP]
| 3. Windows 7 OS
||}
+==============+

The first OS I had installed was Vista. I then installed Ubuntu with GRUB. This had me dual booting. I then installed Windows 7.
After installing Windows 7 I was unable to boot Ubuntu (I could boot Vista as Windows 7 came with a boot loader. It just didn't support Linux).

To fix this I went into Ubuntu's live cd and re-wrote GRUB to the MBR. After this I could then boot Vista, Ubuntu, and Windows 7. BUT, not all by GRUB. Windows 7 also installed a boot loader.
My GRUB Boot loader is something like this:

Ubuntu Hardy (Version number...)
Windows 7 and Vista
Windows XP install [This is the recovery drive]

If I go to Ubuntu Hardy, it loads the OS right up. If I go to Windows 7 and Vista, it doesn't. In stead it loads Windows 7's boot loader, which then allows me to boot Vista or Windows 7.

Make sense? I'm guessing GRUB is stage 1 and Windows boot loader is 2? Not sure.

Anyway, what I'm wanting to do is install XP on partition 2 of disk 2. I'm predicting it to over write GRUB and leave XP only boot-able. This is fine as I can go back to the Ubuntu live cd and re-write GRUB. But now I'm wondering if XP will also over-write the windows 7 loader. If that happens I would no longer be able to boot Windows 7 nor Vista. I would then have to re-write the Windows 7 boot loader and bla bla bla, it gets complicated. Would XP over-write both GRUB and win7 loader?

Hopefully I made some sense and gave enough information.
Thanks.
I found an article that may help you S-Fraz. By the way i'm Dr.Vista from Bryansoft. :D
[http://lifehacker.com/5126781/how-to-dual-boot-windows-7-with-xp-or-vista](http://lifehacker.com/5126781/how-to-dual-boot-windows-7-with-xp-or-vista)

---

### Post by 3Miro on 2009-06-06
My guess is that you have to install XP and the reinstall Grub. (It is unlikely that XP would see Vista or 7)

---

