---
title: "WTH???...  Grub problem with Dual-Boot &amp; XP"
date: 2010-05-05
forum: Desktop Environments
---

### Post by keithld on 2010-05-05
I got some updates the other day and now I have no Windows XP showing up in the Grub Menu....

I did **NOT** update to 10.04 LTS...

Any ideas guys on how to fix this????


Thx.

---

### Post by grumpy.medic on 2010-05-05
I had a similar issue after updating (but I was already on Lucid at that time). It is possible that something in GRUB loader files got corrupted.

What do you exactly see? Do you still see GRUB but no windows partition?

When you boot Ubuntu under System>Administration>Gparted if it is not there open terminal and type:

```
sudo apt-get install gparted
```

It will prompt, say YES. After install type:

```
sudo gparted
```

You will see your swaps and other partitions. Is your XP partition still visible?

Cheers!

---

### Post by keithld on 2010-05-05
Yes it's still there:

[IMG]http://img.photobucket.com/albums/v342/KeithLDick/ntfs.png[/IMG]

---

### Post by grumpy.medic on 2010-05-05
> **keithld said:**
> Yes it's still there:

[IMG]http://img.photobucket.com/albums/v342/KeithLDick/ntfs.png[/IMG]

Chances are that your MBR was damaged and now is not addressing your NTFS partition properly.

**[COLOR="Red"]Please only do the following if you have everything backed up... I can not guarantee no data loss. Please be aware of that![/COLOR]**

[LIST]
[*]Use your XP recovery/install disc and boot to it.

[*]When prompted press R to repair Windows XP install

[*]If prompted enter your Admin password (Windows)

[*]If there is an option to select multiple OSs, choose Windows XP

[*]To fix the MBR type the following:

```
fixmbr
```

[*]This assumes that your installation is on the C:\ drive. You will be presented with several scary warning lines the reading of which will make you want to say no. Microsoft is exceptionally vague regarding the conditions under which fixmbr can cause problems although they are clear about the consequences (losing all data on the hard drive), so use this at your own risk.

[*]Type Y and ENTER to fix your MBR

[*]Do not worry if it finishes in less than a second, the MBR is very small.

[*]After it is done, leave the recovery and reboot.
[/LIST]

I hope this will help you out!

Cheers!

---

### Post by keithld on 2010-05-05
Thanks I'll it in a bit...

It won't hurt Grub and I will thill have a dual-boot?


Cheers,

Keith

---

### Post by grumpy.medic on 2010-05-05
> **keithld said:**
> Thanks I'll it in a bit...

It won't hurt Grub and I will thill have a dual-boot?


Cheers,

Keith

Well... it should not hurt it. The caveat to that is, when I had the same issue going on with my netbook, it was with Win7. And I used the Win7 recovery disc, which is a little more advanced than XP's recovery. Worst case, you might have to do a recovery on GRUB/Ubuntu to get your boot loader back.

Like said, if you can, make a back up. But as of now, your NTFS partition is not accessible as your BIOS does not know what to do with the information provided = bad MBR.

I wish I could give you a definite answer, it appears to be the same case, even though the circumstances are different.

:-/

---

### Post by keithld on 2010-05-06
Anyone else have any suggestions???

---

### Post by nitstorm on 2010-05-06
Sorry if this sounds elementary but did you run 
```

sudo update-grub

```
(if you are working with Grub2 that is..)

---

### Post by keithld on 2010-05-06
Yes did that...

Just Checked and it's Grub 1.97 Beta 4

---

### Post by xDarkicex on 2010-05-06
I didnt even know gparted had a GUI I always use the terminal 
Windows recovery disk check your partitions

---

### Post by nitstorm on 2010-05-06
> Yes did that...

Just Checked and it's Grub 1.97 Beta 4 	

Then +1 to grumpy.medic's post on fixing the MBR. And please do back-up, just in case. Better safe than sorry. And if you do lose the Grub while fixing the MBR follow [THIS]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html") link to get back the grub.

---

### Post by keithld on 2010-05-06
Thanks Nitstorm...

---

### Post by grumpy.medic on 2010-05-06
> **xDarkicex said:**
> I didnt even know gparted had a GUI I always use the terminal 
Windows recovery disk check your partitions

