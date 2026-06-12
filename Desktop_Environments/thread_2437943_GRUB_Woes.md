---
title: "GRUB Woes"
date: 2020-03-03
forum: Desktop Environments
---

### Post by Geoff_Lane on 2020-03-03
Folks,

How can I disable all GRUB menu entries except the Custom Entries?

update-grub  grub-mkconfig and grub-install are giving me nightmares when I try to tidy up the menu on an external drive, I've somehow ended up losing GRUB from my main internal drive although I did not knowingly touch it, drive letters change depending on which one boots.  Had to reinstall GRUB to internal drive and now all OK - except for the untidy menu.

I'd just like to use Custom Menu only.

Would it be merely change the permissions to scripts in /etc/grub.d/     ?

Geffers

---

### Post by Dennis N on 2020-03-03
> How can I disable all GRUB menu entries except the Custom Entries?
It's done with changing permissions of files in /etc/grub.d

Most important is to make **30_os-prober** non-executable.
For strictly custom menu entries only, you can do the same with 10_linux and 20_memtest86+, but I opt to leave these alone.

Run sudo update-grub after changes.

---

### Post by Geoff_Lane on 2020-03-03
> **Dennis N said:**
> It's done with changing permissions of files in /etc/grub.d

Most important is to make **30_os-prober** non-executable.
For strictly custom menu entries only, you can do the same with 10_linux and 20_memtest86+, but I opt to leave these alone.

Run sudo update-grub after changes.

Thank you, will do so now.

Geoff

---

### Post by oldfred on 2020-03-03
UEFI or BIOS.
You do need to make sure you boot external drive from external drive.
Default install using Ubuntu's Ubiquity only installs grub to first drive, usually internal drive & sda or first NVMe drive.
With BIOS you can specify during Something Else install, but that does not work with UEFI installs.

Old info, but still valid (I think). I turn off os-prober and use 40_custom, but let it find kernels in my install.
Grub2 info by ranch hand and many links to other grub2 info sites
[http://ubuntuforums.org/showthread.php?p=8191211#post8191211](http://ubuntuforums.org/showthread.php?p=8191211#post8191211)

From Ranch hand
You only need 3 scripts for grub to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09, 25, 40)


How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by Geoff_Lane on 2020-03-05
> **oldfred said:**
> 
From Ranch hand
You only need 3 scripts for grub to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09, 25, 40)



All O/Ss are UEFI

When I had the problems identified in the other thread posted recently I merely stopped the Linux file 02 and 03 probe from running and everything went wrong from there.

My main problem is trying to understand where the grub boot-loader is getting its config files from.  Every Linux distro has the same named config files, if a subsequent O/S is installed does it uses those config files or the original installation.

I have an external disk, almost without fail when I boot to it it comes up with the menu that I have on my internal drive, kill the power,restart and correct menu then appears.

Geoff

---

### Post by yancek on 2020-03-05
>  My main problem is trying to understand where the grub boot-loader is getting its config files from. 

If all your systems are UEFI, you can have only one set to boot first from the system board and EFI partition.  If you have multiple UEFI systems installed with separate directories for each on the EFI partition, you can change which boots in he BIOS firmware boot options one time only or in the BIOS firmware on a permanent basis.  Methods vary with manufacturer.  Each OS should have a separate directory in the EFI partition and will point to the remaining/necessary boot/grub files on the / (root filesystem) partition for that OS.

---

### Post by oldfred on 2020-03-05
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Geoff_Lane on 2020-03-07
> **yancek said:**
> If all your systems are UEFI, you can have only one set to boot first from the system board and EFI partition.  If you have multiple UEFI systems installed with separate directories for each on the EFI partition, you can change which boots in he BIOS firmware boot options one time only or in the BIOS firmware on a permanent basis.  Methods vary with manufacturer.  Each OS should have a separate directory in the EFI partition and will point to the remaining/necessary boot/grub files on the / (root filesystem) partition for that OS.

Thank you.

Geoff

---

### Post by Geoff_Lane on 2020-03-07
> **oldfred said:**
> 

From Ranch hand
You only need 3 scripts for grub to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09, 25, 40)



I've disabled 10_linux using same command, that seems to work OK though it does find a Fedora installation, and of course Windoz (appreciate the disabled file looks for Linux) and puts both in the menu.

But if I subsequently disable probe by sudo chmod -x 30_os-prober followed by  update-grub then my custom entries do not load and when I boot it goes  to BIOS after a pause as it seems there are no entries to boot.

Geoff

---

### Post by yancek on 2020-03-07
Did you read post #7 above by oldfred?  You indicate multi-boot but not what you are multi-booting or how many hard drives you have or how many EFI partitions or which OS is set to boot first from the BIOS.  All these and more questions can be answered if you run boot repair as suggested by oldfred and post the link to the output here!  Otherwise, it's just going to be a lot of guessing.

---

### Post by oldfred on 2020-03-07
Lots of examples here. Read first few, then jump to end & work backwards for latest info.
[https://ubuntuforums.org/showthread.php?t=2076205](https://ubuntuforums.org/showthread.php?t=2076205)

Where are you putting you custom entries?
You do not put them into /boot/grub/grub.cfg as it gets refreshed with every grub or kernel update.
See notes at top of that file.

---

### Post by Geoff_Lane on 2020-03-07
> **oldfred said:**
> Lots of examples here. Read first few, then jump to end & work backwards for latest info.
[https://ubuntuforums.org/showthread.php?t=2076205](https://ubuntuforums.org/showthread.php?t=2076205)

Where are you putting you custom entries?
You do not put them into /boot/grub/grub.cfg as it gets refreshed with every grub or kernel update.
See notes at top of that file.

Custom entries in 40_custom in /etc/grub.d/

Geoff

---

### Post by Geoff_Lane on 2020-03-07
> **yancek said:**
> Did you read post #7 above by oldfred?  You indicate multi-boot but not what you are multi-booting or how many hard drives you have or how many EFI partitions or which OS is set to boot first from the BIOS.  All these and more questions can be answered if you run boot repair as suggested by oldfred and post the link to the output here!  Otherwise, it's just going to be a lot of guessing.

I have and internal drive on a Toshiba laptop which has Winows10, Ubuntu 18:04 and Fedora.  It has a UEFI partition.

An external USB drive also has a UEFI partition, it then has two primary partitions with Ubuntu Mate 18:04 and Raspberry Pi desktop for PC.  I've then got an extended partition and within two logical partitions, one running Debian, the other PCLinuxOS

I am able to start all OS with the internal drive booting but am able to press F12 and get BIOS to boot 2nd drive.

So all OK except if I disable script 30_os-probe using chmod-x then the custom entries (40_custom) don't appear when update-grub is run so as grub menu empty nothing to boot so machine jumps to bios.

So, question was; why does disabling 30_os-prober appear to stop 40_custom from running?

Geoff

---

### Post by oldfred on 2020-03-07
Post this:
ls -l /etc/grub.d

If you have files with proxy in the name, then those are from Grub customizer.

---

### Post by Geoff_Lane on 2020-06-19
> **yancek said:**
> Did you read post #7 above by oldfred?  You indicate multi-boot but not what you are multi-booting or how many hard drives you have or how many EFI partitions or which OS is set to boot first from the BIOS.  All these and more questions can be answered if you run boot repair as suggested by oldfred and post the link to the output here!  Otherwise, it's just going to be a lot of guessing.

Didn't really need to, my previous post referrred to disabling various scripts in the /etc/grub.d/ folder that resolved the issue.

Geoff

---

