---
title: "Fixing vista mbr...no vista cd"
date: 2009-02-03
forum: General Help
---

### Post by Asacolips on 2009-02-03
I (in a move of extreme stupidity) removed my Vista mbr using the EasyBCD program.  I had freshly installed linux in an empty partition, and it surprisingly didn't install grub.  I assumed it was because of how I had used EasyBCD to repair the mbr before, and so I used it to try and reinstate grub be removing it.  Rather than doing something that made a little more sense such as using grub's commands from linux.  I did however select the backup option before doing so.

Too bad I can't access my partition from Ubuntu, due to a failed shutdown (though I don't recall any errors during shutdown).

Basically, I've been wracking my brain for about five hours now scouring the internet looking for ways to fix my mbr for vista.  Worst comes to worst, I have my single most important few files on a thumbdrive, but I still want that vista partition to work.  It would be a hassle to reinstall xp and then use my university's vista upgrade all over again.

So far, I've tried to use ms-sys, but I've had no luck there.  I can't get that via apt-get, and I can't build it from source, I'm getting some errors even though I had gotten build-essential prior.  After that I tried to use Super Grub via a dvd-rw, and that doesn't work.  Whenever I use it's fix mbr for xp option, I get the same message I had gotten before:

Error: Incorrect BOOT.INI
C:\windows\

(or something along the lines of that, I'm not looking at it now and can't be positive what it said).

What bugs me the most is that I'm sure I could get the backup in the right place if I could just open Vista's partition from linux, but it won't allow me to because of the failed unmount...

If anyone has any suggestions at all to help, it would be extremely appreciated.  I'm sure I can find some way to get things back to normal (either by trying to get my Windows 7 beta disk to work again or going through that lengthy xp/vista install/upgrade process) after next week.  But again, I would heavily prefer to have this work from my old vista setup.

Many thanks,

---

