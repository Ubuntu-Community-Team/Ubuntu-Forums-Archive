---
title: "Bootloader for Windows lost"
date: 2013-08-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by antros48 on 2013-08-29
Hi everyone
I tried to install ubuntu 13.04 x86 on my 16 GB flash drive using the pendrive program. When i restarted my laptop and selected boot from usb drive i then selected install ubuntu on my dva2 using ext4 and "/" on mount. After finishing the process i restarted my laptop and i was keep booting in ubuntu os without even asking me if i wanted to boot in windows. I then removed usb from laptop and the only os that exists is ubuntu. The only thing i noticed is that in the partitioning menu earlier where i selected the 16 GB flash drive, it also said Windows 8 loader next to it something that was a bit strange since my windows was installed on my 240 Gb ssd. I enter in ubuntu without usb and i can see all my files from windows desktop. Is there any possible way to recover my windows???
College is opening next week and i could really use some help..
Thanks a lot!

---

### Post by lukeiamyourfather on 2013-08-29
Try reconfiguring GRUB to see Windows, usually this command can find a Windows install and configure it automatically.

```
sudo update-grub
```

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by oldfred on 2013-08-29
If lukeiamyourfather suggestion does not work, we will need lots of details.

If you had Windows 8, it is UEFI, but you can install Ubuntu in either UEFI boot mode or BIOS boot mode and from BIOS boot mode you cannot boot Windows. Boot-Repair can convert install if needed.
But if you go back into UEFI, you then should be able to boot Windows from UEFI mode not CSM/BIOS/Legacy mode.

Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by antros48 on 2013-08-29
[[COLOR=#000000]lukeiamyourfather[/COLOR]]("http://ubuntuforums.org/member.php?u=774656")[COLOR=#000000]  Thank you for your respond. Unfortunately i tried this code and it didn't work... I tried all of the options in boot-repair menu but still nothing happened. I cannot boot windows 8 at all, i don't even have the choice to do. 
Oldfred thank you for the response also. For now the only info i can provide you is the text file that contains the results of the boot-repair procedure. I am at work and i hope later i can give you all the appropriate info.. Hope you can help me!

[/COLOR]```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 28Aug2013]



============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM


sda2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda2 and looks at sector 18604176 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Operating System:  Ubuntu 13.04 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img


sda3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8
    Boot files:        /Windows/System32/winload.exe /wubildr /wubildr.mbr


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1                  63       208,844       208,782  de Dell Utility
/dev/sda2             208,896    30,928,895    30,720,000  83 Linux
/dev/sda3    *     30,928,896   500,112,830   469,183,935   7 NTFS / exFAT / HPFS




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/sda1        3030-3030                              vfat       DellUtility
/dev/sda2        0ec7f866-6d0a-445c-8b27-4d89bc80b24a   ext4       
/dev/sda3        0876FF6276FF4F46                       ntfs       


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/sda2        /                        ext4       (rw,errors=remount-ro)




=========================== sda2/boot/grub/grub.cfg: ===========================


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


if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi


export menuentry_id_option


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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}


if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  0ec7f866-6d0a-445c-8b27-4d89bc80b24a
else
  search --no-floppy --fs-uuid --set=root 0ec7f866-6d0a-445c-8b27-4d89bc80b24a
fi
    font="/usr/share/grub/unicode.pf2"
fi


if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
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
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-0ec7f866-6d0a-445c-8b27-4d89bc80b24a' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  0ec7f866-6d0a-445c-8b27-4d89bc80b24a
    else
      search --no-floppy --fs-uuid --set=root 0ec7f866-6d0a-445c-8b27-4d89bc80b24a
    fi
    linux    /boot/vmlinuz-3.8.0-29-generic root=UUID=0ec7f866-6d0a-445c-8b27-4d89bc80b24a ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-29-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-0ec7f866-6d0a-445c-8b27-4d89bc80b24a' {
    menuentry 'Ubuntu, with Linux 3.8.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-29-generic-advanced-0ec7f866-6d0a-445c-8b27-4d89bc80b24a' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  0ec7f866-6d0a-445c-8b27-4d89bc80b24a
        else
          search --no-floppy --fs-uuid --set=root 0ec7f866-6d0a-445c-8b27-4d89bc80b24a
        fi
        echo    'Loading Linux 3.8.0-29-generic ...'
        linux    /boot/vmlinuz-3.8.0-29-generic root=UUID=0ec7f866-6d0a-445c-8b27-4d89bc80b24a ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-29-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-29-generic-recovery-0ec7f866-6d0a-445c-8b27-4d89bc80b24a' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  0ec7f866-6d0a-445c-8b27-4d89bc80b24a
        else
          search --no-floppy --fs-uuid --set=root 0ec7f866-6d0a-445c-8b27-4d89bc80b24a
        fi
        echo    'Loading Linux 3.8.0-29-generic ...'
        linux    /boot/vmlinuz-3.8.0-29-generic root=UUID=0ec7f866-6d0a-445c-8b27-4d89bc80b24a ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-29-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-advanced-0ec7f866-6d0a-445c-8b27-4d89bc80b24a' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  0ec7f866-6d0a-445c-8b27-4d89bc80b24a
        else
          search --no-floppy --fs-uuid --set=root 0ec7f866-6d0a-445c-8b27-4d89bc80b24a
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=0ec7f866-6d0a-445c-8b27-4d89bc80b24a ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-recovery-0ec7f866-6d0a-445c-8b27-4d89bc80b24a' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  0ec7f866-6d0a-445c-8b27-4d89bc80b24a
        else
          search --no-floppy --fs-uuid --set=root 0ec7f866-6d0a-445c-8b27-4d89bc80b24a
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=0ec7f866-6d0a-445c-8b27-4d89bc80b24a ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-19-generic
    }
}


### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###


### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  0ec7f866-6d0a-445c-8b27-4d89bc80b24a
    else
      search --no-floppy --fs-uuid --set=root 0ec7f866-6d0a-445c-8b27-4d89bc80b24a
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  0ec7f866-6d0a-445c-8b27-4d89bc80b24a
    else
      search --no-floppy --fs-uuid --set=root 0ec7f866-6d0a-445c-8b27-4d89bc80b24a
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###


### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------


=============================== sda2/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=0ec7f866-6d0a-445c-8b27-4d89bc80b24a /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------


=================== sda2: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


  12.322250366 = 13.230915584   boot/grub/grub.cfg                             1
   8.884895325 = 9.540083712    boot/grub/i386-pc/core.img                     1
   0.956172943 = 1.026682880    boot/vmlinuz-3.8.0-19-generic                  1
   1.385864258 = 1.488060416    boot/vmlinuz-3.8.0-29-generic                  1
   0.956172943 = 1.026682880    vmlinuz                                        1
   1.612644196 = 1.731563520    boot/initrd.img-3.8.0-19-generic               3
   1.653625488 = 1.775566848    boot/initrd.img-3.8.0-29-generic               1
   1.612644196 = 1.731563520    initrd.img                                     3
   1.653625488 = 1.775566848    initrd.img.old                                 1


=============================== StdErr Messages: ===============================


cat: write error: Broken pipe


ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-08-29__18h28 ===================
boot-repair version : 3.199~ppa24~raring
boot-sav version : 3.199~ppa24~raring
glade2script version : 3.2.2~ppa45~raring
boot-sav-extra version : 3.199~ppa24~raring
boot-repair is executed in installed-session (Ubuntu 13.04, raring, Ubuntu, i686)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=0ec7f866-6d0a-445c-8b27-4d89bc80b24a ro quiet splash vt.handoff=7


=================== os-prober:
/dev/sda2:The OS now in use - Ubuntu 13.04 CurrentSession:linux


=================== blkid:
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat"
/dev/sda2: UUID="0ec7f866-6d0a-445c-8b27-4d89bc80b24a" TYPE="ext4"
/dev/sda3: UUID="0876FF6276FF4F46" TYPE="ntfs"




1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.


Windows not detected by os-prober on sda3.


=================== /etc/grub.d/ :
drwxr-xr-x  2 root root     4096 &#913;&#960;&#961;  24 20:06 grub.d
total 72
-rwxr-xr-x 1 root root  7541 &#913;&#960;&#961;   9 12:28 00_header
-rwxr-xr-x 1 root root  5974 &#913;&#960;&#961;   9 11:53 05_debian_theme
-rwxr-xr-x 1 root root 11381 &#913;&#960;&#961;   9 12:28 10_linux
-rwxr-xr-x 1 root root 10258 &#913;&#960;&#961;   9 12:28 20_linux_xen
-rwxr-xr-x 1 root root  1688 &#916;&#949;&#954;   5  2012 20_memtest86+
-rwxr-xr-x 1 root root 10976 &#913;&#960;&#961;   9 12:28 30_os-prober
-rwxr-xr-x 1 root root  1426 &#913;&#960;&#961;   9 12:28 30_uefi-firmware
-rwxr-xr-x 1 root root   214 &#913;&#960;&#961;   9 12:28 40_custom
-rwxr-xr-x 1 root root   216 &#913;&#960;&#961;   9 12:28 41_custom
-rw-r--r-- 1 root root   483 &#913;&#960;&#961;   9 12:28 README








=================== /etc/default/grub :


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"






=================== UEFI/Legacy mode:
This installed-session is not EFI-compatible.
EFI in dmesg.
[    0.000000] ACPI: UEFI bafe7000 0003E (v01 DELL    QA09    00000002 PTL  00000002)
[    0.000000] ACPI: UEFI bafe6000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: UEFI bafe5000 0026A (v01 DELL    QA09    00000002 PTL  00000002)
SecureBoot disabled.




=================== PARTITIONS & DISKS:
sda2    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    .
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda3.


sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    63 sectors * 512 bytes




=================== parted -l:


Model: ATA SAMSUNG SSD PM81 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
1      32.3kB  107MB   107MB   primary  fat16        diag
2      107MB   15.8GB  15.7GB  primary  ext4
3      15.8GB  256GB   240GB   primary  ntfs         boot


=================== parted -lm:


BYT;
/dev/sda:256GB:scsi:512:512:msdos:ATA SAMSUNG SSD PM81;
1:32.3kB:107MB:107MB:fat16::diag;
2:107MB:15.8GB:15.7GB:ext4::;
3:15.8GB:256GB:240GB:ntfs::boot;




=================== mount:
/dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/antros/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=antros)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)




=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fb1 fd full fuse hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uinput urandom v4l vga_arbiter vhost-net video0 zero
ls /dev/mapper:  control


=================== hexdump -n512 -C /dev/sda1
00000000  eb 54 90 44 65 6c 6c 20  38 2e 30 00 02 04 01 00  |.T.Dell 8.0.....|
00000010  02 00 02 00 00 f8 cc 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  8d 2f 03 00 80 00 29 30  30 30 30 44 65 6c 6c 55  |./....)0000DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 10 00  |tilityFAT16   ..|
00000040  01 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 33 c0  8e d0 bc 00 07 fc b9 80  |......3.........|
00000060  00 8e d8 be 00 7c b8 00  20 8e c0 33 ff f3 66 a5  |.....|.. ..3..f.|
00000070  ea 75 00 00 20 8e d8 be  cc 01 b8 01 02 b9 01 00  |.u.. ...........|
00000080  b6 00 8a 16 24 00 bb 00  02 cd 13 0f 82 0c 01 80  |....$...........|
00000090  3e c2 03 06 74 0e c6 06  c2 03 06 b8 01 03 cd 13  |>...t...........|
000000a0  0f 82 f7 00 66 0f b7 06  0e 00 66 03 06 1c 00 66  |....f.....f....f|
000000b0  0f b7 0e 16 00 66 d1 e1  66 03 c1 66 a3 46 00 66  |.....f..f..f.F.f|
000000c0  0f b7 0e 11 00 89 0e 52  00 83 c1 0f c1 e9 04 88  |.......R........|
000000d0  0e 40 00 66 03 c1 66 a3  4e 00 b8 00 30 a3 44 00  |.@.f..f.N...0.D.|
000000e0  8e c0 e8 d4 00 33 db b9  0b 00 be e1 01 8b fb f3  |.....3..........|
000000f0  a6 74 0f 83 c3 20 ff 0e  52 00 75 eb be d7 01 e9  |.t... ..R.u.....|
00000100  99 00 26 8b 47 1a a3 54  00 a1 16 00 a3 52 00 66  |..&.G..T.....R.f|
00000110  0f b7 06 0e 00 66 03 06  1c 00 66 a3 46 00 a1 52  |.....f....f.F..R|
00000120  00 3d 40 00 76 02 b0 40  a2 40 00 e8 8b 00 66 0f  |.=@.v..@.@....f.|
00000130  b6 06 40 00 66 01 06 46  00 29 06 52 00 74 09 c1  |..@.f..F.).R.t..|
00000140  e0 05 01 06 44 00 eb d6  c7 06 44 00 70 00 a0 0d  |....D.....D.p...|
00000150  00 a2 40 00 66 0f b7 06  54 00 66 83 e8 02 66 0f  |..@.f...T.f...f.|
00000160  b6 0e 0d 00 66 f7 e1 66  03 06 4e 00 66 a3 46 00  |....f..f..N.f.F.|
00000170  e8 46 00 8b 36 54 00 b8  00 30 d1 e6 73 03 05 00  |.F..6T...0..s...|
00000180  10 8e c0 26 ad 3d f8 ff  73 16 a3 54 00 0f b6 06  |...&.=..s..T....|
00000190  0d 00 c1 e0 09 01 06 42  00 eb b9 e8 0d 00 eb fe  |.......B........|
000001a0  8a 16 24 00 33 ed ea 00  00 70 00 b4 0e ac bb 07  |..$.3....p......|
000001b0  00 cd 10 80 3c 00 75 f3  c3 b4 42 8a 16 24 00 be  |....<.u...B..$..|
000001c0  3e 00 cd 13 72 01 c3 be  cc 01 eb cf 44 69 73 6b  |>...r.......Disk|
000001d0  20 65 72 72 6f 72 00 4e  6f 20 6c 6f 61 64 65 72  | error.No loader|
000001e0  00 44 45 4c 4c 42 49 4f  20 42 49 4e 00 00 00 00  |.DELLBIO BIN....|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 f0 d7 01  |........?.......|
00000020  00 00 00 00 80 00 80 00  be 2d f7 1b 00 00 00 00  |.........-......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  46 4f ff 76 62 ff 76 08  |........FO.vb.v.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200


=================== df -Th:


Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda2      ext4       15G  3.3G   11G  24% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev           devtmpfs  3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs     799M  860K  798M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     3.9G  152K  3.9G   1% /run/shm
none           tmpfs     100M   20K  100M   1% /run/user
/dev/sda1      vfat      102M  9.1M   93M   9% /mnt/boot-sav/sda1
/dev/sda3      fuseblk   224G  122G  103G  55% /mnt/boot-sav/sda3


=================== fdisk -l:


Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x07f2837e


Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      208844      104391   de  Dell Utility
/dev/sda2          208896    30928895    15360000   83  Linux
/dev/sda3   *    30928896   500112830   234591967+   7  HPFS/NTFS/exFAT






=================== Recommended repair
Recommended-Repair
This setting will reinstall the grub2 of sda2 into the MBR of sda.
Additional repair will be performed: unhide-bootmenu-10s repair-filesystems  fix-windows-boot




Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var


fsck -fyM /dev/sda2
fsck from util-linux 2.20.1


fsck -fyM /dev/sda1
fsck from util-linux 2.20.1


ntfsfix /dev/sda3
Refusing to operate on read-write mounted device /dev/sda3.
Quantity of real Windows: 1
WinSE in sda3
/mnt/boot-sav/sda3/ may need repair.
/mnt/boot-sav/sda3/bootmgr may need repair.
grub-install (GRUB) 2.00-13ubuntu3,grub-install (GRUB) 2.


Reinstall the GRUB of sda2 into the MBR of sda
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0


update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Found memtest86+ image: /boot/memtest86+.bin
Unhide GRUB boot menu in sda2/boot/grub/grub.cfg


Boot successfully repaired.


You can now reboot your computer.




A broken Wubi has been detected. Please fix it this way:
[https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu)

```

---

### Post by oldfred on 2013-08-29
Changed quote to code. Please use code for long text or terminal output. It is the # sign in the advanced editor.

Did you have another install of Windows in sda2. It looks like you install in sda3 is missing two of the three normal boot files which Windows 7 install installs into a boot partition or installs into the first install of Windows.

       Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

You are missing the first two files. You cannot repair from Linux but with a Windows repairCD or Flash drive you can run the repairs to add bootmgr and create a new BCD.

      
 How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

You also show an old install of wubi in the Windows partition. You should be able to uninstall that from inside Windows.

---

### Post by antros48 on 2013-09-01
Thanks for the response. It seems that i accidentally installed the ubuntu partition on a 15GB of my ssd where the windows loader was installed, instead on my 15BG flash disk. I think it was just sda i chose and not sda2 or 3.. I did the upgrade from windows 7 to 8 using the update tool and not with any cd or dvd so i do not have any repair discs. I downloaded the mini partition wizard and burned it on a dvd and i chose rebuild mbr but now my pc does not even boot and a message pops up saying BOOTMGR IS MISSING PRESS CTRL ALT DEL TO RESTART. &#913;ny thoughts?

---

### Post by oldfred on 2013-09-01
It is the bootmgr & BCD that are missing.

One user did just copy his bootmgr from his Windows repairCD and used bcdEdit to fix the BCD that the repairCD had.

I think Windows 8 has a backup of bootmgr somewhere in the system folders.
Someone posted that the UEFI version has that efi version of bootmgr in this location.
 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

Some then use EasyBCD to repair BCD.

 Windows 8 BCD 
[http://ubuntuforums.org/showthread.php?t=2110638](http://ubuntuforums.org/showthread.php?t=2110638)

If you have access to another system with the same 32bit or 64bit type any version you can make the repair flash drive.

---

### Post by antros48 on 2013-09-01
Ok i tried everything with a bootable usb stick that contained the windows 8 installation files since i didn't have the discs. With the command prompt i used all of the orders that bootrec provided. Nothing happened. Then i used the auto repair choice and again nothing changed. I repeated the above procedure and my laptop finally boot in windows 8! I do not know what changed in the second time but i had the result i wanted to!
Thank you all for the responses and i hope i helped someone with my procedure. Most important of all is lessons learned!

---

### Post by oldfred on 2013-09-01
Glad you got it working. :)

Often Windows needs to run the auto repairs 3 times. 
And you have to run chkdsk until there are no errors or often more than once as it does not always fix everything on one pass.

---

