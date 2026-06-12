---
title: "ubuntu partition erased, but still boots"
date: 2009-05-28
forum: General Help
---

### Post by revalion on 2009-05-28
After reformatting my Ubuntu partition, the GRUB loader still appears when I turn on my computer and I can succesfully boot into Ubuntu. Yet, since the partition was reformatted I can't find where the system is located on my harddrive. It obviously shouldn't be there. I don't know how it's still there. I now run Ubuntu off my flash drive, and I would like to simply run Vista from my harddrive. Does anyone know how I can figure out where Ubuntu is on my harddrive?

p.s. the Ubuntu system came back after running the commands:
[FONT=Fixedsys][SIZE=2]sudo grub
grub> find /boot/grub/stage1
grub> foot (hd0,4)
grub> setup (hd0,4)
grub> quit[/SIZE][/FONT]
which I entered when I meant to run to fix the grub on my flashdrive but apparently fixed the grub on my flashdrive.

---

### Post by mdurham on 2009-05-29
I think you need to be a bit clearer. Do you have both Windows and Ubuntu on the hard drive? If you remove the Ubuntu you won't be able to boot into Windows without restoring the MBR by using the Windows install disk.

What does this mean?
> I meant to run to fix the grub on my flashdrive but apparently fixed the grub on my flashdrive. 

---

