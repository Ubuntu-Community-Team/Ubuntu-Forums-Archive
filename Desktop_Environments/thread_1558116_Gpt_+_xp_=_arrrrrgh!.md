---
title: "Gpt + xp = arrrrrgh!"
date: 2010-08-21
forum: Desktop Environments
---

### Post by M_Mynaardt on 2010-08-21
Hi, all!

Well, I've installed Ubuntu on two computers: one older laptop and my netbook.  The Laptop (a bit of an old clunker) is solely on Ubuntu now (goodbye Vista!).  I made my netbook a dual boot with Windows XP and Ubuntu.  So far, so good.

I wanted to make my desktop (on XP) a dual boot computer with XP and Ubuntu.  I ran the installation desk; no problems there.  **_However_**, when I go to start up the computer there is _no_ option to choose between Ubuntu and Windows.  And after some messing about I discovered my desktop does _not_ have a BIOS, but has a GPT instead.  Swell!

What I can't figure out is how does one change the GPT to allow a dual boot system?  I've not been able to find any information on how to do this.  Any suggestions?  (pretty please)

](*,)

---

### Post by corrytonapple on 2010-08-21
Hit shift on startup to get the GRUB options menu.

---

### Post by srs5694 on 2010-08-23
First, you've conflated two related, but distinct, concepts: firmware and partition tables.

Two types of firmware that can be found on PCs today are the old Basic Input/Output System (BIOS) and the newer Extensible Firmware Interface (EFI). The latest EFI implementations often go by the name United EFI (UEFI), so you may see that, too. Most PCs have old-style BIOSes, but Intel-based Macs use EFI, as do a few new non-Mac computers.

Two types of partition tables that are at least somewhat common today are the old-style Master Boot Record (MBR) table, aka MS-DOS partition tables; and the newer GUID Partition Table (GPT). GPT is defined as part of the EFI specification, but GPT may be used on BIOS-based computers, and EFI-based computers can use MBR disks; thus, there's no necessary correlation between the firmware type and the partition table type on any given computer. That said, most EFI-based systems use GPT and most BIOS-based systems use MBR.

It's unclear whether you mean that your desktop is EFI-based or that it has a GPT hard disk. The solution to your problem depends on which of these is the case.

If it's an EFI-based system, you'll need to locate an appropriate boot loader. I'm not an expert on this, but I know that a boot loader called rEFIt is often used on such systems, and GRUB 2 is also supposed to have EFI support.

If you've got a BIOS-based system and a GPT disk, you have more serious problems, since AFAIK no version of Windows supports booting from GPT on a BIOS-based computer. In this case, you'll need to either create a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) to make Windows happy or convert the disk from GPT to MBR form. Hybrid MBRs are flaky and dangerous, so I don't recommend doing this unless you need a quick fix. You can use [GNU Parted](http://www.gnu.org/software/parted/) or [GParted](http://gparted.sourceforge.net/) to convert from GPT to MBR in a destructive way, or my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) to convert while preserving the existing partitions, with caveats. The caveats are that some layouts cannot be completely converted. If you've got more than four partitions, you'll have to have space between some of them to do a complete conversion; without at least a little space, you'll lose some of the partitions. A non-destructive conversion is also inherently risky; it's conceivable you'll end up trashing the whole disk, and it's virtually certain that you'll need to re-install your boot loader.

---

### Post by JBAlaska on 2010-08-23
Theoretically you could boot from a livecd, start gparted and "shrink" the GPT partition from the front by 64kb, make a 64kb linux partition in the free space and set tag "bios_grub" , restart the live cd and reinstall grub.
Theoretically..

**Disclaimer: anytime you shrink or grow a partition, you may loose data! Backup first!**

---

### Post by M_Mynaardt on 2010-08-23
Hi, All!

Okay; I tried the first suggestion of hitting the shift key upon start up.  That didn't work.  Oh well.

