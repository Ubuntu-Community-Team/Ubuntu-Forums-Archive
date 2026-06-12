---
title: "No boot menu in Grub2, straight to rescue prompt"
date: 2010-07-06
forum: Desktop Environments
---

### Post by Man with Hat on 2010-07-06
Hi,

I have recently partitioned my hard drive to have both linux and win XP duel boot. I had linux installed first and followed a good guide on how to get winXP on there too. I ran into problems as the guide I was using was written for Grub not Grub 2.

I have been using [_this guide_]("http://ubuntuforums.org/showthread.php?t=1195275") and [_this one too_]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") to get a boot menu as I could only boot straight into Win XP. After using the first guide, I now boot straight to the rescue prompt. I followed it further and was able to boot into ubunu by typing several commands to manually load kernel etc. Once in Ubuntu, I updated my grub and computer still boots to rescue.

In the second guide, there is this section:

**[I]Grub shows rescue prompt (and does not continue to boot)**
You may have a buggy bios and the location of your /boot/* files is not under the 1024 cylinder boundary. Create a small partition on the beginning of the disk, mount it as /mnt/b, cp -av /boot/* /mnt/b; umount /mnt/b; mount /dev/small_partition /boot; grub-install /dev/<device>.
[/I]
Which is kinda gobble de gook to me. I seem to already have 2 small partitions already (I'm assuming one from Ubuntu install and one from WinXP install). Could I point something to one of these or something? And I am a little worried about playing around with partitions at the moment (plus I wouldn't have a clue how to do it in a terminal) as I don't want to accidentally delete data.

**I really just want an easy way to understand to get a boot menu to choose between Ubuntu and Win XP** Urgent help needed as I need docs/emails on both OS's ASAP

Please no one post a link to a wonderful guide that someone else wrote, just please tell me what I need to do ;) Appreciate any and all help!!!!!! Going to bed now as is very late but will check in morning. Thanks in advance

---

### Post by scott1541 on 2010-07-06
Watch this video and do what linux woman says [http://www.youtube.com/watch?v=WtBBl6HvdpM]("http://www.youtube.com/watch?v=WtBBl6HvdpM")

^^ Thinking about it this might not help you, but it's worth a try.

---

### Post by Man with Hat on 2010-07-06
Thanks for the reply :)

Only problem with that video is that I can't hear it! The reason I ended up putting windows back on in the first place is I got so fed up with trying for over a year to make my sound card work properly in Linux!! :)

---

### Post by Man with Hat on 2010-07-07
Not sure if anyone is checking this, but I am going to update it anyway so that hopefully it will be of use to another fellow noob who runs into the same problem :)

First let me say **_MAKE A LIVE CD BEFORE YOU DO ANYTHING_**, I have needed this thing like nothing else. It is the greatest contribution that Linux has made in my life this week!!

Next to summarise the guides (links are in my first post), if you need to boot from the rescue mode, then type these commands:

[B]insmod /boot/grub/linux.mod
linux /vmlinuz root=/dev/sda1 ro [/B][I][B]
initrd /initrd.img
boot[/B]

[/I][I]{note sda1 is my hard drive that I boot from, yours could be sda2,  sdb1 or something. If you are unsure, check the guide at part 15 for a  couple of extra steps to work out what yours is. Same goes for a Wubi user as there are different commands}

[/I]

---

### Post by Man with Hat on 2010-07-07
Now for the part that hopefully is being read by people who can help me!!

After much stuffing around, I decided to just install linux on the same partition again. This worked fine, although I'm not sure if I did something funky because it created its own little 10gig partition and booted from that. I could then use the command:
[B]
sudo update-grub[/B]

And what do you know? I had a nice bootable grub menu when I turned the computer on. Hooray I thought. I could boot into my new 10gig linux and also into my windows XP. In the linux bootup, I could see my original partition with the original linux accounts etc on it (obviously couldn't do this in Win xp). I decided in windows to install Office, but because of my lack of foresight, I hadn't dedicated enough space on the NTFS partition for it. So I chucked in the live CD and used GPART to make my linux partition 30gig smaller and NTFS bigger. It said everything was successful. So I restarted, looked at my grub menu (which by the way contains about 10 choices for linux - I only use the first - and one for win) and booted to Win. It went as far as bringing the splash screen up and no further. I tried to boot to linux. This one actually showed my my accounts and asked me to log in, but when I tried it told me to contact my computer administrator. After I contacted myself, I realised that my computer administrator is way over his head. When I get back from work today I will keep trying things out, but some guidance would be really fantastic someone.....

---

### Post by oldfred on 2010-07-07
You may not have boot issues that this covers as it is up thru the grub menu.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

If you get a windows screen then grub has booted it and windows then has troubles. It often does not like to be resized and at the minimum wants to run chkdsk. If you have a windows CD boot the repair section and run chkdsk.

chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 

The Ubuntu issue may be video driver?

---

### Post by Man with Hat on 2010-07-08
> **oldfred said:**
> You may not have boot issues that this covers as it is up thru the grub menu.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

If you get a windows screen then grub has booted it and windows then has troubles. It often does not like to be resized and at the minimum wants to run chkdsk. If you have a windows CD boot the repair section and run chkdsk.

chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 

The Ubuntu issue may be video driver?

Win XP #-o

I should have thought to do this!! Thanks, sometimes you just need someone to point it out! I will run that now and post results. 

Ubuntu :-k

I'm not sure.... I can't actually get past the login screen to figure this out now. I type in my username and password. It goes away as if it is going to load into my profile and then asks me for my username and password as if nothing had ever happened, but tells me to contact sys admin. Hold on.... Hmmm actually I am trying to remember the exact message, because it may have said something about this now that I think about it. Will be right back, but if it is a video card issue, how can I fix this? Can I do it through the live bootup? I would have thought this would not save anything I do.


Also here is the RESULTS.txt I don't know why it says Feb 15th
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    69,272,279    69,272,217  83 Linux
/dev/sda2    *     69,272,280   150,368,399    81,096,120   7 HPFS/NTFS
/dev/sda3         150,368,461   156,296,384     5,927,924   5 Extended
/dev/sda5         150,368,463   156,296,384     5,927,922  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   312,576,704   312,576,642   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        c37db846-1f03-49c2-8f74-2b0052660a81   ext3                                     
/dev/sda2        0AD45F25D45F1275                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        b7c5fb4f-3e9a-43f1-bf66-e4e6168433c0   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        32D0E903D0E8CE63                       ntfs       Storage                       
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=c37db846-1f03-49c2-8f74-2b0052660a81 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c37db846-1f03-49c2-8f74-2b0052660a81

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        c37db846-1f03-49c2-8f74-2b0052660a81
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=c37db846-1f03-49c2-8f74-2b0052660a81 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        c37db846-1f03-49c2-8f74-2b0052660a81
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=c37db846-1f03-49c2-8f74-2b0052660a81 ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic
uuid        c37db846-1f03-49c2-8f74-2b0052660a81
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=c37db846-1f03-49c2-8f74-2b0052660a81 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid        c37db846-1f03-49c2-8f74-2b0052660a81
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=c37db846-1f03-49c2-8f74-2b0052660a81 ro  single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid        c37db846-1f03-49c2-8f74-2b0052660a81
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=c37db846-1f03-49c2-8f74-2b0052660a81 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid        c37db846-1f03-49c2-8f74-2b0052660a81
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=c37db846-1f03-49c2-8f74-2b0052660a81 ro  single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-16-generic
uuid        c37db846-1f03-49c2-8f74-2b0052660a81
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=c37db846-1f03-49c2-8f74-2b0052660a81 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-16-generic (recovery mode)
uuid        c37db846-1f03-49c2-8f74-2b0052660a81
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=c37db846-1f03-49c2-8f74-2b0052660a81 ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Chainload into GRUB 2
root        c37db846-1f03-49c2-8f74-2b0052660a81
kernel        /boot/grub/core.img

title        Ubuntu 10.04 LTS, memtest86+
uuid        c37db846-1f03-49c2-8f74-2b0052660a81
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c37db846-1f03-49c2-8f74-2b0052660a81
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c37db846-1f03-49c2-8f74-2b0052660a81
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c37db846-1f03-49c2-8f74-2b0052660a81
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=c37db846-1f03-49c2-8f74-2b0052660a81 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c37db846-1f03-49c2-8f74-2b0052660a81
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=c37db846-1f03-49c2-8f74-2b0052660a81 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c37db846-1f03-49c2-8f74-2b0052660a81
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c37db846-1f03-49c2-8f74-2b0052660a81 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c37db846-1f03-49c2-8f74-2b0052660a81
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=c37db846-1f03-49c2-8f74-2b0052660a81 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c37db846-1f03-49c2-8f74-2b0052660a81
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=c37db846-1f03-49c2-8f74-2b0052660a81 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c37db846-1f03-49c2-8f74-2b0052660a81
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=c37db846-1f03-49c2-8f74-2b0052660a81 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c37db846-1f03-49c2-8f74-2b0052660a81
    linux    /boot/vmlinuz-2.6.28-16-generic root=UUID=c37db846-1f03-49c2-8f74-2b0052660a81 ro   quiet splash
    initrd    /boot/initrd.img-2.6.28-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c37db846-1f03-49c2-8f74-2b0052660a81
    echo    'Loading Linux 2.6.28-16-generic ...'
    linux    /boot/vmlinuz-2.6.28-16-generic root=UUID=c37db846-1f03-49c2-8f74-2b0052660a81 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.28-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c37db846-1f03-49c2-8f74-2b0052660a81
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c37db846-1f03-49c2-8f74-2b0052660a81
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0ad45f25d45f1275
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c37db846-1f03-49c2-8f74-2b0052660a81 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b7c5fb4f-3e9a-43f1-bf66-e4e6168433c0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   3.6GB: boot/grub/core.img
   3.5GB: boot/grub/grub.cfg
   8.5GB: boot/grub/menu.lst
   3.4GB: boot/grub/stage2
   3.5GB: boot/initrd.img-2.6.28-16-generic
   3.7GB: boot/initrd.img-2.6.31-21-generic
   4.7GB: boot/initrd.img-2.6.32-21-generic
   3.5GB: boot/initrd.img-2.6.32-22-generic
   3.4GB: boot/vmlinuz-2.6.28-16-generic
   3.4GB: boot/vmlinuz-2.6.31-21-generic
   3.7GB: boot/vmlinuz-2.6.32-21-generic
   3.4GB: boot/vmlinuz-2.6.32-22-generic
   4.7GB: initrd.img
   3.7GB: vmlinuz

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  00 00 08 00 00 00 67 00  65 00 74 00 56 00 61 00  |......g.e.t.V.a.|
00000010  6c 00 75 00 65 00 04 00  00 00 04 00 00 00 0b 00  |l.u.e...........|
00000020  00 00 24 00 70 00 6f 00  6c 00 6c 00 5f 00 73 00  |..$.p.o.l.l._.s.|
00000030  74 00 61 00 74 00 65 00  00 00 05 00 00 00 04 00  |t.a.t.e.........|
00000040  00 00 06 00 00 00 6c 00  6f 00 6f 00 6b 00 75 00  |......l.o.o.k.u.|
00000050  70 00 06 00 00 00 04 00  00 00 15 00 00 00 73 00  |p.............s.|
00000060  74 00 61 00 74 00 65 00  3a 00 70 00 6f 00 6c 00  |t.a.t.e.:.p.o.l.|
00000070  6c 00 5f 00 69 00 6e 00  74 00 65 00 72 00 76 00  |l._.i.n.t.e.r.v.|
00000080  61 00 6c 00 5f 00 73 00  00 00 07 00 00 00 04 00  |a.l._.s.........|
00000090  00 00 0b 00 00 00 67 00  65 00 74 00 49 00 6e 00  |......g.e.t.I.n.|
000000a0  74 00 56 00 61 00 6c 00  75 00 65 00 00 00 08 00  |t.V.a.l.u.e.....|
000000b0  00 00 04 00 00 00 0c 00  00 00 24 00 70 00 6f 00  |..........$.p.o.|
000000c0  6c 00 6c 00 5f 00 74 00  69 00 6d 00 65 00 5f 00  |l.l._.t.i.m.e._.|
000000d0  73 00 09 00 00 00 04 00  00 00 0d 00 00 00 73 00  |s.............s.|
000000e0  75 00 5f 00 67 00 65 00  74 00 5f 00 74 00 69 00  |u._.g.e.t._.t.i.|
000000f0  6d 00 65 00 5f 00 73 00  00 00 0a 00 00 00 04 00  |m.e._.s.........|
00000100  00 00 01 00 00 00 63 00  00 00 0b 00 00 00 04 00  |......c.........|
00000110  00 00 01 00 00 00 64 00  00 00 0c 00 00 00 04 00  |......d.........|
00000120  00 00 01 00 00 00 65 00  00 00 0d 00 00 00 04 00  |......e.........|
00000130  00 00 01 00 00 00 66 00  00 00 0e 00 00 00 04 00  |......f.........|
00000140  00 00 10 00 00 00 24 00  61 00 63 00 74 00 69 00  |......$.a.c.t.i.|
00000150  76 00 69 00 74 00 79 00  5f 00 74 00 69 00 6d 00  |v.i.t.y._.t.i.m.|
00000160  65 00 5f 00 73 00 0f 00  00 00 04 00 00 00 01 00  |e._.s...........|
00000170  00 00 68 00 00 00 10 00  00 00 04 00 00 00 01 00  |..h.............|
00000180  00 00 67 00 00 00 11 00  00 00 04 00 00 00 01 00  |..g.............|
00000190  00 00 62 00 00 00 12 00  00 00 04 00 00 00 01 00  |..b.............|
000001a0  00 00 61 00 00 00 13 00  00 00 04 00 00 00 08 00  |..a.............|
000001b0  00 00 73 00 65 00 74 00  56 00 61 00 6c 00 00 01  |..s.e.t.V.a.l...|
000001c0  c1 ff 82 fe ff ff 02 00  00 00 f2 73 5a 00 00 00  |...........sZ...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Man with Hat on 2010-07-08
GAHHHH!!! Ok now what!?!?!

I tried to do windows system repair and I am using (I am 99% sure) my password for my login as administrator password. I am sure this is the right one, I have been using it to login every day for some time now (sometimes several times a day). Is the password something else that is set by Microsoft? Or am I just doing something strange?

Also I don't know if this is normal, but it asked me to select a windows boot thingy to recover and gave me one option:
1. C:\windows

My windows partition installed itself onto H:\windows as what it thinks is C:\ is my secondary hard drive called "storage." Also I think it had something to do with linux already being on there. As there was no H:\ option, I just chose C:\
Maybe this has something to do with it? I am starting to feel quite stupid now!

{EDIT}
Oops! :) Administrator password was blank, just press enter LOL
I have now done the chkdsk and still the same problem. Thought I'd better add too that I was slapping head about the XP thing because after reading it from you, I remembered reading elsewhere to do this and not because I'm awesome at knowing what I am doing :) Oh and the C:\ thing didn't seem to be an issue at all. 

As far as the linux problem, here is the exact message....

**Install Problem!**
The configuration defaults
for GNOME Power Manager
have not been installed
correctly.
Please contact your
computer administrator.

---

### Post by Man with Hat on 2010-07-08
Latest now one the XP part is that I tried this solution  [http://support.microsoft.com/kb/310396](http://support.microsoft.com/kb/310396) as it suggested that the kernel  itself might be corrupted. This didn't appear to be the case. No further  on the linux side....

---

### Post by Man with Hat on 2010-07-08
I'm at the point now, where I feel like I am better to cut my losses. I would like to backup what I can onto my secondary HDD and reinstall both windows and linux (winxp first this time!!). I want to know how to backup my emails from evolution now though (seeing as the only way into my computer is through live cd. I think I will open a new thread on this issue too as it is a little separate. I will wait til tomorrow in case some more good help comes through preventing this last ditch move :)

---

### Post by nothingspecial on 2010-07-08
I am under the impression that evolution stores the mail in a hidden folder in your home directory called .evolution

You are not having a good time of it are you?

---

### Post by Man with Hat on 2010-07-08
A good time of this? NOOOOO!! ](*,)

I just did a search for "evolution" on my home folder and came up with 289 items. Any idea what I should be looking for and what to do once I find it? Also I have little padlocks on every singe one of them so I will need to get permission to them somehow. I always feel over my head in Linux!! I have started another thread aimed at this exact problem, maybe we could move this discussion there? :o

---

### Post by nothingspecial on 2010-07-08
ok

---

### Post by nothingspecial on 2010-07-08
As you have a whole mess of partitions and many Ubuntus and wotnot on your drive at the moment may I suggest you start again - but - this time create a separate home partition for Ubuntu. The reason I suggest this is that if this sort of thing ever happens again and you want to reinstall, all your settings and emails and what have you will be there and you won`t have to go through all this live cd business again. This is very easy to do.

From the live cd open the partition editor (gparted), it is somewhere in your menus.

Wipe what you have and create 4 new partitions - One for windows, a small about 7gig one for Ubuntu, an even smaller 4gig one for swap and the rest for /home

Do whatever you have to do to install windows, I know nothing of that.

Then when you are in the partitioning stage of the Ubuntu install choose manual (advanced)

Choose the 7 gig partition for Ubuntu, choose to format it ext4 and select a mountpoint of /

Choose the 4 gig one for swap and leave it alone

Choose the larger one for /home, choose to format it ext3 and select a mountpoint of /home

Now, next time you reinstall (hopefully atleast not until 10.10 is released) you do exactly the same thing as you just did except
[SIZE=5][COLOR=Red]
DO NOT CHECK (TICK) THE FORMAT BOX FOR YOUR HOME PARTITION[/COLOR][/SIZE] 

Then there will be no need to copy anything before you do.

Oh and make sure you know where windows is, cheers.

---

### Post by oldfred on 2010-07-08
If you are going to reinstall and have mutiple drives, you must know about the advanced button on the last partition screen where it says ready to install. The advanced button controls which drive grub gets installed to. I recommend leaving windows boot loader in the windows drive, putting grub on the Ubuntu drive and setting the Ubuntu drive as the boot drive in BIOS.

[http://members.iinet.net/~herman546/p28/032_install-now.png]("http://members.iinet.net/%7Eherman546/p28/032_install-now.png")

If you still want to try to fix it. ( We often like to try to fix things even if it takes days or weeks:smile:. I was able to install in 9 min to partitions already created from a USB flash drive, updates took at least twice as long):

the only thing I see in the boot script results is that you have grub legacy's menu.lst still in the grub folder. That sometimes has caused confusion with grub and we have had to totally uninstall both versions of grub and cleanly install grub2.

I have a nvidia card and had to add nomodeset in place of quiet splash to boot. Works for some other cards and other setting are needed for some. What video card do you have.  You use the edit e on the grub menu and scroll to the linux line to edit and then boot. If that works you can either install drivers or edit the line permanently in /etc/default/grub.

---

### Post by Man with Hat on 2010-07-08
> **nothingspecial said:**
> As you have a whole mess of partitions and many Ubuntus and wotnot on your drive at the moment may I suggest you start again - but - this time create a separate home partition for Ubuntu. The reason I suggest this is that if this sort of thing ever happens again and you want to reinstall, all your settings and emails and what have you will be there and you won`t have to go through all this live cd business again. This is very easy to do.

From the live cd open the partition editor (gparted), it is somewhere in your menus.

Wipe what you have and create 4 new partitions - One for windows, a small about 7gig one for Ubuntu, an even smaller 4gig one for swap and the rest for /home

Do whatever you have to do to install windows, I know nothing of that.

Then when you are in the partitioning stage of the Ubuntu install choose manual (advanced)

Choose the 7 gig partition for Ubuntu, choose to format it ext4 and select a mountpoint of /

Choose the 4 gig one for swap and leave it alone

Choose the larger one for /home, choose to format it ext3 and select a mountpoint of /home

Now, next time you reinstall (hopefully atleast not until 10.10 is released) you do exactly the same thing as you just did except
[SIZE=5][COLOR=Red]
DO NOT CHECK (TICK) THE FORMAT BOX FOR YOUR HOME PARTITION[/COLOR][/SIZE] 

Then there will be no need to copy anything before you do.

Oh and make sure you know where windows is, cheers.

Cheers, thats really good advice and I wish I had done that in the first place! I think I now understand how I went wrong earlier because I did actually click advanced and kinda guessed the options I needed :-\" and set a mount point of / at ext 3. It decided to create its own 10 gig for ubuntu when I did that. I kinda like to play around in the advanced areas because I have some idea of what I am doing, but I learn more too this way. Unfortunately this usually comes at a price....

My only other thought on this is there might be a chance that having applications on a separate partition could slow everything down when I try to run them. But as I have never done it before, I don't know. Any thoughts? Also this might be a good idea for the windows install to have 2 partitions, one for the install and one for apps. Too bad they have such different format needs, I could have just installed all apps on the one big partition for either OS.

---

### Post by Man with Hat on 2010-07-08
> **oldfred said:**
> If you are going to reinstall and have mutiple drives, you must know about the advanced button on the last partition screen where it says ready to install. The advanced button controls which drive grub gets installed to. I recommend leaving windows boot loader in the windows drive, putting grub on the Ubuntu drive and setting the Ubuntu drive as the boot drive in BIOS.

[http://members.iinet.net/~herman546/p28/032_install-now.png]("http://members.iinet.net/%7Eherman546/p28/032_install-now.png")

If you still want to try to fix it. ( We often like to try to fix things even if it takes days or weeks:smile:. I was able to install in 9 min to partitions already created from a USB flash drive, updates took at least twice as long):

the only thing I see in the boot script results is that you have grub legacy's menu.lst still in the grub folder. That sometimes has caused confusion with grub and we have had to totally uninstall both versions of grub and cleanly install grub2.

I have a nvidia card and had to add nomodeset in place of quiet splash to boot. Works for some other cards and other setting are needed for some. What video card do you have.  You use the edit e on the grub menu and scroll to the linux line to edit and then boot. If that works you can either install drivers or edit the line permanently in /etc/default/grub.

Yeah I used the advanced button on my install the other day, which is why some things got better and others got hairy ;)

My card is an Nvidia 7800GTX. In earlier versions of Ubuntu I remember that I needed to install the older driver for as it worked and the newer one didn't. I have never heard of nomodeset or quiet splash, but I could hazard a guess at what they are. I will do as you say, hopefully this might be of some help :p

Maybe I will uninstall/re-install grub to see if that helps anything. The thing that I don't really understand is why the problem is same for both Linux and Win boot up. Both have an issue right at the login screen. Is this grub related or not? I thought that grub would have finished everything it cares about by now and something else would have taken over, but that might just be showing my ignorance to what grub could be...

I didn't even realise that you could choose boot loaders in bios. Probably because I am used to only dealing with one OS at any time. 

I like to try fixing things too which is probably why I enjoy being on the computer, something is always going wrong :) This time though I really need things to be fixed fast!! I actually was hoping to have this fixed a couple of days ago, I didn't realise all the little problems that could go wrong. I should have just left things when I had access to both OS until after I finished all the work on the docs/emails that I need to do. Then try to go about fixing it up. The whole reformat thing now is more about I need to get this work done and starting again (even though it is time consuming) may be the quickest option!

---

### Post by Man with Hat on 2010-07-09
> **Man with Hat said:**
> 
**Install Problem!**
The configuration defaults
for GNOME Power Manager
have not been installed
correctly.
Please contact your
computer administrator.

If anyone ever gets this message, it translates into English like this: Your disk is too full, delete something so that I may boot up!

For a slightly advanced (well to me its advanced) way of going about this. I decided that I would delete my downloads folder. But I also wanted to delete it from the trash. This is how I went about it form a live bootup. Got to Terminal and type:

```
gksudo nautilus
```This will give you ultimate power in your computer and allow you to actually do normal things like delete and access files. It will also open up a GUI window for you so you don't have to type everything, but I used a combo of both.

Find whatever files you wish to delete and "move to trash can" - at this point they are still taking up space on the HDD. Then you need to find your trash can. It should be in the "/" directory (which is before the home directory). You will need to "ctrl + H" to see hidden files. Trash can is ".Trash-0" (where the dot means hidden). Right click on it and change the tab to permissions. I said "create and delete files" on pretty much every place for every user (be more choosy if you want, I was getting frustrated and just went all out!) and then press the "apply permissions to enclosed files" so that you will have permission for all files in trash. Now I couldn't find a way to "remove" just here, so I went back to terminal.

```
cd /media
```you will now need to change to your HDD that has ubuntu on it. The easiest way to see it is a simple

```
ls
```And you will see every drive listed. For me my drive has changed its name (not by my choice) to a really long one. This is where the tab feature is great. I could see that the drive I want starts with the letter "c" so I type:

```
 cd c
```Press Tab and I now see

```
 cd c37db846-1f03-49c2-8f74-2b0052660a81 
```Now that I am here I use the following (don't need all of this, I am just including it so its there for reference)

```
ls -a
cd .Trash-0/files
rm -rf /downloads
```The first part will list all files and the -a will tell it to list hidden files
Then I am changing to the directory where my trash is (you can always us ls at any point to list files in directory)
The next part is remove (rm) and all files inside of directory (-rf) then the directory name I want to remove. It is really important that you include the directory name, **don't get caught removing all files on your hard drive by pressing enter after* "*rm -rf /" or something!!!! **The Tab key can also be your new best friend as it will auto finish (or at least suggest) what you want to type. I have now booted into my Ubuntu and am typing this. Now to try and sort out windows (well there is a lot to do here, but at least I am here). I think at the end of this I will do a clean install of both OS anyway just to feel good about it all!

{EDIT}
***!!GOOD TO KNOW!! The main Trash directory seems to be this one:***

/home/{user name}/.local/share/Trash

Use the same steps as above to remove these. I used "rm -rf files" to delete and then remade a new directory called files where the old one was. I'm sure there is a command that just deletes the interior of the directory without deleting the directory itself, but I didn't know where it was.

---

### Post by Man with Hat on 2010-07-09
](*,) Where did my HDD go?

It no longer appears on the "places" menu as file system. I get the feeling that its not mounting or something, but shouldn't it have mounted? I mean in all seriousness isn't this step one of the boot process or something??! GARHGAHAHAEH!!@$@#^

Also to note, this is the second boot up I have done since the last post and I saw the file system there and had a nice browse (although I had no permissions?!?!). Now it has *poof* disappeared into thin air. Well I need to go again, I will try more things when I get back.

](*,) <- This is starting to hurt

---

### Post by Man with Hat on 2010-07-09
Hmmm I think I know the problem. I can't see my drive under "/media/dev/sda1" or whatever it was anymore because I chose at install to mount it at "/." The annoying thing is that I no longer seem to be root! I have gone into nautilus and then changed the file permission to set me as owner of the file system, but it still shows as "root" after I login. Well at least things are slowly getting better.... I am going to keep saying it, but a fresh install might just be as good as a holiday at the moment. But after I do all the work I need to do (if I ever start it instead of trying to make this computer behave :D)

---

### Post by Man with Hat on 2010-07-09
Whew, getting there!!

I am now writing this from windows XP. It seems that the best thing to do was to chuck in the installation disc and do a repair installation. All of my settings appear to have been saved, although I seem unable to turn windows firewall on. As a whole bunch of drivers just got installed, I am hoping this problem will fix itself on the next boot. No problems with Grub, I thought that windows bootloader would take over again, but it didn't! :p

So at a glance, I appear to have access to both Win XP and linux now (although both are running terribly, they are running!). Win XP has no sound, but I will see if installing the creative drivers again will fix this. I haven't gone through yet and re-installed all drivers again.

I think the whole thing needs to be upgraded to SP3 again too.

I did notice something (that I have no idea how I missed!) from the **[_original guide_]("http://ubuntuforums.org/showthread.php?t=1195275") to grub2. Maybe following section 12. Straight away may have been the best solution.** It is a purge uninstall of Grub2 and then a re-install of it. This may have solved all of my problems, but now I will never know. I hope that anyone reading this tries it first!!!!

---

### Post by Man with Hat on 2010-07-12
I'm going to mark this thread as solved now, but before I do I thought I would add one last... Well thought.

I noticed that after using Gpart to repartition my HDDs, the HDD names had changed. The issue with this didn't click until today (BTW I am halfway through doing clean installs of both with Winxp first this time) but I believe this to be the reason that windows had trouble. I noticed it because I couldn't do anything in windows besides a few tasks. The registry had everything pointing to H:\ when it had now been renamed ad D:\ for some reason. This stuffed everything and was the reason that I finally threw in the towel and have decided that a clean install is much better than playing with the registry entries. 

Anyway all the info in this thread is a little scattered, but I believe it does contain (including the links) all the right info to get out of trouble should this be a problem to the next unsuspecting victim! Just needs re-piecing in the correct order I think ;)

---

