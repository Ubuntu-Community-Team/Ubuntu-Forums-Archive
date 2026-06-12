---
title: "GRUB/System Update Problem"
date: 2015-12-13
forum: Desktop Environments
---

### Post by shag00 on 2015-12-13
When I log on to Ubuntu 15.10 I have a little red triangle with an exclamation mark in it. Pressing that tells me I have some issue with out of date repositories and in the drop down menu there are a few options, one of which is install updates. When I press that a new window opens called, "Upgrading System", underneath it says, "configuring grub-pc". Opening the details button shows:
 
processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be profiled on next reboot
processing triggers for systemd (225-1ubuntu9) ...
setting up grub-pc (2.02~beta2-29) ...
grub-install: cannot find a GRUB drive for /,. Check your device map.
Installing for i386-pc platform.
grub-install: cannot find a GRUB drive for /,. Check your device map.
Installing for i386-pc platform.
grub-install: cannot find a GRUB drive for /,. Check your device map.

Now I did have some issue a week or so ago where I used a program to fix the boot which I suspect may be the cause of this problem.

The PC boots up fine and everything works, I am just after a way to correct and remove this problem.

---

### Post by yancek on 2015-12-13
I would suggest that the best way to get information is to get the boot repair iso and burn it to a CD.  After booting it, you should see an option to Create BootInfo Summary.  Make sure you select that and do not make any changes.  You can then post a link here to the output and someone might be able to help.

---

### Post by grahammechanical on 2015-12-13
The update must also include an update to grub itself and the upgrade is not being completed for the reason given. And so, the system is still recording out of date repositories because the upgrade of grub has not been completed.

Update manager will let you de-select packages from being upgraded. That might be one way of allowing the system to complete the general update/upgrade task. It would be a temporary fix.

Regards.

---

### Post by oldfred on 2015-12-13
Did grub originally get installed to a different drive?
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short

---

### Post by shag00 on 2015-12-13
@yancek

Contrary to what I said in my first post, all is not well as I cannot install anything without the installing grub window popping up.

My boot partition is sda1 which is not listed as a location in that window. Does sda1 need to be mounted for boot-repair to find it, as I don't normally mount it?

If it helps I only want to boot from sda1, not every disk.

The link to the boot info summary is: [URL="http://paste.ubuntu.com/13998955/"]http://paste.ubuntu.com/13998955/

[/URL]

---

### Post by shag00 on 2015-12-13
@ oldfred

That command gave:
scott@scottlounge:~$ grub-pc/install_devices:
bash: grub-pc/install_devices:: No such file or directory
scott@scottlounge:~$ sudo debconf-show grub-pc 
[sudo] password for scott: 
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices:
  grub-pc/chainload_from_menu.lst: true
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/install_devices_disks_changed:
  grub-pc/timeout: 10
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/kopt_extracted: false
  grub-pc/partition_description:
  grub2/device_map_regenerated:
  grub2/kfreebsd_cmdline:
  grub-pc/install_devices_empty: false
  grub2/force_efi_extra_removable: false
  grub-pc/disk_description:
  grub2/linux_cmdline:
  grub-pc/install_devices_failed: false
  grub2/linux_cmdline_default: quiet splash
  grub-pc/hidden_timeout: true
  grub2/kfreebsd_cmdline_default: quiet splash
scott@scottlounge:~$ 

and 

scott@scottlounge:~$ sudo lshw -C Disk -short
H/W path         Device     Class          Description
======================================================
/0/2/0.0.0       /dev/sda   disk           120GB INTEL SSDSC2CW12
/0/3/0.0.0       /dev/sdb   disk           4TB ST4000DM000-1F21
/0/4/0.0.0       /dev/sdk   disk           2TB ST2000DL003-9VT1
/0/5/0.0.0       /dev/sdl   disk           4TB WDC WD40EZRX-00S
/0/6/0.0.0       /dev/sdm   disk           2TB ST2000DM001-9YN1
/0/7/0.0.0       /dev/sdn   disk           4TB WDC WD40EFRX-68W
/0/9/0.0.0       /dev/sdc   disk           4TB ST4000DM000-1F21
/0/a/0.0.0       /dev/sdd   disk           4TB ST4000DM000-1F21
/0/b/0.0.0       /dev/sde   disk           4TB ST4000DM000-1F21
/0/c/0.0.0       /dev/sdf   disk           4TB ST4000DM000-1F21
/0/d/0.0.0       /dev/sdg   disk           4TB WDC WD40EZRX-00S
/0/e/0.0.0       /dev/sdh   disk           4TB WDC WD40EFRX-68W
/0/f/0.0.0       /dev/sdi   disk           4TB WDC WD40EZRX-00S
/0/10/0.0.0      /dev/sdj   disk           4TB WDC WD40EZRX-22S

---

### Post by oldfred on 2015-12-13
grub-pc/install_devices:

That says grub is not installed to any drive.

You do not install the grub2 boot loader to a partition. You only install it to the MBR of the Ubuntu drive.
And Boot-Repair's default is to install to every drive, for those users who do not know which drive is the boot drive in BIOS. But with multiple drives you only want the advanced options, choose Ubuntu install and sda (drive) not any partition like sda1.

I use gpt on all new or totally repartitioned drives since 10.10. But for BIOS boot a gpt partitioned drive has to have a tiny 1 or 2MB unformatted partition with bios_grub flag to install correctly to MBR.

---

### Post by shag00 on 2015-12-13
I was under the impression GRUB was needed to boot the PC but as its boots up that's obviously not the case which begs the question, is GRUB necessary if I only have 1 OS installed?

Assuming it's not needed how do I stop the program (grub-pc pagkage) from trying to install even after a reboot?

I think the problem is solved thanks to the replies here and this thread: [http://ubuntuforums.org/showthread.php?t=1593193](http://ubuntuforums.org/showthread.php?t=1593193), as I don't have the red triangle and can install software.

---

### Post by oldfred on 2015-12-13
Grub is the Ubuntu standard boot loader. You have to have some boot loader to start system.

But if you only have one system, grub menu will not normally appear & you can set timeout down. I do not suggest 0 seconds as there may be a time you need to get into menu for recovery or repair.

---