I had a closer look at the properties of "My Computer" business on my computer (it's XP Media Centre Edition).  I saw, in the Advanced Tab, Startup and Recovery Option, Edit Startup Options Manually the following 5 lines:
[INDENT][boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect[/INDENT]

Does anyone know if changing anything there will allow me to double boot?  If so, I have no clue what to change it to...

:confused:

---

### Post by oldfred on 2010-08-23
Post this so we can see your exact configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by M_Mynaardt on 2010-08-23
I downloaded that script file, but it's for Linux.   The problem is that I can't seem to access my installed Ubuntu, so I can't use that script on my desktop just at the moment.

Should I make some sort of boot-disk or boot-USB to force my computer to start with Ubuntu?  As a stop-gap measure, until I can get my machine to do a proper dual boot?  I can do that on my laptop that's working just fine with Ubuntu...

I did try the installation thing a second time in the off chance it just plain didn't work.  But it seems that Ubuntu _is_ there.  But Windows is being a pain (as if that's news) and won't let me access it.  The more I look at Ubuntu, the more I think Windows is [COLOR="Red"]**EVIL**[/COLOR]  :evil:

But I digress...

Thanks for the time and patience by the way.  I'm not completely dim about computers, but I am new to Ubuntu, so I'm on the learning curve sort of thing at the moment...

:shock:

---

### Post by oldfred on 2010-08-23
You can run the script from a liveCD or LiveCd on a USB flash drive.  

I would doubt that XP would even let you install to gpt partitions. Did you convert after your install of windows?

---

### Post by M_Mynaardt on 2010-08-24
I'll try the liveCD thing to run that script tomorrow; I just got home from working all evening.

My desktop computer is about 4 years old and has had XP on it the whole time.  I only recently decided to give Ubuntu a go.  Ubuntu is up and running just fine on my old Toshiba Satellite A100 Laptop and my Acer Aspire One Netbook.  So I was feeling confident about making my desktop a dual boot computer like my netbook.  But it was only when I tried to do this dual boot thing that I discovered there was such a thing as a GPT.  Live and learn, eh?

I wouldn't be surprised if the GPT thing is designed to prevent anything but XP on the computer.  Oh well...

:p

---

### Post by srs5694 on 2010-08-24
GPT is definitely not a Microsoft plot; it was created by Intel as part of its Extensible Firmware Interface (EFI) specification. In fact, XP doesn't support GPT on BIOS-based systems; only a few fairly exotic EFI-based systems. Even Vista and Windows 7 won't boot from a GPT disk except on an EFI-based computer. Either you've got such a computer or you accidentally converted the disk from the more common MBR format to GPT.

In terms of GPT support, Linux is far ahead of Windows; Linux can boot from GPT on either BIOS-based or EFI-based computers. The Linux kernel has had GPT support for longer than Windows has, too.

---

### Post by M_Mynaardt on 2010-08-25
HI again!

> **oldfred said:**
> Post this so we can see your exact configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

Okay, I _**finally**_ got around to running that Boot Info Script.  I didn't do it earlier partly because I was doing shift-work (yawn) but mostly because I didn't have a clue how to type in Linux Terminal commands.  Luckily, the Greater Victoria Library has an abundance of Linux books!  \\:D/

After running that script (properly), I got the results at the end of this message.  My question is; **[COLOR="Indigo"]what do I do[/COLOR]** now?  :-?

Thanks in advance for any advice!  :biggrin:

[FONT="Courier New"][COLOR="DarkRed"]
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   545,519,204   545,519,142   7 HPFS/NTFS
/dev/sda2         545,519,205   586,067,264    40,548,060   5 Extended
/dev/sda5         545,519,268   586,067,264    40,547,997   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    88,574,725    88,574,663   7 HPFS/NTFS
/dev/sdb2          88,575,998   234,436,544   145,860,547   5 Extended
/dev/sdb5         167,317,038   234,436,544    67,119,507   7 HPFS/NTFS
/dev/sdb6          88,576,000   163,995,647    75,419,648  83 Linux
/dev/sdb7         163,997,696   167,315,455     3,317,760  82 Linux swap / Solaris


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 62 MB, 62189568 bytes
16 heads, 32 sectors/track, 237 cylinders, total 121464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *             32       121,342       121,311   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8640DE8D40DE837B                       ntfs       Malcolm Disk                  
/dev/sda2: PTTYPE="dos" 
/dev/sda5        62107DE0E8B26AFF                       ntfs       MBM Work                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        38A0B7E4A0B7A6B2                       ntfs       Old Disk                      
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        F28F7D3B2C2D9292                       ntfs       Old Space                     
/dev/sdb6        fdfe341d-ddb0-465e-8c26-10b7d3676b0c   ext4                                     
/dev/sdb7        155cc143-9d70-45cb-9a99-0467270e6af6   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdg1        1075-C19F                              vfat       64M TRAVEL                    
/dev/sdg: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb6        /media/fdfe341d-ddb0-465e-8c26-10b7d3676b0c ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdg1        /media/64M TRAVEL        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb1        /media/Old Disk          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect











=========================== sdb6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set fdfe341d-ddb0-465e-8c26-10b7d3676b0c
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
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set fdfe341d-ddb0-465e-8c26-10b7d3676b0c
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set fdfe341d-ddb0-465e-8c26-10b7d3676b0c
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=fdfe341d-ddb0-465e-8c26-10b7d3676b0c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set fdfe341d-ddb0-465e-8c26-10b7d3676b0c
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=fdfe341d-ddb0-465e-8c26-10b7d3676b0c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set fdfe341d-ddb0-465e-8c26-10b7d3676b0c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set fdfe341d-ddb0-465e-8c26-10b7d3676b0c
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 8640de8d40de837b
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=fdfe341d-ddb0-465e-8c26-10b7d3676b0c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=155cc143-9d70-45cb-9a99-0467270e6af6 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


  58.3GB: boot/grub/core.img
  50.5GB: boot/grub/grub.cfg
  58.3GB: boot/initrd.img-2.6.32-21-generic
  58.3GB: boot/vmlinuz-2.6.32-21-generic
  58.3GB: initrd.img
  58.3GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
[/COLOR][/FONT]

---

### Post by oldfred on 2010-08-25
I do not see any gpt partitions.

It looks like the drives were originally reversed when Ubuntu was installed but since it will use UUIDs it still should boot. 

Have you in BIOS or using f12 (or whatever key is one time boot select drive) to boot sdb, the 120GB Ubuntu drive first and see if its boots Ubuntu? It looks like it should. After booting run this to update grub.cfg with correct partition numbers.

```
sudo update-grub
```

---

### Post by srs5694 on 2010-08-26
I agree with oldfred. Both /dev/sda and /dev/sdb are clearly MBR disks, not GPT disks -- there's no such thing as an extended partition for GPT, but both disks have extended partitions. The output indicates, if I'm interpreting it correctly, that you've got a Windows boot loader installed in the MBR of /dev/sda and GRUB 2 installed in the MBR of /dev/sdb. If your system is configured to boot /dev/sda by default, that means that GRUB 2 will never run. Changing this in the BIOS so that /dev/sdb boots by default is probably the easiest way to proceed. Alternatively, you could try swapping the cable connections, so that you plug /dev/sda into the motherboard socket currently used by /dev/sdb and vice-versa.

---

### Post by M_Mynaardt on 2010-08-26
> **srs5694 said:**
> GPT is definitely not a Microsoft plot; it was created by Intel as part of its Extensible Firmware Interface (EFI) specification. In fact, XP doesn't support GPT on BIOS-based systems; only a few fairly exotic EFI-based systems. Even Vista and Windows 7 won't boot from a GPT disk except on an EFI-based computer. Either you've got such a computer or you accidentally converted the disk from the more common MBR format to GPT.

In terms of GPT support, Linux is far ahead of Windows; Linux can boot from GPT on either BIOS-based or EFI-based computers. The Linux kernel has had GPT support for longer than Windows has, too.

I guess I was getting a bit paranoid because this GPT thing is a bit annoying.  Oh well; if GPT works better with Linux, then ultimately it's a good thing once I get it working...

---

### Post by srs5694 on 2010-08-26
> **M_Mynaardt said:**
> I guess I was getting a bit paranoid because this GPT thing is a bit annoying.  Oh well; if GPT works better with Linux, then ultimately it's a good thing once I get it working...

Except that there's no trace of GPT on your system, based on the Boot Info Script output you posted. What made you think you had a GPT disk to begin with?

---

### Post by M_Mynaardt on 2010-08-27
> **srs5694 said:**
> Except that there's no trace of GPT on your system, based on the Boot Info Script output you posted. What made you think you had a GPT disk to begin with?

First off, I tried the advice of a computer-pro acquaintance of mine.  He too was at a loss as to why Ubuntu wouldn't boot on my computer.  One thing he suggested was to try to install Ubuntu all over again.

[COLOR="DarkRed"]**AND NOW IT WORKS!!  WOOO-HOOO!!**[/COLOR]

:oops:

As to why I thought I had a GPT disk on my desktop; that's what the XP help files on my computer indicated.  When I couldn't get the choice of Ubuntu or Windows, I looked at the XP help files on how to modify the BIOS and all I got was "this computer has [the new fangled] GUID Partition Table instead of BIOS."

I do have to admit I feel like a bit of putz for not having this trouble.  But I do appreciate the time everyone here took to answer my questions.  I'm not completely dim with computers, but I did learn a few things along the way in trying to get Ubuntu working on my desktop.

Thanks all!  ):P

The only thing I have left to figure out is how to get my USB wireless receiver to work with Ubuntu on my desktop.  I'll check into that tomorrow.

Thanks again, everyone, for taking time out to give me advice!

---

