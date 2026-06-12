---
title: "Computer randomly boots from different hard drives."
date: 2008-12-22
forum: General Help
---

### Post by Alex Carroll on 2008-12-22
I've installed Ubuntu 8.10 on one IDE hard drive, and Windows XP on another SATA drive. When booting up, the computer appears to detect one after the other, often leading me to boot straight into Windows without seeing the GRUB menu. A few (there isn't a set number) restarts later, the GRUB menu will appear first, allowing me a choice of Ubuntu or Windows.

This is quite frustrating when I want to use Ubuntu for something, only to be sent to Windows. I'm not sure if it is a problem with the way GRUB is installed, or if it is a hardware problem, but I'm hoping somebody can shed some light on what is happening.

---

### Post by DieB on 2008-12-22
pls check if your bios offers boot priorities, like first for boot and make the ide number one.

it seems to be a hardware issue.

---

### Post by gTinker on 2008-12-22
[QUOTE=Alex Carroll]I've installed Ubuntu 8.10 on one IDE hard drive, and Windows XP on another SATA drive. When booting up, the computer appears to detect one after the other, often leading me to boot straight into Windows without seeing the GRUB menu. A few (there isn't a set number) restarts later, the GRUB menu will appear first, allowing me a choice of Ubuntu or Windows.

This is quite frustrating when I want to use Ubuntu for something, only to be sent to Windows. I'm not sure if it is a problem with the way GRUB is installed, or if it is a hardware problem, but I'm hoping somebody can shed some light on what is happening.[/QUOTE]

I did a quick forum search because I remembered seeing a thread about a similar issue to what you describe. See if there is anything to help you in this thread:
[http://ubuntuforums.org/showthread.php?t=1017978&highlight=IDE+sata+grub](http://ubuntuforums.org/showthread.php?t=1017978&highlight=IDE+sata+grub)

---

### Post by Alex Carroll on 2008-12-22
DieB: I have tried changing boot priorities, but the problem is that the other hard drive will not be detected until an operating system boots.

gTinker: Thanks for the link, but he appears to be able to control which operating system he boots by changing the drive controller settings, in my case there doesn't appear to be an option.

---

### Post by Alex Carroll on 2008-12-22
Ok, it appears to he a hardware issue; disabling the SATA boot option left me unable to boot any OS - save for the 8.10 Live CD - until the IDE drive started being detected.

---

### Post by gTinker on 2008-12-22
> **Alex Carroll said:**
> I've installed Ubuntu 8.10 on one IDE hard drive, and Windows XP on another SATA drive. When booting up, the computer appears to detect one after the other, often leading me to boot straight into Windows without seeing the GRUB menu. A few (there isn't a set number) restarts later, the GRUB menu will appear first, allowing me a choice of Ubuntu or Windows.

This is quite frustrating when I want to use Ubuntu for something, only to be sent to Windows. I'm not sure if it is a problem with the way GRUB is installed, or if it is a hardware problem, but I'm hoping somebody can shed some light on what is happening.

Looking at what you are describing, it appears that you have GRUB in the MBR of the IDE drive and the DOS/Windows bootloader in the MBR of the SATA. Additionally, it appears that your BIOS doesn't always enumerate your drives in the same order. If you were able to replace the Windows bootloader with GRUB pointing to the /boot on the IDE drive, I would expect your GRUB menu to come up no matter which drive was enumerated first. Don't try to do this if any part doesn't make sense to you. Ask about anything you don't understand and wait for confirmation from someone else reading this before you act. Since I don't have your hardware to test, my theory might not be correct and you probably have a reason you've set up your system as you have. One further question, does your GRUB menu.lst mount partition by device node or UUID?

---

### Post by Alex Carroll on 2008-12-22
Yes, GRUB is on the Ubuntu IDE drive and the Windows bootloader is on the SATA drive. I attempted to put GRUB on the Windows disk yesterday with AutoSuperGrubDisk, but it was unable to do it. Regarding your last question, I'll have to check the menu.lst file when I'm next in Ubuntu, since I'm currently playing TF2 in windows.

---

### Post by Alex Carroll on 2008-12-23
gTinker: Yes, the GRUB menu appears to boot by UUID;

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		837b62e3-c107-47b1-b120-c31e8fbb0b61
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=837b62e3-c107-47b1-b120-c31e8fbb0b61 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

---

