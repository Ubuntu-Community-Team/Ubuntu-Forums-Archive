---
title: "noob needs help w/ multiple boot"
date: 2005-10-22
forum: Desktop Environments
---

### Post by malacoda on 2005-10-22
Hello,

I've played with Ubuntu Breezy, am now dabbling w/ Kubuntu Breezy and am attempting to install Fedora Core 4 and PCLinuxOS on my drive as well - as a noob I just want to try a few linux flavors before settling on one...

Anyhow,  At present I have Win XP (trying to wean myself off it which is whole reason for trying all these linux distros) on an IDE hd and Kubuntu on a SATA.  Dual boot for this setup is working fine.

I'm now trying to add the other 2 distros to the SATA along side Breezy.  I've partitioned and installed Fedore next to Kubuntu and during install did NOT change or overwrite existing GRUB.  

My problem is that, during Fedora download, iso burn, and install I didn't see any reference to the kernal #.:confused: 

I think *<--key word* my next step is to edit GRUB to include a listing for the Fedora install but I don't know what commands can be used - either in KDE or terminal (or *gulp*...Windows) - to determine what the Fedora kernel # is so I can attempt to edit GRUB.  My serach of the Fedora site and core 4 release notes didn't turn up anything either... in every instance I found it was just referred to as Core 4...

Can anyone tell me how I can find out the kernel info for a distro install I can't yet boot into?

thanks,
Malac

---

### Post by paddyg on 2005-10-22
Why don't you mount Fedora partition in ubuntu and take a look at fedora /boot?

PS: i tried fedora 4 as soon as it was out (i was using fedora 1). Well, i was disappointed and i switched to Hoary. Never regretted that! D'you wanna know what? Updates & program repositories: i don't think rpm is as solid as apt-get.

---

