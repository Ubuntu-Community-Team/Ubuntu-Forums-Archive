---
title: "Cloning Win hard drive?"
date: 2008-12-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lee292 on 2008-12-23
I have an Inspiron 8500 I bought used without operating system or driver discs. I currently am swapping hard drives back and forth to run Win XP Pro and Ubuntu. The Win disk (Hitachi 40GB) is showing its age and before it dies, I want to install a new, bigger hard drive (Samsung HM160HC, 160GB), and have both Win XP and Ubuntu on it in a dual-boot system.  I've read that you can clone the hard drive by booting up with a Live CD and using the dd command.   Once I get Win, I can reinstall Ubuntu from the CD.  First,how do I use dd to copy my Win drive to my USB backup drive, and then copy the image to the new drive.  Second, how can I reinstall Ubuntu's many updates beside a lengthy online session?

---

### Post by logos34 on 2008-12-23
You could first copy the entire 40 GB drive to the USB drive, like this:

> [Cloning an entire hard disk]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/How_To_Do_Eveything_With_DD"):

dd if=/dev/sda of=/dev/sdb conv=notrunc,noerror

In this example, sda is the source. sdb is the target. Do not reverse the intended source and target. Surprisingly many people do. notrunc means to not truncate. noerror means to keep going if there is an error. Normally dd stops at any error. if you have a question about a hard drive on whether or not it works, you can try to use it as the source drive for the dd command. You should get an error if it is not working. target drives need to be really messed up to give an error in dd.

Then swap in the empty 160 GB and reverse the process:

> dd if=/dev/sdb of=/dev/sda conv=notrunc,noerror

You should have a bootable windows at this point, since the above command copies everthing including the MBR.

Do the same procedure for linux, except copy only the / partition to USB:

> dd if=/dev/sda1 of=/dev/sdb1 bs=4096 conv=notrunc,noerror

Swap the 160 GB drive back in.  Use Gparted on the live cd to create a second partition (sda2), ext3, and copy ubuntu / to it like this:
> [URL="http://www.brunolinux.com/02-The_Terminal/The_dd_command.html"]
dd if=/dev/sdb1 of=/dev/sda2 bs=4096 conv=notrunc,noerror[/URL]

Create a /swap and change the UUID in /etc/fstab to match.

oh, and add windows [boot entry]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu") and [mountpoint]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#Ubuntu%208.10%20(Intrepid%20Ibex)%20and%20Ubuntu%208.04%20LTS%20(Hardy%20Heron)").

at least that's the way I'd probably do it.  

good luck

---

