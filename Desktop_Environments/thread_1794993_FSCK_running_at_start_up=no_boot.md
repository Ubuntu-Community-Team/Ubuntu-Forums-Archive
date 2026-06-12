---
title: "FSCK running at start up=no boot"
date: 2011-07-01
forum: Desktop Environments
---

### Post by Geezanansa on 2011-07-01
Hi all

Just asking for some pointers on how to get my system booting, as it aint... reliably.

Just a noob so hope terminology close enough...

After powering up system i get post screen then ubuntu starts booting to splash screen then i get a screen with  fsck from util-linux-ng 2.17.2 and a lot of other txt.  Problem used to eventualy boot but I am finding more and more difficult to boot (freezes at fsck txt screen)
Had been using ctrl+alt+del to restart now use alt+sysreq+r/e/i/s/u/b

How do i configure or stop fsck?
How do i perform a hdd and file check?


Thanks in advance folks.

---

### Post by Rubi1200 on 2011-07-02
Hi,
post the specifications for the computer and, if possible, the following information:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Geezanansa on 2011-07-02
Thx Rubi1200

> Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any  changes." Once the desktop loads come back here and do the following:
I only recently (c. April 2011) installed !0.10 from cd and only last week upgraded to 11.04 (not from cd but online) 
I tried cd i have any way but just wants to install 10.10 with an option of upgrading to 11.04 
so i go and make up an 11.04 live cd....

Using StartUp-Manager I unchecked the show text and the other option in  the msc settings.  My system now simply freezes on ubuntu splash screen  when trying to boot

Using shift key to access recovery options and selecting 11.04 recovery option I have used options to determine it is a graphics/ x config prob.  ie when i choose load into failsafe x option there is a problem and asks me to reconfigure x config...After doing this system did boot into ubuntu but ubuntu now says i do not have the hardware to run unity so running in classic mode.  Not had that before unity was running previously.

.Just trying to give more info.

I get working on following your instructions Rubi1200.

---

### Post by Geezanansa on 2011-07-02
OK Rubi1200 here is the info you requested
I am running a vapochill unit cooloing an amd sempron 3500+cpu, 2GB DDR, 120GB IDE HDD, SATA DVD ODD, IDE DVD ODD, FDD,  100 LAN PCI CARD which is all plugged into an asrock alivenf6g-vsta mobo which has NVIDIA® GeForce 6100 / nForce 430 or GeForce 6150SE / nForce 430 Chipsets(not sure which is on my board info from manufacturers website)



 [CODE                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   230,277,119   230,275,072  83 Linux
/dev/sda2         230,279,166   240,119,807     9,840,642   5 Extended
/dev/sda5         230,279,168   240,119,807     9,840,640  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        a46aefda-0eb9-4861-8181-31943338816b   ext4       
/dev/sda5        87790257-b0e0-4b7c-99a2-8aa78f2bbcf1   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root a46aefda-0eb9-4861-8181-31943338816b
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root a46aefda-0eb9-4861-8181-31943338816b
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root a46aefda-0eb9-4861-8181-31943338816b
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=a46aefda-0eb9-4861-8181-31943338816b ro  quiet vga=788  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root a46aefda-0eb9-4861-8181-31943338816b
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=a46aefda-0eb9-4861-8181-31943338816b ro single  quiet vga=788
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root a46aefda-0eb9-4861-8181-31943338816b
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=a46aefda-0eb9-4861-8181-31943338816b ro  quiet vga=788  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root a46aefda-0eb9-4861-8181-31943338816b
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=a46aefda-0eb9-4861-8181-31943338816b ro single  quiet vga=788
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root a46aefda-0eb9-4861-8181-31943338816b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root a46aefda-0eb9-4861-8181-31943338816b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=87790257-b0e0-4b7c-99a2-8aa78f2bbcf1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  94.131374359 = 101.072793600  boot/grub/core.img                             1
  52.692394257 = 56.578027520   boot/grub/grub.cfg                             1
  40.844726562 = 43.856691200   boot/initrd.img-2.6.35-28-generic              2
  41.110351562 = 44.141903872   boot/initrd.img-2.6.38-8-generic               2
  94.261249542 = 101.212246016  boot/vmlinuz-2.6.35-28-generic                 1
  40.141910553 = 43.102048256   boot/vmlinuz-2.6.38-8-generic                  1
  41.110351562 = 44.141903872   initrd.img                                     2
  40.844726562 = 43.856691200   initrd.img.old                                 2
  40.141910553 = 43.102048256   vmlinuz                                        1
  94.261249542 = 101.212246016  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error][/CODE]

---

### Post by Geezanansa on 2011-07-02
After removing live cd and restarting my system did boot to log in screen; logged in fine but no unity.....:(
Will try changing startup-manager msc/txt setting and restart to see if fsck still trying to run...

---

### Post by Geezanansa on 2011-07-02
Just confirming the fsck thing apparently aint happening as i get straight from splash to log in screen.

After logging in to ubuntu i have the classic desktop no unity.  Searching forums.  Help would be welcomed.

---

### Post by Rubi1200 on 2011-07-02
A quick glance at the script results does not suggest anything unusual.

I think this is a hardware, most likely graphics, issue.

The message you posted before about Unity not able to run probably means your graphic card is not supported for Unity.

Here are some links that may help you track this down:
[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)
[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)

If Unity-3D does not work, you can consider Unity-2D (available in the repositories) as an alternative to the Classic desktop.

You can also try booting with nomodeset and then checking for drivers for your card to see if that helps:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

### Post by Geezanansa on 2011-07-02
Thx for links to further reading it appears my onboard gpu is down on dedicated ram for running unity.
Maybe this is/was prob with booting!  x config
So everything has now reconfigured and reliably booting.  So just to try and understand what I have done is when i booted from live cd x config was updated and saved so that at next normal boot system uses new x config???


I have not changed my hardware using on board gpu only.  Unity was working but possibly cause of boot probs...
nomodeset looks relevant and promising!

Thx again Rubi1200.  Your input is much appreciated.

---

### Post by Geezanansa on 2011-07-02
> You can also try booting with nomodeset and then checking for drivers for your card to see if that helps:
[http://ubuntuforums.org/showpost.php...97&postcount=1]("http://ubuntuforums.org/showpost.php?p=10069997&postcount=1")If the nomodeset command is used in the grub screen ie hold shift at boot after post to load grub and press  c for command screen.

That command is not recognised in the grub used by natty it works on lucid though apparently... or...

How do i boot using nomodeset?

I am posting with a unity desktop though I post in MG&TL thread  "unity not there" on how i did this as after trying live cd thing again(after boot probs again-cos i changed nvidia settings!) it detected xorg and apper problems.

---

