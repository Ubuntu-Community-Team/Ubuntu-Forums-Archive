---
title: "Restore GRUB"
date: 2006-05-26
forum: Desktop Environments
---

### Post by seshomaru samma on 2006-05-26
I was following the instructions[ here]("http://ubuntuforums.org/showthread.php?t=56723&page=2") on how to dual boot Ubuntu and Windows XP without changing the Windows MBR. I copied the bootloader into a floppy but (surprise, suprise) the floppy died on me and now I can't boot into Ubuntu . Can I copy a bootloader from another Ubuntu machine ,burn it to a CD /usb /floppy and boot from it ? if so ,which file do I need to copy . 
thanks

---

### Post by aysiu on 2006-05-26
Dual-boot's a lot easier if you use Grub instead of Windows' boot loader.

Maybe these two links might help you:
[https://wiki.ubuntu.com/GrubHowto/BootFloppy](https://wiki.ubuntu.com/GrubHowto/BootFloppy)
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by johnc4510 on 2006-05-26
Insert your install cd and boot to it.
At the splash screen(before the install starts) type: rescue
The installer will start, answer the initial questions language, etc.
When you are asked which partition you wish to mount, select the partion you mounted Ubuntu on.
Then enter the following command: grub-install /dev/hda
Remove the cd from the drive and reboot. You should see the boot menu.

---

### Post by erniewinner on 2006-05-28
i too would rather use a seperate boot cd as i have faffed with grub all day... i dont' have a floppy. can anyone answer this question? thanks. :rolleyes:

---

