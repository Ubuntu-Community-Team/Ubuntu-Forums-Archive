---
title: "GRUB error 21"
date: 2008-12-20
forum: General Help
---

### Post by medioxcore on 2008-12-20
hi guys!

i recently installed intrepid ibex on an external (previously internal.  from an old laptop) HD.  it has some problems, and everything i've read says ubuntu runs a little buggy when booted from a USB drive, so i'm thinking about just wiping the drive and using it solely for storage.  my problem is that whenever i don't have the external plugged in, when i try to boot, i get "error 21" and my computer freezes.  i'm worried that if i just wipe the drive, the files GRUB is looking for wont be there, and i will never be able to completely boot.  am i wrong?

suggestions?

---

### Post by cdtech on 2008-12-20
You probably installed the GRUB bootloader to the MBR of the primary drive. Which OS do you have on the computer without the USB connected? If it's windows you will have to repair the MBR with an installation disc. If it's Linux you'll just need to reinstall the GRUB bootloader.

---

### Post by logos34 on 2008-12-20
> **medioxcore said:**
>   it has some problems, and everything i've read says ubuntu runs a little buggy when booted from a USB drive, so i'm thinking about just wiping the drive and using it solely for storage.

I never had any problems on mine, booting or otherwise...sure it was a little slower (~35 MB/s) but hardly noticeable in everyday use.

---

### Post by medioxcore on 2008-12-20
> **cdtech said:**
> You probably installed the GRUB bootloader to the MBR of the primary drive. Which OS do you have on the computer without the USB connected? If it's windows you will have to repair the MBR with an installation disc. If it's Linux you'll just need to reinstall the GRUB bootloader.

its vista :/

well... it's a dual-boot.  vista/hardy heron

how do i go about repairing the MBR

---

### Post by cdtech on 2008-12-20
If you have the install disk you can use that, if not you could use the "testdisk" program

---

### Post by caljohnsmith on 2008-12-20
Medioxcore, you can restore a Windows equivalent MBR to your Windows drive from Ubuntu by opening a terminal (Applications > Accessories > Terminal) and doing:
```
sudo lilo -M  /dev/sda mbr
```
That assumes your internal drive is sda, which it should be; but if by chance it isn't, you'll need to change that in the above command. How about giving that shot and let us know how it goes.

---

