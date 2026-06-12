---
title: "Kernel panic. Linux headers 3.0.0.13 Ubuntu 11.10"
date: 2011-10-22
forum: Desktop Environments
---

### Post by lucacerone on 2011-10-22
Dear all,
whenever I try to boot with linux kernel 3.0.0.13
(the one installed by the upgrades) I get a Kernel Panic error:
> 
VFS: Cannot open root device "sda1" or unknown block (0,0=
Please append a correct "root=" boot option;


Luckily enough if I boot using the previous version I don't have any issue.
How can I solve this? Where should I append the correct root= option?

If I don't get this Kernel to work, how can I remove it as the default
and stick to the older one?

Thanks a lot,
any help is greatly appreciated!

Cheers, Luca

---

### Post by lucacerone on 2011-10-26
No advice for me? Not even how to remove the new kernel and restore the old one as default?

---

### Post by typhoon_tip on 2011-10-26
Try out this one Luca:
[http://www.linuxquestions.org/questions/linux-kernel-70/2-6-19-vfs-cannot-open-root-device-sda1-or-unknown-block-0-0-a-509439/](http://www.linuxquestions.org/questions/linux-kernel-70/2-6-19-vfs-cannot-open-root-device-sda1-or-unknown-block-0-0-a-509439/)

Seems is due to SATA handling differences in the Kernel.

Note: you cannot make the old Kernel the default one ! You should make the new one work and leave the old one alone there. If you cannot start anything you may have to use install CD or USB to enter the partition and edit the conf files manually.

Hope it helps !
Ciao,
Simone

---

### Post by coffeecat on 2011-10-26
> **lucacerone said:**
> Dear all,
whenever I try to boot with linux kernel 3.0.0.13

Have you enabled the proposed repository? At this moment in time, the 3.0.0.13 kernel is only available from the proposed repository. Unless you want to be involved in quality control testing and risk system breakage it is inadvisable to enable the proposed repository.

Disable the proposed repository and uninstall all 3.0.0.13 packages.

---

### Post by lucacerone on 2011-10-26
tnx typhoon and coffeecat!
Actually I was wondering how this linux kernel came on my system.
I cannot do it now, but tonight I'll definitively disable the proposed repository!
When I have disabled the proposed updates how can I restore my packages to the latest stable versions???

Also typhoon mentioned something about the SATA module.
Funny thing is that a few months ago I had issues with my CDRom.
I thought it was broken (Ubuntu got stuck at boot, and I could only solve
by removing the CD from my laptop....) but it seems a bit too of a coincidence that the new issues have arisen on the same module....
How can I check what is wrong?

Thanks for your help guys, it is really appreciated!

---

### Post by typhoon_tip on 2011-10-26
I confirm the above, I checked my 11.10 Kernel version and is 3.0.0.12, so you have probably broken something by using the proposed repository. If you can manage to start, you can disable the proposed repository and get rid of that Kernel to revert back to 3.0.0.12.

---

### Post by lucacerone on 2011-10-26
Yes I know I have the wrong header (I have a perfectly working machine
at work that as the .12 header).

I can access the working linux-image, but after disabling the proposed
repository I don't know how to revert the packages to the version
in the other ones. How can I do that?

Thanks for your help,
cheers, -Luca

---

### Post by typhoon_tip on 2011-10-26
> **lucacerone said:**
> Yes I know I have the wrong header (I have a perfectly working machine
at work that as the .12 header).

I can access the working linux-image, but after disabling the proposed
repository I don't know how to revert the packages to the version
in the other ones. How can I do that?

Thanks for your help,
cheers, -Luca

If you can access it, you can use apt-get

---

### Post by coffeecat on 2011-10-26
> **lucacerone said:**
> 
I can access the working linux-image, but after disabling the proposed
repository I don't know how to revert the packages to the version
in the other ones. How can I do that?

Open Synaptic (install it if it's not already installed - it no longer comes as default in 11.10), search for the string "3.0.0.13", and mark all 3.0.0.13 packages for complete removal. There should be three. The uninstallation process will run update-grub which refreshes the grub menu, so the 3.0.0.12 kernel should then appear as the default.

---

### Post by lucacerone on 2011-10-26
Typhoon I can boot in my old installation and can use apt-get.
My only problem is that I don't know which packages should be removed :)
> **typhoon_tip said:**
> If you can access it, you can use apt-get

---