Most people don't. But it is in GUI form on the live discs... it helps visualize your partitions imo :-)

---

### Post by grumpy.medic on 2010-05-06
> **nitstorm said:**
> Then +1 to grumpy.medic's post on fixing the MBR. And please do back-up, just in case. Better safe than sorry. And if you do lose the Grub while fixing the MBR follow [THIS]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html") link to get back the grub.

nitstorm, that is a good walkthrough, I just wish I would have had that about 4 months ago :-/ 

Oh... and thanks for helping out!

---

### Post by keithld on 2010-05-06
Forgot to mention.. I can mount the Windows partition fine and look at files, copy stuff etc... So everything is still there...

Weird thing is I was checking to see what Version of Grub I have and the grub.cfg file showed up and from what I read Grub 2 uses that and Grub legacy uses menu.lst (I think)..

So looking in the grub.cfg the Windows boot entry is in there but whats weird is when Grub comes up on Boot it says it's: version 1.97 Beta 4...

Weird

---

### Post by grumpy.medic on 2010-05-07
> **keithld said:**
> Forgot to mention.. I can mount the Windows partition fine and look at files, copy stuff etc... So everything is still there...

Weird thing is I was checking to see what Version of Grub I have and the grub.cfg file showed up and from what I read Grub 2 uses that and Grub legacy uses menu.lst (I think)..

So looking in the grub.cfg the Windows boot entry is in there but whats weird is when Grub comes up on Boot it says it's: version 1.97 Beta 4...

Weird

That is odd. IMHO I would go ahead and attempt to fix the MBR and if necessary rebuild the GRUB loader. That will probably serve you best.

Cheers!

---

### Post by oldfred on 2010-05-07
Lets take a look at your entire boot process:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by keithld on 2010-05-07
Okay here's the results

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders, total 156312576 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa6aaa6aa

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   110,880,629   110,880,567   7 HPFS/NTFS
/dev/sda2         110,880,630   156,312,449    45,431,820   5 Extended
/dev/sda5         110,880,693   154,336,454    43,455,762  83 Linux
/dev/sda6         154,336,518   156,312,449     1,975,932  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        AA4405FD4405CCCF                       ntfs                                     
/dev/sda5        9daa9ae6-55ff-44b1-91d7-3381247bd451   ext4                                     
/dev/sda6        0148582f-f5dd-4ce9-a6ce-2ef8141a1bc9   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 9daa9ae6-55ff-44b1-91d7-3381247bd451
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9daa9ae6-55ff-44b1-91d7-3381247bd451
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=9daa9ae6-55ff-44b1-91d7-3381247bd451 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9daa9ae6-55ff-44b1-91d7-3381247bd451
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=9daa9ae6-55ff-44b1-91d7-3381247bd451 ro single 
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9daa9ae6-55ff-44b1-91d7-3381247bd451
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=9daa9ae6-55ff-44b1-91d7-3381247bd451 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9daa9ae6-55ff-44b1-91d7-3381247bd451
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=9daa9ae6-55ff-44b1-91d7-3381247bd451 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9daa9ae6-55ff-44b1-91d7-3381247bd451
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=9daa9ae6-55ff-44b1-91d7-3381247bd451 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9daa9ae6-55ff-44b1-91d7-3381247bd451
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=9daa9ae6-55ff-44b1-91d7-3381247bd451 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9daa9ae6-55ff-44b1-91d7-3381247bd451
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=9daa9ae6-55ff-44b1-91d7-3381247bd451 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9daa9ae6-55ff-44b1-91d7-3381247bd451
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=9daa9ae6-55ff-44b1-91d7-3381247bd451 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9daa9ae6-55ff-44b1-91d7-3381247bd451
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=9daa9ae6-55ff-44b1-91d7-3381247bd451 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9daa9ae6-55ff-44b1-91d7-3381247bd451
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=9daa9ae6-55ff-44b1-91d7-3381247bd451 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9daa9ae6-55ff-44b1-91d7-3381247bd451
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=9daa9ae6-55ff-44b1-91d7-3381247bd451 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9daa9ae6-55ff-44b1-91d7-3381247bd451
	linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=9daa9ae6-55ff-44b1-91d7-3381247bd451 ro single 
	initrd	/boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9daa9ae6-55ff-44b1-91d7-3381247bd451
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=9daa9ae6-55ff-44b1-91d7-3381247bd451 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 9daa9ae6-55ff-44b1-91d7-3381247bd451
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=9daa9ae6-55ff-44b1-91d7-3381247bd451 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set aa4405fd4405cccf
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=9daa9ae6-55ff-44b1-91d7-3381247bd451 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0148582f-f5dd-4ce9-a6ce-2ef8141a1bc9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  62.6GB: boot/grub/core.img
  61.7GB: boot/grub/grub.cfg
  57.1GB: boot/initrd.img-2.6.31-14-generic
  58.3GB: boot/initrd.img-2.6.31-15-generic
  58.7GB: boot/initrd.img-2.6.31-16-generic
  58.1GB: boot/initrd.img-2.6.31-17-generic
  63.4GB: boot/initrd.img-2.6.31-19-generic
  63.2GB: boot/initrd.img-2.6.31-20-generic
  64.7GB: boot/initrd.img-2.6.31-21-generic
  57.3GB: boot/vmlinuz-2.6.31-14-generic
  58.2GB: boot/vmlinuz-2.6.31-15-generic
  58.5GB: boot/vmlinuz-2.6.31-16-generic
  58.8GB: boot/vmlinuz-2.6.31-17-generic
  62.9GB: boot/vmlinuz-2.6.31-19-generic
  63.2GB: boot/vmlinuz-2.6.31-20-generic
  63.3GB: boot/vmlinuz-2.6.31-21-generic
  64.7GB: initrd.img
  63.2GB: initrd.img.old
  63.3GB: vmlinuz
  63.2GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by keithld on 2010-05-07