### Post by caljohnsmith on 2009-02-03
So do you want Grub on start up or the Vista boot manager instead? I think it would help to get a better picture of your setup first, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop (can be the Live CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Powerman2442 on 2009-02-03
Microsoft has released a Vista Recovery CD ISO since most manufacturers don't include OS CDs or DVDs with their computers. You can find the 32bit and 64-bi versions of the recovery CD ISO here. 

--> [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/) <--

It is a torrent file so you will need a program tat handles torrents. Once you download it you burn a CD image just like you would for a LiveCD. Reboot with the CD in and you should be able to use bootrec.exe to repair the Windows MBR and get access to your files within Windows Vista again. However, if you do this you WON'T be able to boot into Linux again until you install GRUB or another bootloader.

I had a similar problem but I had a Recovery CD from the manufacturer of my laptop (Gateway). Once you get loaded up into the Recovery CD you can use the information on this link to recover your Windows MBR. --> [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392) <--

Unless I have misunderstood something you have said all of this should work. I take it as there is no way to get back into your Windows partition and you want to fix the Windows MBR to get to it. Like I said, I had a similar problem and had to use the CD/DVD that came with my laptop to repair the MBR.

However, I'd suggest talking with some of the Linux Gurus on this forum before doing this particular step. They might be able to help you fix it differently without harming your current bootloader. I'm fairly new to Linux myself.

Good luck,

---

### Post by Asacolips on 2009-02-03
Thanks for the replies.  I'll try to get the script cal mentioned when I get back to my home pc, and run it.

Thanks for that info powerman, I'll try that tonight.  Basically what's happening is I can see vista from grub, but it seems it's booting into vista's boot so to speak.  If I try to boot Vista from grub I get the same message I would if I booted it by itself.

Again thanks for the suggestions, I'll try them when I get back to my house.

---

### Post by Powerman2442 on 2009-02-03
I think when you select Vista in the GRUB menu it loads up Vista's bootloader, that was there before the GRUB installation, from that point and the rest is all Windows. So I'd say something happened to the Windows MBR and even if you "fix" GRUB per say (reinstall it or whatever) it still won't work because when GRB loads Vista's bootloader it will just create he same problem. I'd say download and burn a recovery CD from that website and fix the MBR. You may have to install GRUB again afterwords, but then it should work fine.

Like I said I am fairly new to Linux but I am going on what I had to come up with without any help. It worked for me.

---

### Post by Asacolips on 2009-02-03
That's what I'm intending to do.  I'll definitely have to try fixing it in general, as Super Grub's fixing method placed xp's nt-based mbr on there. I'm attempting to download the recovery disk, but it's taking ages as I haven't been able to find a good mirror yet (no torrents from my machine so I'm getting nothing with that, and the only direct download I've found is rapidshare's limited free bandwidth).

Anyways, here's the output of that script.  Keep in mind that I tried to repair it with Super Grub last night, so it doesn't show as Vista:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda3 and 
                       looks at sector 518429871 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x12c912c9

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   481,275,269   481,275,207   7 HPFS/NTFS
/dev/sda2         481,275,270   482,319,494     1,044,225  82 Linux swap / Solaris
/dev/sda3         482,319,495   625,137,344   142,817,850  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="361C57401C56F9F7" TYPE="ntfs" 
/dev/sda2: TYPE="swap" UUID="d83c3b6a-c99b-476d-96ed-87ca8303667e" 
/dev/sda3: UUID="10291b0f-2c44-4e38-bdbc-bb8dc083331e" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/matt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=matt)

=========================== sda3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=10291b0f-2c44-4e38-bdbc-bb8dc083331e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=10291b0f-2c44-4e38-bdbc-bb8dc083331e ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=10291b0f-2c44-4e38-bdbc-bb8dc083331e ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=10291b0f-2c44-4e38-bdbc-bb8dc083331e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=d83c3b6a-c99b-476d-96ed-87ca8303667e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 265.4GB: boot/grub/menu.lst
 265.4GB: boot/grub/stage2
 265.4GB: boot/initrd.img-2.6.24-19-generic
 265.3GB: boot/vmlinuz-2.6.24-19-generic
 265.4GB: initrd.img
 265.3GB: vmlinuz

```

Also, grub is currently my bootloader, as I managed to get it back via ubuntu's live cd and using the grub commands.

**[EDIT] **I've been looking at microsoft's [page]("http://support.microsoft.com/kb/927392") on using the vista recovery disc.  I'm under the impression that I should attempt this in the order of /FixMbr, /FixBoot, and /RebuildBcd.  That's assuming that any of the options fail, I would move on to the next one.  Would that be correct or would I likely cause system damages by doing any of those?

---

### Post by caljohnsmith on 2009-02-03
Actually, there is no such thing as a Vista MBR or XP MBR; Microsoft uses the same MBR for both XP and Vista. The difference is in the partition boot sector: the XP partition boot sector boots "NTLDR" whereas the Vista boot sector boots "BOOTMGR". Right now your sda1 partition boot sector is an XP boot sector, so I think that is probably what you are referring to. It's strange because the script seems to think your sda1 partition has XP installed rather than Vista (although most of XP's and Vista's boot files are present), so to help clear up the confusion, how about posting the output of the following:
```
sudo mount /dev/sda1 /mnt && ls -l /mnt
```
And also, I would not recommend running "fixmbr" from a Windows CD unless you want to get rid of Grub; if you want to fix the Vista boot sector, you can run:
```
bootrec /fixboot
```
From the Vista CD.

---

### Post by Asacolips on 2009-02-03
I had thought it was essentially the same mbr, but I didn't know the terminology. Thanks for the clear up.

Anyways, here's the output:
```
total 4498540
drwxrwxrwx 1 root root       4096 2008-09-18 21:45 22833de09a1eb840abb50a
drwxrwxrwx 1 root root      32768 2008-08-23 18:13 ARENA
-rwxrwxrwx 1 root root         24 2006-09-18 17:43 AUTOEXEC.BAT
drwxrwxrwx 1 root root       4096 2008-11-05 22:08 $AVG8.VAULT$
drwxrwxrwx 1 root root      16384 2008-09-18 16:42 bcc0b3b4941f886893f3f56636
drwxrwxrwx 1 root root       8192 2009-02-03 01:57 Boot
-rwxrwxrwx 1 root root        355 2008-11-06 00:16 Boot.BAK
-rwxrwxrwx 2 root root        355 2008-11-06 02:30 Boot.ini.saved
-rwxrwxrwx 1 root root     377151 2008-12-13 02:03 bootmgr
-rwxrwxrwx 1 root root       8192 2009-01-28 00:34 BOOTSECT.BAK
-rwxrwxrwx 1 root root       3288 2009-01-29 23:34 bootsqm.dat
drwxrwxrwx 1 root root          0 2009-01-29 15:05 Config.Msi
-rwxrwxrwx 3 root root         10 2006-09-18 17:43 config.sys
drwxrwxrwx 1 root root       4096 2008-10-09 22:19 CPM
drwxrwxrwx 1 root root          0 2008-09-01 14:12 DECCHECK
drwxrwxrwx 1 root root          0 2006-11-02 08:02 Documents and Settings
-rwxrwxrwx 2 root root         18 2008-11-23 21:55 GO_NETWORK.LOG
-rwxrwxrwx 1 root root 2145857536 2009-02-02 18:14 hiberfil.sys
drwxrwxrwx 1 root root          0 2008-11-06 01:04 $INPLACE.~TR
-rwxrwxrwx 1 root root          0 2008-07-25 13:35 IO.SYS
-rwxrwxrwx 1 root root          0 2008-07-25 13:35 MSDOS.SYS
drwxrwxrwx 1 root root          0 2008-08-25 11:00 MSOCache
drwxrwxrwx 1 root root          0 2009-02-02 18:18 NST
-rwxrwxrwx 1 root root      47564 2008-04-14 08:00 NTDETECT.COM
-rwxrwxrwx 1 root root     250048 2008-04-14 08:00 ntldr
drwxrwxrwx 1 root root          0 2008-12-08 00:05 NVIDIA
-rwxrwxrwx 1 root root 2459770880 2009-02-02 18:14 pagefile.sys
drwxrwxrwx 1 root root          0 2009-01-30 13:11 PerfLogs
drwxrwxrwx 1 root root       8192 2009-01-30 12:40 ProgramData
drwxrwxrwx 1 root root      32768 2009-01-29 15:05 Program Files
drwxrwxrwx 1 root root       4096 2008-10-16 14:10 Python25
drwxrwxrwx 1 root root          0 2008-11-06 01:15 $Recycle.Bin
-rwxrwxrwx 1 root root        522 2008-07-25 13:54 RHDSetup.log
drwxrwxrwx 1 root root      16384 2009-02-02 22:44 System Volume Information
drwxrwxrwx 1 root root          0 2008-09-18 22:50 Temp
drwxrwxrwx 1 root root       4096 2008-11-06 00:58 Users
drwxrwxrwx 1 root root      40960 2009-02-03 02:00 Windows
drwxrwxrwx 1 root root          0 2008-11-06 02:24 $WINDOWS.~Q
```

I'll try fixboot first, but I'm not worried about removing grub at the moment.  I've learned the actual way to restore it (using root() and setup()) so that won't be a problem.  I'm also considering changing my ubuntu partition to linux mint if I can get vista working again, as I rather like it from what I saw on it's live cd.

Anyways, I'm about to attempt the repair (just finished the cd).

---

### Post by timcredible on 2009-02-03
you could try [super grub disk]("http://supergrubdisk.org").  i don't know if it works with vista or not

---

### Post by Asacolips on 2009-02-03
Super Grub did more damage for me than repairs.  However, I fixed it, using the Vista recovery cd powerman linked to.  Thanks a lot for the help guys, I would have probably formatted the entire disk if I couldn't have gotten it. I owe you!

---

### Post by Powerman2442 on 2009-02-03
> **Asacolips said:**
> Super Grub did more damage for me than repairs.  However, I fixed it, using the Vista recovery cd powerman linked to.  Thanks a lot for the help guys, I would have probably formatted the entire disk if I couldn't have gotten it. I owe you!

Did you end up having to reinstall GRUB then? I figured you were like me, Vista was my main OS and had all my important information on it. Had to use my recovery CD and bootrec to get Vista to boot again, just reinstalled GRUB later. Seemed like the easiest method at the time. Glad you got it working though.

---

### Post by Asacolips on 2009-02-04
Actually I didn't.  It went to grub, but now Vista's option works.  I may try to find a way to get Vista's mbr to work by itself again, in case I get rid of linux for whatever reason, but it's working fine for now.

---

