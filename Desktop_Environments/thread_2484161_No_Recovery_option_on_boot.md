---
title: "No Recovery option on boot"
date: 2023-02-19
forum: Desktop Environments
---

### Post by tapasray on 2023-02-19
My notebook was in dual-boot mode with Windows 10 factory installed but Ubuntu 22.04 set as default OS. I had to delete Windows and reinstall Ubuntu 22.04 LTS as the sole OS on account of certain problems. While in dual-boot mode, GRUB used to present me with Ubuntu boot in both normal and recovery modes, as well as Windows. But now that there is only Jammy, no option is given at boot. I have tried to enter Recovery mode through Shift+Escape, 1, and various F keys at boot following instructions on askubuntu (1) and other sites. Nothing has helped. I need to run Recovery urgently as the machine has become very slow, surprisingly after the change-over to a single-OS configuration. I want to get back the options at boot. How can I get them? Please help. Thanks in advance.

---

### Post by grahammechanical on 2023-02-19
Question

How did you delete Windows? There should be a small partition formatted as FAT 32 and called an EFI System Partition. It will contain boot files for both Windows and Ubuntu. If we delete that partition then the Grub boot loader no longer exists.

The Grub boot menu only appears when we are booting Ubuntu with another OS or two. If we only have Ubuntu then we will not see the Grub boot menu. With a UEFI based motherboard we can press the ESC key (perhaps several times). That should (may) bring up the Grub boot menu with the Advanced Options choice.

Regards

---

### Post by tapasray on 2023-02-19
Thanks, @grahammechanical. I think I merged all the partitions, formated to NTFS and installed Ubuntu, which created its own partitions (Ext4). I just checked and a 505 MB EFI partition does exist still. Can I work with it to get Advanced Options somehow even though I have only Ubuntu now and no other OS? Maybe I should install another light-weight OS just to get GRUB running?

---

### Post by tapasray on 2023-02-19
It's getting late here. Thanks in advance if you respond, I shall get to see it after some hours. The same to anyone else who may respond.

---

### Post by oldfred on 2023-02-19
When you only have one install, grub just automatically boots.
With UEFI install you should press escape key just after vendor logo, but before grub menu would normally appear to get grub menu. Timing often quick and you may have to try more than once.
If UEFI fast boot on, then you may not have time to press any key. Check UEFI settings.
Or full cold boot from total power down will give normal boot, if fast boot on.

---

### Post by tapasray on 2023-02-19
Thanks, @oldfred. I shall try this.

---