Also if I end up fixing the MBR and Grub is gone are there any Newbie instructions on how to get it back???

Thanks guys...

Keith

---

### Post by oldfred on 2010-05-07
I do not see anything wrong in your boot configuration.

You can install bootloaders with this information:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Sometimes totally reinstalling grub and putting into the MBR solves problems, sometimes running sudo update-grub solves issues.

These instructions are to uninstall old grub & new grub so if you get an error on grub ignore it.

purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common

sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by keithld on 2010-05-07
purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common

sudo grub-install --recheck /dev/sda
sudo update-grub[/QUOTE]


Well I did the above and it trashed everything, no Grub no boot at all and my Windows Recovery CD was bad so I have to get Windows reinstalled at the shop... NEW Install as he could fix the old install...

My Question now is can I get to the Ubuntu partition and at least recover my Firefox BookMarks???? then get rid of the Ubuntu partitions????

I have the other stuff I wanted to keep from Ubuntu but I forgot to Export my Firefox Bookmarks...

This is kinda souring me on Ubuntu now so I think I'll wait a few weeks before I try Ubuntu again so they can fix more bugs...

Thanks for the help Guys..

---

### Post by oldfred on 2010-05-07
The above command would not of trashed system. What error messages did you get?  You can always reinstall grub or a windows boot loader per post #20.

You can use any liveCD to get into your installed partition to copy files. You also can chroot into it to repair it if just reinstalling grub to the MBR does not work.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You can also install a windows boot loader from linux liveCD or install.
sudo  apt-get install lilo
sudo lilo -M /dev/sdX mbr

---

### Post by keithld on 2010-05-07
At this point all I want is my Bookmarks from Firefox on Ubuntu...

Maybe in the future I'll just set up a separate box with Ubuntu but now I'm hearing that Grub does indeed mess things up in the Windows MBR so I'm not going to chance that again...

---

### Post by oldfred on 2010-05-07
The problem with grub is not users per se. The instructions assumes users know the difference between drive and partition and installing grub to a drive's MBR vs. a partition's  PBR. The say to install to all drives but everyone is confused and they present a list of all drives and partitions. If you have windows then you overwrite the windows boot in the PBR. Windows uses both the MBR and the PBR to boot.

If you install grub to only the drive MBR you will be ok. I am not sure upgrade is the best way anyway. You do not get to upgrade to ext4 nor use grub2, both are considered improvements although since they are changes some do not like changes. I am not a convert to clean installs since Karmic after upgradeing every 6 months for 3 years.

---

