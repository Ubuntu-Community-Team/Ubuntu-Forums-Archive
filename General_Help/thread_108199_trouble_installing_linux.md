---
title: "trouble installing linux"
date: 2005-12-25
forum: General Help
---

### Post by Snaaky on 2005-12-25
Ok, I've been trying too install ubuntu with a dual boot with windows. I've installed windows and am now trying too install ubuntu on a different hard drive. (My windows hd is a sata drive and I have a amd64) I work through the installation and partition the hd for the swap partition and a main partition. I then continue to install. It gets to a point where it installs grub and then wants to restart and boot from the hard drive. The first time I tried it it booted into windows, and the second time I just got an error and wanted me to insert a system disk. I've tried playing with the boot settings in bios but it doesn't seem 2 make any difference. Does anyone know what would cause this? Maybee I'm setting up the partitions wrong?

Thanks for any help.

---

### Post by rcerreto on 2005-12-25
Likely you're not installing grub (linux bootloader) in the right place.
If your bios is set to boot from your first SATA disk, it should go to /dev/sda
During the installation process, while installing grub, you're asked where to install it.
Can you remember what you answered?

---

### Post by Snaaky on 2005-12-25
the linux installer detects windows and ask me if I want 2 install it 2 the master boot record. I selected yes, because I assumed that that would put it in the right place. It never gave me the oportunity to specify a location. Is there a way to specify it?

---

### Post by Snaaky on 2005-12-25
ok, some good news, some bad news, I reinstalled everything, and when the linux installer restarted the computer after installing grub it actually booted grub. Bad news is it immediatly gave me and error. 

stage1.5ReadError 

Does anybody know what this is/ how to fix it?

---

### Post by rcerreto on 2005-12-26
You say that windows disk is SATA, what about the ubuntu one. Is it SATA as well or IDE?
Something is going wrong during grub install and we have to understand what.
Could you post /boot/grub/device.map ?
It could be helpful.

---

### Post by Snaaky on 2005-12-26
Ubuntu drive is IDE.

How do I post "/boot/grub/device.map" 

I did manage to repair the MBR so that I could boot into windows again although I am not able 2 boot into linux.

---

### Post by briancurtin on 2005-12-26
[QUOTE=Snaaky]How do I post "/boot/grub/device.map"[/QUOTE]
```
cat /boot/grub/device.map
```
and just paste what gets displayed there into a post

---

