---
title: "Drive Encryption with dual boot"
date: 2010-05-30
forum: Desktop Environments
---

### Post by waliu on 2010-05-30
Hello,

I have a DELL Latitude E6410 64bit with Core i5. My goal is to have my Windows 7 encrypted and my Ubuntu 10.4 unencrypted and to be able to boot them both.

So here are the details. I installed windows 7 first. Then I installed Ubuntu and GRUB was in the MBR. Then I started TrueCrypt 5 from Windows 7 and encrypted the system partition, not the whole drive! So the TrueCrypt loader overwrote the GRUB in the MBR. Now when I start my computer, i see the prompt for password from the TrueCrypt boot loader. If I enter my password, windows is loaded. The other option at the beginning is to press Esc and that should offer me other boot loaders. Well, on my DELL there's this RECOVERY partition and it boots immediately. So, does anyone know how I can integrate the GRUB in the process.

I know, that there are many howto-s on the internet about this problem, but I haven't found a solution for grub2 and windows 7! It is indeed different, because GRUB does not have menu.lst any more and Windows 7 does not have boot.ini!

Here some more info about my partitions:
```

/dev/sda1   fat16          DellUtility
/dev/sda2   ntfs           RECOVERY
/dev/sda3   unknown
/dev/sda4   extended
 - /dev/sda5   ext4        ubuntu
 - /dev/sda6   linux-swap

```
Windows 7 in installed on /dev/sda3 and is encrypted, that's why the file system is unknown.
Ubuntu 10.4 is installed on /dev/sda5

I know of three options to deal with the problem:

**solution 1**
Install GRUB to the PBR (partition boot record) of the linux partition - that's /dev/sda5 in my case. Then, it should be possible to load GRUB when you press Esc in the TrueCrypt boot loader.

**solution 2**
Make Windows load Linux. Copy the PBR of the linux partiotion to a file and copy the file to windows. Then add an entry in the windows loader to include the linux loader file.

**solution 3**
Make GRUB load TrueCrypt's boot loader. Make a backup of the MBR (containing the TrueCrypt's loader). Add Truecrypt’s MBR as a chain boot loader in GRUB. Finally, rewrite the MBR using this new GRUB.

I will appreciate it very very much (and I'm sure others will be looking for this solution) if someone can post exact steps for solutions 2 and 3. Just remember, there's no boot.ini in win 7 and there's no menu.lst in /boot/grub.

I personally prefer solution 1, because the only way to see that there's a linux partition is to press Esc at the beginning. Normally, I can input my pass to the TrueCrypt boot loader and no one watching behind me will know, that I have linux ;)

I did install GRUB to my PBR with 
```

from the live CD:
first mount /dev/sda5 to /media/ubuntu
sudo grub-install --root-directory=/media/ubuntu /dev/sda5

```
I also tried with 
```

from inside ubuntu:
> grub
grub> find /boot/grub/stage1
hd0,4
grub> root (hd0,4)
grub> setup (hd0,4)
grub> quit

```
After one of these, I am able to boot my ubuntu after restart. But then I reboot and load windows, reboot once again and press Esc in order to try to boot ubuntu again, and then I don't see the grub loader list, but the "grub> " shell prompt instead! I thought that I will be able to see the grub loader also after many restarts, not just the first time...

Do you have an idea why this configuration "breaks" after 1-2 reboots? Maybe the problem is that my ubuntu is on an extended partition (sda4)?

Thanks in advance!
Regards,
waliu

---

### Post by sidzen on 2010-05-30
I had similar problem with two linux distros -- yeah, bootable root (/) must be on a Primary partition. (I've seen some even recommend a separate 512 - 1024MB /boot partition formatted to ext2) -- good deduction!

---

### Post by waliu on 2010-06-01
Hello again,

I deleted the extended partition, created new primary and installed ubuntu there. That fixes the problem indeed. I still hope that s.o. will post a howto for the other 2 solutions, it's interesting how to do it with grub2 and win7 boot manager...

Cheers!

---

### Post by thegeologician on 2011-06-09
Hi,
just got me a Dell Latitude E6420, and want to do the exact same thing - has anyone found a solution to do it with GRUB2 (and Windows 7)?

---

