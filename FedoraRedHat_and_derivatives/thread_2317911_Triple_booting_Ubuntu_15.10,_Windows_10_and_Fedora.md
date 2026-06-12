---
title: "Triple booting Ubuntu 15.10, Windows 10 and Fedora 23."
date: 2016-03-21
forum: Fedora/RedHat and derivatives
---

### Post by amantripathi4u on 2016-03-21
Hello community. Currently  I am running Ubuntu 15.10 in dual boot mode with Windows 10. Both are running fine. I want to install Fedora 23 on a triple boot configuration on my system. But apparently all of these operating systems use different boot loaders. I don't know how to configure boot loaders. I googled a lot but couldn't find relavent information. Kindly tell me proper steps to triple boot above mentioned OSs. Thanks.

---

### Post by grahammechanical on 2016-03-21
Ubuntu & Fedora use the same Linux boot loader - Grub 2. There are differences as to how the OS manipulate Grub. Fedora requires this command to reconfigure the Grub configuration file (grub.cfg)

```
grub2-mkconfig -o /boot/grub2/grub.cfg
```

Ubuntu provides us with a script. So, we run

```
sudo update-grub
```

And the script does the job.

To install (reinstall) Grub Fedora uses

```
grub2-install /dev/sda
```

Ubuntu uses

```
sudo grub-install /dev/sda
```

Points to keep in mind.

1) The last Linux distribution to be installed will put is version of Grub into place over-writing the Grub version installed by the first distribution of Linux.
2) As each Linux gets updates to the kernel and Grub it is likely that Grub will be reinstalled as part of the process. So, the last Linux to be updated will end up in control of the Grub boot menu.

Select a distribution of Linux to be in control of the boot menu. If you want that to be Ubuntu, then after Fedora is installed boot into Ubuntu from the menu provided by Fedora and run those two Ubuntu commands.

Repeat each time that Fedora takes back control of the boot menu. I use this same method because I have different versions of Ubuntu installed. 

[https://fedoraproject.org/wiki/GRUB_2?rd=Grub2](https://fedoraproject.org/wiki/GRUB_2?rd=Grub2)

If you decide to delete an install of Linux first make sure that the Linux that you want to keep is in control of the boot loader as you will not be able to load the remaining Linux. Similarly, if you want to remove Linux completely and leave Windows as the only OS, you need to restore the Windows boot loader before removing Linux.

Regards.

---

### Post by oldfred on 2016-03-21
Does Fedora use LVM as default partitioning?

I have seen where some suggest just using an ext4 partition similar to Ubuntu as one of the advantage of LVM is when entire drive is LVM. 

And if Fedora is in LVM, you have to add the LVM drivers back into Ubuntu to be able to mount or add Fedora's grub entries.

---

### Post by Dennis N on 2016-03-21
I have Fedora 23 (actually Korora 23 - a respin) installed on this computer and it uses the same grub as Ubuntu. It's installer is called Anaconda, and is very good, but has a non linear approach that is unlike ubiquity. If you are doing UEFI, you can create multiple ESP system partitions. I have three for example. The installer will default to making an LVM installation, but I selected the standard installation. I have it multibooting with my other distros in a UEFI system, which of course includes a couple of Ubuntu flavors. 

I would recommend Korora 23 over Fedora 23 as has all the multimedia stuff ready to go and is themed up very nicely. Otherwise you will spend a lot of setup time. Under the hood, they are the same.

Edit: I should add that I don't have any Windows OS on the system - things work better without Windows.

---

### Post by Dennis N on 2016-03-21
> **oldfred said:**
> And if Fedora is in LVM, you have to add the LVM drivers back into Ubuntu to be able to mount or add Fedora's grub entries.

Isn't the LVM support built into the kernel? 

At least the newest Ubiquity is capabable of detecting and installing to an LVM logical volume. But it cannot create them*. So you have to set up the LVM first. I recently installed 16.04 beta1s into LVM logical volumes on my test machine - BIOS with GPT - done both with a separate boot on a standard partition and also everything in the root partition in the logical volume. These are mixed with standard non-LVM installs. Newest Grub detects them all, LVM and non-LVM, and can boot them all.

*when using the "something else" partition editor.

---

### Post by Dennis N on 2016-03-21
> Fedora requires this command to reconfigure the Grub configuration file (grub.cfg): ```
grub2-mkconfig -o /boot/grub2/grub.cfg
```
In Fedora, I constructed an alias for the command and included it in .bashrc (mine is for a UEFI system):
```
alias update-grub='sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg'
```

---

### Post by oldfred on 2016-03-21
I watch install process and I see it un-install LVM & RAID drivers as well as gparted and many other things after install, based on what/how you install.

I immediately go back and install gparted so I can work on other than my mounted drive(s).

---

### Post by Dennis N on 2016-03-21
So, I guess not. Checked the menu entry for one of the LVM installs, and it has "insmod lvm" included.

---

### Post by howefield on 2016-03-21
Moved to "*Fedora/RedHat and derivatives*" forum.

---

