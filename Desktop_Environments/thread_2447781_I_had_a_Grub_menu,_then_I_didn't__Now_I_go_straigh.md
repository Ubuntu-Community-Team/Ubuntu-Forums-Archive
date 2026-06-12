---
title: "I had a Grub menu, then I didn't:  Now I go straight to login"
date: 2020-07-25
forum: Desktop Environments
---

### Post by watchpocket on 2020-07-25
In a desktop workstation, I have a 1-terabyte Western Digital SSD containing Ubuntu-MATE 18.04.4. 

It boots in BIOS mode and uses MBR partitioning, and has one large 998 GB partition at /dev/sda1.  Ext4 file system. I use a swap file, with no swap partition.

I also have in the box, for storage only, a non-booting 960 GB Sandisk SSD.  

When I set 18.04 up a few months ago, it had a functioning, visible Grub menu. But somewhere along the line in the last month or two, *** the Grub menu disappeared - it does not display when I boot up. ***Now I boot, then wait almost a full minute, then the login window appears.
 
(I set up this 18.04 after removing all three of [COLOR=#8b4513]*(a)*[/COLOR] a separate SSD containing Ubuntu-MATE  16.04;* [COLOR=#8b4513](b)[/COLOR]* an old spinner HD that contained MATE 14.04;  and [COLOR=#8b4513]*(c)*[/COLOR] another spinner  that was used for storage)

Installed on my system are:
 
grub-common 2.02-2ubuntu8.15,   **  <--**
grub2-common 2.02-2ubuntu8.15,   ***<-- should I have both of these installed?  Should I remove grub-common & keep grub2-common?***
grub-pc 2.02-2ubuntu8.15,
 grub-pc-bin 2.02-2ubuntu8.15, and 
grub-gfxpayload-lists 0.7.


I'm trying to get ready to:

 [COLOR=#800000]*(a)*[/COLOR] remove the SSD with the old BIOS 18.04 install;  then
[COLOR=#8b4513]*(b)*[/COLOR] install, on separate SSD drives, Ubuntu-MATE 20.04 and 18.04 in UEFI mode  with GPT partitioning;
 ***but I want to solve this current grub issue first.***  Thanks for any tips.

Some info:
```
--> [COLOR=#0000ff]uname -a [/COLOR] 
Linux rjbox 5.4.0-42-generic #46~18.04.1-Ubuntu SMP Fri Jul 10 07:21:24 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux


--> [COLOR=#0000ff]lsb_release -a [/COLOR]
LSB Version:    core-9.20170808ubuntu1-noarch:security-9.20170808ubuntu1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic


--> [COLOR=#0000ff]ls -la /  [/COLOR]
total 2097268
      4 drwxr-xr-x  25 root root       4096 Jul 22 00:59 ./
      4 drwxr-xr-x  25 root root       4096 Jul 22 00:59 ../
      4 drwxr-xr-x   2 root root       4096 May 25 13:05 bin/
      4 drwxr-xr-x   3 root root       4096 Jul 22 01:10 boot/
      4 drwxr-xr-x   2 root root       4096 Mar 27 21:39 cdrom/
      0 drwxr-xr-x  21 root root       4880 Jul 25 20:30 dev/
     12 drwxr-xr-x 178 root root      12288 Jul 24 22:28 etc/
      4 drwxr-xr-x   3 root root       4096 Mar 27 21:40 home/
      0 lrwxrwxrwx   1 root root         32 Jul 22 00:59 initrd.img -> boot/initrd.img-5.4.0-42-generic
      0 lrwxrwxrwx   1 root root         32 Jul 22 00:59 initrd.img.old -> boot/initrd.img-5.3.0-62-generic
      4 drwxr-xr-x  23 root root       4096 Jul  6 15:30 lib/
      4 drwxr-xr-x   2 root root       4096 Jul  6 15:30 lib64/
     16 drwx------   2 root root      16384 Mar 27 21:33 lost+found/
      4 drwxr-xr-x   3 root root       4096 Apr  5 21:05 media/
      4 drwxr-xr-x   3 root root       4096 May 18 00:19 mnt/
      4 drwxr-xr-x   9 root root       4096 May 10 22:31 opt/
      0 dr-xr-xr-x 265 root root          0 Jul 25 11:38 proc/
      4 drwx------  13 root root       4096 Jun  4 22:25 root/
      0 drwxr-xr-x  37 root root       1200 Jul 25 20:30 run/
     12 drwxr-xr-x   2 root root      12288 Jul  6 15:30 sbin/
      4 drwxr-xr-x  14 root root       4096 May 21 02:03 snap/
      4 drwxr-xr-x   2 root root       4096 Feb  3 13:22 srv/
2097156 -rw-------   1 root root 2147483648 Mar 27 21:35 swapfile
      0 dr-xr-xr-x  13 root root          0 Jul 25 11:38 sys/
      4 drwxr-xr-x   9 root root       4096 Jul 21 16:01 timeshift/
      4 drwxrwxrwt  21 root root       4096 Jul 25 20:48 tmp/
      4 drwxr-xr-x  10 root root       4096 Feb  3 13:22 usr/
      4 drwxr-xr-x  14 root root       4096 Feb  3 13:36 var/
      0 lrwxrwxrwx   1 root root         29 Jul 22 00:59 vmlinuz -> boot/vmlinuz-5.4.0-42-generic
      0 lrwxrwxrwx   1 root root         29 Jul 22 00:59 vmlinuz.old -> boot/vmlinuz-5.3.0-62-generic


--> [COLOR=#0000ff]ls -la /boot [/COLOR]
total 173888
    4 drwxr-xr-x  3 root root     4096 Jul 22 01:10 ./
    4 drwxr-xr-x 25 root root     4096 Jul 22 00:59 ../
 4388 -rw-------  1 root root  4490843 Jun 24 08:07 System.map-5.3.0-62-generic
 4468 -rw-------  1 root root  4573787 Jul 10 02:54 System.map-5.4.0-42-generic
  232 -rw-r--r--  1 root root   235827 Jun 24 08:07 config-5.3.0-62-generic
  236 -rw-r--r--  1 root root   237786 Jul 10 02:54 config-5.4.0-42-generic
    4 drwxr-xr-x  5 root root     4096 Jul 22 01:08 grub/
73080 -rw-r--r--  1 root root 74833744 Jul  8 16:11 initrd.img-5.3.0-62-generic
72820 -rw-r--r--  1 root root 74561600 Jul 22 00:59 initrd.img-5.4.0-42-generic
  180 -rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
  184 -rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
  184 -rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
 8948 -rw-------  1 root root  9158912 Jun 24 08:20 vmlinuz-5.3.0-62-generic
 9156 -rw-------  1 root root  9371904 Jul 10 02:56 vmlinuz-5.4.0-42-generic


--> [COLOR=#0000ff]ls -la /boot/grub [/COLOR] 
total 2392
   4 drwxr-xr-x 5 root root    4096 Jul 22 01:08 ./
   4 drwxr-xr-x 3 root root    4096 Jul 22 01:10 ../
   4 drwxr-xr-x 2 root root    4096 Mar 27 21:41 fonts/
   4 -rw------- 1 root root     712 May 15 21:52 gfxblacklist.txt
  12 -r--r--r-- 1 root root    9605 Jul 22 01:08 grub.cfg
   4 -rw-r--r-- 1 root root    1024 Jul 25 11:38 grubenv
  12 drwxr-xr-x 2 root root   12288 Mar 27 21:45 i386-pc/
   4 drwxr-xr-x 2 root root    4096 Mar 27 21:45 locale/
2344 -rw-r--r-- 1 root root 2397557 Mar 27 21:45 unicode.pf2


--> [COLOR=#0000ff]cat /etc/default/grub [/COLOR]
#   If you change this file, run 'update-grub' afterwards to update /boot/grub/grub.cfg.
#   For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="video=VGA-1:640x480"

# GRUB_GFXMODE=1024x640
# GRUB_GFXPAYLOAD=1024x640
# GRUB_GFXPAYLOAD_LINUX=keep


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
# GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
# GRUB_TERMINAL=console

# The resolution used on graphical terminal:
# Note that you can use only modes which your graphic card supports via VBE.
# You can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
# GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
# GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
# GRUB_INIT_TUNE="480 440 1"



.

```

---

### Post by oldfred on 2020-07-25
If you have only one install, then grub menu does not normally show.
It is when you have multiple installs that menu shows by default.
With BIOS you can hold shift key from BIOS screen until menu appears.
With UEFI it will be press escape key (possibly more than once) near end of UEFI/BIOS screen.

With 18.04 or later to always see menu
#GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT_STYLE=menu

For info on UEFI install, see link below in my signature.
Last install will be the one in charge & its grub will be the one used. But major grub update may reset another install to be the default.

---

### Post by ActionParsnip on 2020-07-26
If you hold SHIFT at boot, does it help?

---

### Post by watchpocket on 2020-07-26
@oldfred:  Thank you very much for responding.  About my installation of both  grub-common and grub2-common, I have a feeling that the presence of  grub-common is extraneous and unnecessary, since I also have *grub2-common* installed.  Can you (or anyone) confirm this?

(I didn't realize I had both installed until I prepared to make the post above.) 				


@ActionParsnip:  Yes!  Thank you.  Holding the <SHIFT> key does indeed cause the Grub menu to display.  (Actually, right now I don't want it to display, I just wanted  to understand why it wasn't displaying.)

---

### Post by watchpocket on 2020-07-26
One other question:  I recently successfully installed a UEFI-booting  Ubuntu-MATE 18.04 on a standalone SSD ( which booted via USB), using a  GPT partition table. 

I did  checks to make sure it was in fact booting UEFI with a separate FAT-32 partition and with GPT.  

I made the boot partition (the FAT32 partition) with both the boot flag and the esp flag  in gparted.

**After  not plugging this drive in for a few weeks, I noticed that it was no  longer bootable, and that the /sys/firmware/efi directory was  mysteriously no longer there.**  All I have now is an empty  /sys/ dir for that SSD.  

This struck me as very strange, and I don't know what could have caused it.  I never just deleted these directories. 

It's  not a big deal because it wasn't a working drive, and I'm about to  re-install a UEFI/GPT again with the 18.04 installer, but it seemed odd.

I  want to have the (currently standalone) UEFI/GPT 18.04 and a 20.04  drive inside in my desktop box for dual-boot.  I know that they *** both *** have to be UEFI/GPT.

[***UPDATE:***  Actually, I think I know what may have caused this: It may have to do with the fact that after installation, I got a warning from fdisk saying that the backup sectors were misaligned, something along that line, can't remember exactly.]

---

### Post by oldfred on 2020-07-27
Normal UEFI install to an external drive with Ubuntu's Ubquity installs grub2's efi boot files into first drive's ESP - efi system partition. Usually that is the internal Windows drive's ESP.

You then have to reinstall grub manually or with Boot-Repair and maybe change mount of ESP in fstab to external drive's ESP, so grub updates are to correct ESP.

This is a very old bug that they now say is important, but are not working on. Please add to it.
Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Most now suggest unplugging internal drive either physically or logically in UEFI. Some have posted that after boot of installer, removing boot/esp flags from internal drive's ESP before install, works. Just be sure to restore that before rebooting while still in live installer. I have not had that work and always open terminal in middle of install at user & password screen, and check mounts to see which ESP is used.


If you can boot external install you can do a total reinstall of grub selecting the correct ESP.
Or most find it easier to use Boot-Repair & its advanced options to choose install & where to install boot  loader.

It is only Ubuntu's Ubiquity installer that seems to have issue. Have tried several other distributions and they let me select which drive/ESP to use.

---

### Post by watchpocket on 2020-08-15
I'm about to install Ubuntu-MATE 20.04.1 (UEFI) from a live USB flash drive onto an external SSD. (This SSD will later be placed internally.)

For me the problem of where the efi boot files get put should be easily solved - I'll just unplug my desktop tower's current internal (BIOS) 18.04 drive and also unplug my internal non-booting storage drive.  Can't see how I'd run into any problems with boot files by doing this.

---

