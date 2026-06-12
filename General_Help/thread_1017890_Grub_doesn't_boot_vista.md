---
title: "Grub doesn't boot vista"
date: 2008-12-21
forum: General Help
---

### Post by Sweet666 on 2008-12-21
Hello everybody,

I have a huge problem, grub doesn't want to boot vista nor xp.

When I switch on my computer, grub proposes ubuntu or windows.
When I chose windows I have an error message:
 "Error 11: Unrecognised device string
  Press any key to continue "
There is nothing else, just this message.
I have some geek friends and they tried a lot of things but nothing worked. When I use ubuntu I have access to the vista partition and the xp partition.

Please help me, I am desperate and I have no idea what I should do and I'd like to avoid the solution of installing all again.

Beyond you will find my configuration and my grub configuration.

Thanks


_[SIZE="4"]My configuration is:[/SIZE]_



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=ccedb8c9-259f-4710-90c0-39672a3eaad6 /home           ext3    relatime        0       2
# /dev/sda8
UUID=88608CA0608C969A /media/data     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=C204813304812B8B /media/vista    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=8E180A8E180A760D /media/xp       ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=d9659e02-7aaf-44e9-bd00-2588df06c1fc /usr            ext3    relatime        0       2
# /dev/sda9
UUID=d03a3798-ddd3-48b0-a0cc-7fc8b870cf90 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0




[SIZE="4"]_My grub configuration is:_[/SIZE]



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
# kopt=root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by caljohnsmith on 2008-12-21
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "boot_info_results.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

---

### Post by Sweet666 on 2008-12-21
Here comes what you asked for:





#!/bin/bash
#to use this script:
#
#sudo bash boot_info_script.txt
#
#date  12/19/08
#author  meierfra.  (with lots of input from caljohnsmith)
# 
#Looks at all MBRs and identifes the boot loader. 
#   For Grub and Supergrub:  displays the controlling partition.
#   If the  MBR's is unknown, displays the whole MBR.
#Looks at all  partitions:
#   Determines their type
#          For ntfs: displays the offset of the partition as recorded
#          in  the boot sector
#   Identifes their boot sectors.
#         For grub: displays the controlling partition and the offset
#         of the stage2 file as recorded in the boot sector.
#   Identifies the operating system
#   Lists  boot programs.
#   Displays "fdisk -lu"
#   Displays "blkid -c /dev/null"
#   Displays "sfdisk -d"
#   Finds  boot directories and displays their contents.
#   For EasyBCD: finds all bootpart codes  and displays the offset
#                and boot drive its is trying to chainloade. 
#   Finds and displays  boot configuration files.
#All information is written to the file "boot_info_results.txt" in the
#    same folder as the script
#
#To do:
#   Information should be displayed in a nicer format.
#   Extract info from BCD? Possible? 
#   Identify Distros. 
#   List offsets of some boot files (for Grub error 18)
#   Boot sector info for grub is confusing.
#   Examine the  NTFS boot sector more closely to see whether
#     testdisk "RebuildBS" needs to be run.
#   Read bootpart files and see which boot sector it is pointing to.  
#   Test the script on different distros.
#    Use command line options, to choose what information to display.
#   On vfat partition "ntldr" and "ntdecct.com" are 
#       list in all lowercase and in all caps
#  vfat boot sector are not identfied
#  On fedora line 230 (offset=$(hexdump -s 0x44 -n 4 -e '"%d"' $part);
#     gives a "hexdump illegal seek error" same error in some other place
#              


Boot_Dir="
    /Boot
    /boot
    /BOOT
    /boot/grub
    /grub
    /ubuntu/disks
    /ubuntu/disks/boot/
    /ubuntu/disks/boot/grub
    /ubuntu/disks/install/boot
    /ubuntu/disks/boot/grub
    /NST
    "

Boot_Prog="
    /bootmgr
    /BOOTMGR
    /grldr
    /GRLDR
    /ntldr
    /NTLDR
    /NTDETECT.COM
    /ntdetect.com
    /NTBOOTDD.SYS
    /ntbootdd.sys
    /wubildr.mbr
    /ubuntu/winboot/wubildr.mbr
     "

Boot_Files="
    /boot/grub/menu.lst
    /grub/menu.lst
    /menu.lst
    /ubuntu/disks/boot/grub/menu.lst
    /ubuntu/disks/install/boot/grub/menu.lst
    /boot/grub/grub.conf
    /grub/grub.conf
    /grub.conf
    /boot.ini
    /etc/fstab
    "

Dir=`cd $(dirname $0);pwd`;
LogFile=$Dir/boot_info_results.txt

exec 6>&1   
exec >$LogFile

Folder=/tmp/BootInfo
while (! mkdir $Folder$i 2>/dev/null)
    do  
      ((i++))
      wait;
    done
Folder=$Folder$i

cd $Folder

Log1=$Folder/Log1
Error_Log=$Folder/Error_Log
Trash=$Folder/Trash
Mount_Error=$Folder/Mount_Error
Unknown_MBR=$Folder/Unknown_MBR
Tmp_Log=$Folder/Tmp_Log
exec 2>$Error_Log


Hard_Drives=$(ls /dev/hd? /dev/sd? 2>>$Trash )
for drive in $Hard_Drives;
  do 
    Message=$(echo is installed in the MBR of  $drive)
    case $(hexdump   -v -n  2 -e '/1 "%x"'  $drive) in
	eb48) BL=Grub
             dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $drive);
             offset=$(hexdump -s 0x44 -n 4 -e '"%d"' $drive);
              if  [ "$offset" != 1 ];
	      then
                  pa=-1
                  for hdd in $Hard_Drives;
		  do
		      tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump    -n 4 -e '"%x"');
                      if [ "$tmp" = 3be5652 ]; then
                      pa=$(dd if=$hdd skip=$((offset+1)) count=1 2>>$Trash | hexdump  -s 0xa  -n 1 -e '"%d"');
                      stage2_hdd=$hdd
                      fi;
                  done;
                  let dr-127
                  Message=$(echo $Message and looks at sector $offset)         
                  if [ "$dr" = 128 ];
                      then
                          Message=$(echo $Message of the same hard drive) 
                      else
                           Message=$(echo $Message on boot drive \#$dr)
		  fi;
                    Message=$(echo $Message for the stage2 file.);
                    
                        if [ "$pa" = -1  ]
		     then
		         Message=$(echo $Message, but no stage2 files can be found at this location); 
                     else
                       pa=$((pa+1))
                        Message=$(echo $Message \(a  stage2 file is  at this location on $stage2_hdd\)  and on)
                        if [ $pa = 256 ];
                        then
                            Message=$(echo $Message  the same partition) 
                        else
                           Message=$(echo $Message  partition \#$pa) 
	                fi;
                       Message=$(echo $Message for menu.lst.)
                     fi;
		 
	      else
	      pa=$(hexdump -s 0x419 -n 1 -e '"%d"' $drive);
              dr=$(hexdump -s 0x41a -n 1 -e '"%d"' $drive);
              if [ $pa$dr = 4649 ]; 
		then
		BL=SuperGrub
                pa=$(hexdump -s 0x41e -n 1 -e '"%d"' $drive);
                dr=$(hexdump -s 0x41f -n 1 -e '"%d"' $drive);
 	      fi
              dr=$((dr-127))
              pa=$((pa+1))
              if [ $dr = 128 ];
               then
                Message=$(echo $Message  and  looks on the same drive in partition \#$pa  for its boot files.)
              else
               Message=$(echo $Message  and looks  on boot drive \#$dr in partition \#$pa  for its boot files.)
            fi;
	    fi;; 
 	33c0) BL=Windows;;
	fa31) BL=Syslinux;;
	faeb) BL=Lilo;; 
	fc31) BL=Testdisk;;
	eb5e) BL=Grub4Dos;;
	b800) BL=Plop;;
	33ff) BL=Gateway?;;
	fceb) BL=Bootit;;
          00) BL="No boot loader";;
	   *) BL="No known boot loader"
              echo "Unknown MBR on $drive" >> $Unknown_MBR;
              echo >> $Unknown_MBR;
              hexdump -n 512 -C $drive >> $Unknown_MBR;
              echo >> $Unknown_MBR;;
        esac;
        echo $BL $Message
  
    sfdisk -d  $drive >>$Log1;
    done
    echo


for part in $(ls /dev/hd??* /dev/sd??* 2>>$Trash)
   do
      BSI=""
      drive=${part:0:8}
      part_number=${part:8}
      part_type=$(sfdisk -c $drive $part_number)
      name=$(basename $part);
      echo  $name:;
      mkdir $name 
      type=$( /lib/udev/vol_id -t $part 2>$Tmp_Log );
      if [ $part_type = 5 ] || [ $part_type = f ] && [ "$type" = "" ] ;
         then
	 type="Extended Partition";
	 cat $Tmp_Log>>$Trash;
	 else
         cat $Tmp_Log>>$Error_Log
      fi;
      echo "    File system:  "$type;
      if [ "$type" != "swap" ]  && [ "$type" != "Extended Partition"  ] && [ "$type" != "unknown volume type" ] && [ "$type" != "LVM2_member" ]  ;
       then 
      if  mount $part $name 2>$Mount_Error; then
      if [ "$type" = "ntfs" ];
         then
         offset=$(hexdump -s 0x1c -n 4 -e '"%d\n"' $part);
         BSI=$(echo  According to  the  info in the boot sector, $name starts at sector $offset.)   
      fi;
          case $(hexdump -v -s 0x80 -n  2 -e '/1 "%x"'  $part) in
            08cd) BST=XP;;
            b6d1) BST=XP;;
	    55aa) BST=Vista;;           
	    5272) BST=Grub;
                  offset=$(hexdump -s 0x44 -n 4 -e '"%d"' $part);
                  dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $part);
                   pa=-1
                  for hdd in $Hard_Drives;
		  do
		      tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump    -n 4 -e '"%x"');
                      if [ "$tmp" = 3be5652 ]; then
                      pa=$(dd if=$hdd skip=$((offset+1)) count=1 2>>$Trash | hexdump  -s 0xa  -n 1 -e '"%d"');
                      stage2_hdd=$hdd
                      fi;
                  done;
                  dr=$((dr-127))
                  BSI=$(echo $BSI Grub is installed to the boot sector of $part and looks at sector $offset )        
                  if [ "$dr" = 128 ];
                      then
                          BSI=$(echo $BSI of the same hard drive) 
                      else
                          BSI=$(echo $BSI on boot drive \#$dr)
		  fi;
                  BSI=$(echo $BSI for the stage2 file.);
                    
                        if [ "$pa" = T  ]
		     then
		        BSI=$(echo $BSI, but no stage2 files can be found at this location); 
                     else
                       pa=$((pa+1))
                       BSI=$(echo $BSI  \(a  stage2 file is  at this location on $stage2_hdd\)  and on )                       
                        if [ "$pa" = 256 ];
                        then
                           BSI=$(echo $BSI the same partition) 
                        else
                            BSI=$(echo $BSI  partition \#$pa )
	                fi;
                      BSI=$(echo $BSI for menu.lst.)
                     fi;;
                  
                   
            7cc6) BST=Win_98;;
            7304) BST=Dos_1.0;;
            2d5e) BST=Dos_1.1;;
 	      00) sig2=$(hexdump -v -s 0x80 -n  2 -e '/1 "%x"'  $part)
                      if [ "$sig2" = 00 ];
		      then
                      BST="No Boot Loader";
		      else
		      BST="Unknown"
                      echo "Unknown BootLoader  on $part" >> $Unknown_MBR;
                      echo >> $Unknown_MBR;
                      hexdump -n 512 -C $part >> $Unknown_MBR;
                      echo >> $Unknown_MBR;
                  fi;;
                *) BST="Unknown"
                   echo "Unknown BootLoader  on $part" >> $Unknown_MBR;
                   echo >> $Unknown_MBR;
                   hexdump -n 512 -C $part >> $Unknown_MBR;
                   echo >> $Unknown_MBR;
            esac;

       OS=""
       [ -e $name"/Windows/System32/config/BCD-Template" ] ||  [ -e $name"/windows/system32/config/bcd-template" ] || [ -e $name"/WINDOWS/System32/config/BCD-Template" ] ||
  [ -e $name"/WINDOWS/system32/config/BCD-Template" ] && OS=Vista

       [ -e $name"/Windows/System32/config/SecEvent.Evt" ] ||  [ -e $name"/WINDOWS/system32/config/SecEvent.Evt" ] || [ -e $name"/WINDOWS/system32/config/secevent.evt" ] || [ -e $name"/windows/system32/config/secevent.evt" ] && OS=XP
  
       [ -e $name"/etc" ] && OS=$(cat $name/etc/issue)
     

       BootFiles=""
       for file in $Boot_Files;
       do
           if [ -e $name$file ];
              then BootFiles=$(echo $BootFiles"  "$file);
	      echo >> $Log1
	      echo $name$file >> $Log1;
              echo >> $Log1
              cat $name$file >> $Log1;
	   fi;
       done;

       for file in $Boot_Prog;
       do
           if [ -e $name$file ];
              then BootFiles=$(echo $BootFiles"  "$file);          
	   fi;
       done;

       for file in $Boot_Dir;
       do
           if [ -e $name$file ];
              then BootFiles=$(echo $BootFiles"  "$file); 
	      echo >> $Log1
	      echo $name$file >> $Log1;
              echo >> $Log1
              ls -la  $name$file >> $Log1 ; 
              if [ "$file" = "/NST" ];
		  then
		  for loader in $( ls  $name$file );
		  do
                      sig=$(hexdump -s 0x101 -n 8  -e '8/1 "%_p"' $name$file/$loader)
                      if [ "$sig"  = "BootPart" ]
			  then
                          offset=$(hexdump -s 0xf1 -n 4 -e '"%d"' $name$file/$loader);
                              dr=$(hexdump -s 0x6f -n 1 -e '"%d"' $name$file/$loader);
			      dr=$((dr -127))
 			  BSI=$(echo $BSI "  "BootPart in $loader is trying to chain load sector \#$offset on boot drive \#$dr);
		       fi;
		  done;
               fi;
	   fi;
       done;

      echo "    Boot sector  type:  "$BST
      echo "    Boot sector  info:  "$BSI  
      echo "    Operating System: "$OS
      echo "    Boot files/directories present: " $BootFiles
     
     umount $name ;
     else
     echo "    Mounting failed:  ";  
     cat   $Mount_Error;
     fi;
     fi;
     echo;
 
     done;

fdisk -lu
blkid -c /dev/null
echo >> $Log1
echo "StdErr Messages ">>$Log1
echo >> $Log1
cat $Log1
[ -e $Unknown_MBR ] && cat $Unknown_MBR
cat $Error_Log
chown $(basename ~) $LogFile
exec 1>&-
exec 1>&6
exec 6>&-
echo Finished. The results are in the file $(basename $LogFile)   located in $Dir

---

### Post by caljohnsmith on 2008-12-21
You accidentally posted the "boot_info_[COLOR="Blue"]script[/COLOR].txt" file; please post instead the "boot_info_[COLOR="Blue"]results[/COLOR].txt" file. :)

---

### Post by Sweet666 on 2008-12-21
Grub is installed in the MBR of /dev/sda and looks on the same drive in partition #6 for its boot files.
Windows is installed in the MBR of /dev/sdb
Windows is installed in the MBR of /dev/sdc

sda1:
    File system:  ntfs
    Boot sector  type:  Vista
    Boot sector  info:  According to the info in the boot sector, sda1 starts at sector 2048.
    Operating System: 
    Boot files/directories present:  /bootmgr /boot

sda2:
    File system:  ntfs
    Boot sector  type:  Vista
    Boot sector  info:  According to the info in the boot sector, sda2 starts at sector 24578048.
    Operating System: Vista
    Boot files/directories present:  /boot.ini /bootmgr /ntldr /NTDETECT.COM /Boot

sda3:
    File system:  Extended Partition

sda5:
    File system:  ntfs
    Boot sector  type:  Unknown
    Boot sector  info:  According to the info in the boot sector, sda5 starts at sector 126.
    Operating System: XP
    Boot files/directories present: 

sda6:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: Ubuntu 8.04.2 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda7:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sda8:
    File system:  ntfs
    Boot sector  type:  Vista
    Boot sector  info:  According to the info in the boot sector, sda8 starts at sector 63.
    Operating System: 
    Boot files/directories present: 

sda9:
    File system:  swap

sdb1:
    File system:  Extended Partition

sdb5:
    File system:  ext3
    Boot sector  type:  No Boot Loader
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sdc1:
    File system:  vfat
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 


Platte /dev/sda: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder, zusammen 488397168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Disk identifier: 0xe5fbbd23

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1            2048    24578047    12288000   27  Unbekannt
Partition 1 endet nicht an einer Zylindergrenze.
/dev/sda2   *    24578048    64578047    20000000    7  HPFS/NTFS
Partition 2 endet nicht an einer Zylindergrenze.
/dev/sda3        64581300   488392064   211905382+   f  W95 Erw. (LBA)
/dev/sda5        64581426    96036569    15727572    7  HPFS/NTFS
/dev/sda6        96036633   104036939     4000153+  83  Linux
/dev/sda7       104037003   136038419    16000708+  83  Linux
/dev/sda8       136038483   483138809   173550163+   7  HPFS/NTFS
/dev/sda9       483138873   488392064     2626596   82  Linux Swap / Solaris

Platte /dev/sdb: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder, zusammen 488397168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Disk identifier: 0xc6e55532

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1              63   488392064   244196001    f  W95 Erw. (LBA)
/dev/sdb5             126   488392064   244195969+  83  Linux

Platte /dev/sdc: 320.0 GByte, 320072933376 Byte
255 Köpfe, 63 Sektoren/Spuren, 38913 Zylinder, zusammen 625142448 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Disk identifier: 0x44fdfe06

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdc1              63   625137344   312568641    c  W95 FAT32 (LBA)
/dev/sda1: UUID="96B67ED5B67EB4F9" LABEL="WinRE" TYPE="ntfs" 
/dev/sda2: UUID="C204813304812B8B" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sda5: UUID="8E180A8E180A760D" LABEL="XP" TYPE="ntfs" 
/dev/sda6: UUID="d04ffdf6-d533-4f24-8366-02d2a4079d3d" TYPE="ext3" 
/dev/sda7: UUID="d9659e02-7aaf-44e9-bd00-2588df06c1fc" TYPE="ext3" 
/dev/sda8: UUID="88608CA0608C969A" LABEL="DATA" TYPE="ntfs" 
/dev/sda9: TYPE="swap" UUID="d03a3798-ddd3-48b0-a0cc-7fc8b870cf90" 
/dev/sdb5: UUID="ccedb8c9-259f-4710-90c0-39672a3eaad6" TYPE="ext3" 
/dev/sdc1: LABEL="My Book" UUID="47B6-E2F4" TYPE="vfat" 
# Partitionstabelle von /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 24576000, Id=27
/dev/sda2 : start= 24578048, size= 40000000, Id= 7, bootable
/dev/sda3 : start= 64581300, size=423810765, Id= f
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 64581426, size= 31455144, Id= 7
/dev/sda6 : start= 96036633, size=  8000307, Id=83
/dev/sda7 : start=104037003, size= 32001417, Id=83
/dev/sda8 : start=136038483, size=347100327, Id= 7
/dev/sda9 : start=483138873, size=  5253192, Id=82
# Partitionstabelle von /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=488392002, Id= f
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
/dev/sdb5 : start=      126, size=488391939, Id=83
# Partitionstabelle von /dev/sdc
unit: sectors

/dev/sdc1 : start=       63, size=625137282, Id= c
/dev/sdc2 : start=        0, size=        0, Id= 0
/dev/sdc3 : start=        0, size=        0, Id= 0
/dev/sdc4 : start=        0, size=        0, Id= 0

sda1/boot

insgesamt 3100
drwxrwxrwx 1 root root       0 2008-02-05 17:24 .
drwxrwxrwx 1 root root    4096 2008-02-06 04:12 ..
-rwxrwxrwx 1 root root 3170304 2006-09-18 14:45 boot.sdi

sda2/boot.ini

[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

sda2/Boot

insgesamt 744
drwxrwx--- 1 root plugdev   4096 2008-02-06 03:03 .
drwxrwx--- 1 root plugdev  12288 2008-12-21 17:01 ..
-rwxrwx--- 1 root plugdev 262144 2008-12-13 19:41 BCD
-rwxrwx--- 1 root plugdev  25600 2008-12-13 18:40 BCD.LOG
-rwxrwx--- 2 root plugdev      0 2008-02-06 03:03 BCD.LOG1
-rwxrwx--- 2 root plugdev      0 2008-02-06 03:03 BCD.LOG2
-rwxrwx--- 1 root plugdev  65536 2008-02-06 03:03 bootstat.dat
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 cs-CZ
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 da-DK
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 de-DE
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 el-GR
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 en-US
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 es-ES
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 fi-FI
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 Fonts
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 fr-FR
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 hu-HU
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 it-IT
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 ja-JP
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 ko-KR
-rwxrwx--- 1 root plugdev 386664 2006-11-02 10:51 memtest.exe
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 nb-NO
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 nl-NL
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 pl-PL
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 pt-BR
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 pt-PT
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 ru-RU
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 sv-SE
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 tr-TR
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 zh-CN
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 zh-HK
drwxrwx--- 1 root plugdev      0 2008-02-06 03:03 zh-TW

sda6/boot/grub/menu.lst

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
# kopt=root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


sda6/etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=ccedb8c9-259f-4710-90c0-39672a3eaad6 /home           ext3    relatime        0       2
# /dev/sda8
UUID=88608CA0608C969A /media/data     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=C204813304812B8B /media/vista    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=8E180A8E180A760D /media/xp       ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=d9659e02-7aaf-44e9-bd00-2588df06c1fc /usr            ext3    relatime        0       2
# /dev/sda9
UUID=d03a3798-ddd3-48b0-a0cc-7fc8b870cf90 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

sda6/boot

insgesamt 94048
drwxr-xr-x  3 root root    4096 2008-12-17 20:48 .
drwxr-xr-x 21 root root    4096 2008-12-17 20:48 ..
-rw-r--r--  1 root root  422607 2008-04-10 18:51 abi-2.6.24-16-generic
-rw-r--r--  1 root root  422667 2008-08-21 06:46 abi-2.6.24-19-generic
-rw-r--r--  1 root root  422838 2008-10-22 05:12 abi-2.6.24-21-generic
-rw-r--r--  1 root root  422838 2008-11-24 23:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root  422838 2008-11-27 23:13 abi-2.6.24-23-generic
-rw-r--r--  1 root root   79964 2008-04-10 18:51 config-2.6.24-16-generic
-rw-r--r--  1 root root   80049 2008-08-21 06:46 config-2.6.24-19-generic
-rw-r--r--  1 root root   80062 2008-10-22 05:12 config-2.6.24-21-generic
-rw-r--r--  1 root root   80062 2008-11-24 23:47 config-2.6.24-22-generic
-rw-r--r--  1 root root   80051 2008-11-27 23:13 config-2.6.24-23-generic
drwxr-xr-x  2 root root    4096 2008-12-21 19:17 grub
-rw-r--r--  1 root root 8160720 2008-07-01 01:39 initrd.img-2.6.24-16-generic
-rw-r--r--  1 root root 7765601 2008-04-22 20:44 initrd.img-2.6.24-16-generic.bak
-rw-r--r--  1 root root 7918059 2008-08-27 17:26 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 7917692 2008-08-13 17:21 initrd.img-2.6.24-19-generic.bak
-rw-r--r--  1 root root 7920151 2008-11-07 10:03 initrd.img-2.6.24-21-generic
-rw-r--r--  1 root root 7919468 2008-11-02 20:19 initrd.img-2.6.24-21-generic.bak
-rw-r--r--  1 root root 7918694 2008-12-07 16:58 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7917697 2008-12-01 09:05 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root 7918546 2008-12-17 20:48 initrd.img-2.6.24-23-generic
-rw-r--r--  1 root root 7918449 2008-12-17 20:48 initrd.img-2.6.24-23-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 12:06 memtest86+.bin
-rw-r--r--  1 root root  899892 2008-04-10 18:51 System.map-2.6.24-16-generic
-rw-r--r--  1 root root  905170 2008-08-21 06:46 System.map-2.6.24-19-generic
-rw-r--r--  1 root root  905617 2008-10-22 05:12 System.map-2.6.24-21-generic
-rw-r--r--  1 root root  905617 2008-11-24 23:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root  905633 2008-11-27 23:13 System.map-2.6.24-23-generic
-rw-r--r--  1 root root 1904248 2008-04-10 18:51 vmlinuz-2.6.24-16-generic
-rw-r--r--  1 root root 1921464 2008-08-21 06:46 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 1920760 2008-10-22 05:12 vmlinuz-2.6.24-21-generic
-rw-r--r--  1 root root 1921176 2008-11-24 23:47 vmlinuz-2.6.24-22-generic
-rw-r--r--  1 root root 1921976 2008-11-27 23:13 vmlinuz-2.6.24-23-generic

sda6/boot/grub

insgesamt 212
drwxr-xr-x 2 root root   4096 2008-12-21 19:17 .
drwxr-xr-x 3 root root   4096 2008-12-17 20:48 ..
-rw-r--r-- 1 root root    197 2008-12-21 19:17 default
-rw-r--r-- 1 root root     30 2008-07-01 01:39 device.map
-rw-r--r-- 1 root root   8056 2008-12-21 19:17 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-12-21 19:17 fat_stage1_5
-rw-r--r-- 1 root root     18 2008-12-21 19:17 installed-version
-rw-r--r-- 1 root root   8608 2008-12-21 19:17 jfs_stage1_5
-rw-r--r-- 1 root root   6308 2008-12-17 20:48 menu.lst
-rw-r--r-- 1 root root   5876 2008-12-17 20:48 menu.lst~
-rw-r--r-- 1 root root   7324 2008-12-21 19:17 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-12-21 19:17 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-21 19:17 stage1
-rw-r--r-- 1 root root 108356 2008-12-21 19:17 stage2
-rw-r--r-- 1 root root   9276 2008-12-21 19:17 xfs_stage1_5

StdErr Messages 

Unknown BootLoader  on /dev/sda5

00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 7e 00 00 00  |........?...~...|
00000020  00 00 00 00 80 00 80 00  a7 f7 df 01 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  7a ff 1d 00 00 00 00 00  |........z.......|
00000040  f6 00 00 00 01 00 00 00  0d 76 0a 18 8e 0a 18 8e  |.........v......|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on /dev/sdc1

00000000  eb 58 90 6d 6b 64 6f 73  66 73 00 00 02 20 20 00  |.X.mkdosfs...  .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  82 d6 42 25 e3 53 02 00  00 00 00 00 02 00 00 00  |..B%.S..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 01 29 f4 e2 b6 47 4d  79 20 42 6f 6f 6b 20 20  |..)...GMy Book  |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Warnung: erweiterte Partition beginnt nicht an einer Zylindergrenze
DOS und Linux werden den Inhalt unterschiedlich interpretieren.
Warnung: erweiterte Partition beginnt nicht an einer Zylindergrenze
DOS und Linux werden den Inhalt unterschiedlich interpretieren.
Warnung: erweiterte Partition beginnt nicht an einer Zylindergrenze
DOS und Linux werden den Inhalt unterschiedlich interpretieren.

---

### Post by caljohnsmith on 2008-12-21
So you can boot OK into Ubuntu, true? How about doing the following:
```
gksudo gedit /boot/grub/menu.lst
```
And replace your current Vista entry with:
```
title Windows Vista
rootnoverify (hd0,1)
chainloader +1
```
Reboot, select "Windows Vista" from your Grub menu, and please let me know exactly what happens.

---

### Post by Sweet666 on 2008-12-21
sorry but if i run the command you told me, ubunto begin to load something 
and then nothing happens ????

but if looked into my menu.lst, there is a entry like your`s

---

### Post by getRandomName() on 2008-12-21
Sweet666 is on Kubuntu and thus doesn't have gedit installed.

Use this command instead:
```
kdesu kwrite /boot/grub/menu.lst
```
or:
```
sudo nano /boot/grub/menu.lst
```

---

### Post by TeXtonyx on 2008-12-21
> **Sweet666 said:**
> sorry but if i run the command you told me, ubunto begin to load something 
and then nothing happens ????

but if looked into my menu.lst, there is a entry like your`s

--------------

Grub is installed in the MBR of /dev/sda and looks on the 
same drive in partition #6 for its boot files.
Windows is installed in the MBR of /dev/sdb
Windows is installed in the MBR of /dev/sdc

Gerät boot. Anfang Ende Blöcke Id System
/dev/sdb1 63 488392064 244196001 f W95 Erw. (LBA)
/dev/sdb5 126 488392064 244195969+ 83 Linux


Gerät boot. Anfang Ende Blöcke Id System
/dev/sdc1 63 625137344 312568641 c W95 FAT32 (LBA)
/dev/sda1: UUID="96B67ED5B67EB4F9" LABEL="WinRE" TYPE="ntfs"
/dev/sda2: UUID="C204813304812B8B" LABEL="SYSTEM" TYPE="ntfs"
/dev/sda5: UUID="8E180A8E180A760D" LABEL="XP" TYPE="ntfs" 


------------------------------------------

My diagnosis would be that sdb1 and sdc1 need one of those bootable *
next to them.

caljohnsmith: This script that you and meierfra put together
is a very impressive piece of work. I'm just testing my theory
against what you will say, you are very authoritative in this
grubby area :-) People keep posting the script rather than the result!

---

### Post by caljohnsmith on 2008-12-21
> **Sweet666 said:**
> sorry but if i run the command you told me, ubunto begin to load something 
and then nothing happens ????

but if looked into my menu.lst, there is a entry like your`s
How about first opening a terminal in Ubuntu (Applications > Accessories > Terminal) and then copy/paste the "gksudo gedit /boot/grub/menu.lst" command into the terminal. If that doesn't work, please copy/paste the error it gives you and post it back here.

---

### Post by caljohnsmith on 2008-12-21
> **TeXtonyx said:**
> 
caljohnsmith: This script that you and meierfra put together
is a very impressive piece of work. I'm just testing my theory
against what you will say, you are very authoritative in this
grubby area :-) People keep posting the script rather than the result!
Yes, meierfra changed the boot_info_script.txt just today so that the new results file is called "RESULTS.txt" rather than "boot_info_results.txt", which is too easily mixed up with the script it seems. Meierfra deserves 100% credit for the script; I've given him some suggestions of what I thought would be good to include, but writing the bash script is 100% his effort. I think the script sure makes troubleshooting Grub and other booting problems so much easier to figure out. Thanks for the kind words though, I'll be sure to pass them along to meierfra. :)

---

### Post by Sweet666 on 2008-12-22
I've done what you told me to do and it changes nothing, I still have the same error message:
"Error 11: unrecognised device string"

---

### Post by TeXtonyx on 2008-12-22
> **Sweet666 said:**
> I've done what you told me to do and it changes nothing, I still have the same error message:
"Error 11: unrecognised device string"

He wants you to provide information about your system and
is then going to diagnose what is wrong, and then make
suggestions about fixing your problem. You have to follow
his responses to your posts. Nobody yet has told you anything
to do to fix your system yet, only requests for information,
that once you get, you copy and paste to this forum in a post.

---

### Post by Sweet666 on 2008-12-22
> **TeXtonyx said:**
> He wants you to provide information about your system and
is then going to diagnose what is wrong, and then make
suggestions about fixing your problem. You have to follow
his responses to your posts. Nobody yet has told you anything
to do to fix your system yet, only requests for information,
that once you get, you copy and paste to this forum in a post.

He told me to change something and then to reboot.
The thing with vista.
Maybe I am an idiot, but that's what I understood.
I entered the sudo code and then I changed the windows vista, I rebooted and I had the same error message.

---

### Post by Sweet666 on 2008-12-22
> **caljohnsmith said:**
> How about first opening a terminal in Ubuntu (Applications > Accessories > Terminal) and then copy/paste the "gksudo gedit /boot/grub/menu.lst" command into the terminal. If that doesn't work, please copy/paste the error it gives you and post it back here.


I made this in a terminal but nothing happens, I have no error message. The first time he asks my password but nothing happens after entering it.
Then I tried again and I think that he tries to open something but he doesn't succeed.

---

### Post by caljohnsmith on 2008-12-22
OK, how about posting the output of the following commands:
```
cat /boot/grub/menu.lst
sudo apt-get purge grub
sudo apt-get install grub
sudo grub-install --recheck /dev/sda
```
After that reboot, and let me know if anything changes.

---

### Post by Sweet666 on 2008-12-22
It changes nothing, still the same problem

---

### Post by Sweet666 on 2008-12-22
Here is the output:


$ sudo apt-get purge grub
[sudo] password for anna:
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut
Reading state information... Fertig
Die folgenden Pakete werden ENTFERNT:
  grub*
0 aktualisiert, 0 neu installiert, 1 zu entfernen und 0 nicht aktualisiert.
After this operation, 856kB disk space will be freed.
Möchten Sie fortfahren [J/n]? j
(Lese Datenbank ... 152382 Dateien und Verzeichnisse sind derzeit installiert.)
Entferne grub ...
Lösche Konfigurationsdateien von grub ...

---

### Post by Sweet666 on 2008-12-22
> **caljohnsmith said:**
> OK, how about posting the output of the following commands:
```
cat /boot/grub/menu.lst
sudo apt-get purge grub
sudo apt-get install grub
sudo grub-install --recheck /dev/sda
```
After that reboot, and let me know if anything changes.

Here comes everything:



$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title           Ubuntu 8.04.2, kernel 2.6.24-23-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-23-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro quiet splash
initrd          /boot/initrd.img-2.6.24-23-generic
quiet

title           Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-23-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro single
initrd          /boot/initrd.img-2.6.24-23-generic

title           Ubuntu 8.04.2, kernel 2.6.24-22-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-22-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro quiet splash
initrd          /boot/initrd.img-2.6.24-22-generic
quiet

title           Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-22-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro single
initrd          /boot/initrd.img-2.6.24-22-generic

title           Ubuntu 8.04.2, kernel 2.6.24-21-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro quiet splash
initrd          /boot/initrd.img-2.6.24-21-generic
quiet

title           Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-21-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro single
initrd          /boot/initrd.img-2.6.24-21-generic

title           Ubuntu 8.04.2, kernel 2.6.24-19-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.2, kernel 2.6.24-16-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=d04ffdf6-d533-4f24-8366-02d2a4079d3d ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04.2, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
rootnoverity            (hd0,1)
savedefault
makeactive
chainloader     +1




$ sudo apt-get install grub
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut
Reading state information... Fertig
Vorgeschlagene Pakete:
  grub-doc mdadm
Die folgenden NEUEN Pakete werden installiert:
  grub
0 aktualisiert, 1 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
Es müssen noch 0B von 386kB Archiven geholt werden.
After this operation, 856kB of additional disk space will be used.
Vorkonfiguration der Pakete ...
Wähle vormals abgewähltes Paket grub.
(Lese Datenbank ... 152336 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke grub (aus .../grub_0.97-29ubuntu21.1_i386.deb) ...
Richte grub ein (0.97-29ubuntu21.1) ...




$ sudo grub-install --recheck /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc

---

### Post by caljohnsmith on 2008-12-22
Please remove the "makeactive" and "savedefault" lines from your Vista entry, as given from my post #6. Also, do you get any Grub errors when you boot Ubuntu from the Grub menu?

---

### Post by Sweet666 on 2008-12-22
I've done what you told me to do, it changes nothing.
I have no error when starting ubuntu only with windows

---

### Post by caljohnsmith on 2008-12-22
OK, while you are in your Ubuntu install do:
```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo update-grub
```
And say yes to create a new menu.lst. After it is done, do:
```
gksudo gedit /boot/grub/menu.lst
```
And if it has an entry for Vista, change it to what I previously gave, or if it doesn't have a Vista entry simply add the one I gave. Then reboot, and let me know exactly what happens when you try to boot Vista from the Grub menu.

---

### Post by Sweet666 on 2008-12-22
```
gksudo gedit /boot/grub/menu.lst
```


this one doesn't works.

I've done the rest, now I can't chose any more.
Grub doesn't let me any choice any more, it just starts ubuntu

---

### Post by lowtolerance on 2008-12-22
My guess is you guys are barking up the wrong tree here. The same thing happened to me a couple of weeks ago, and it turned out that I accidentally installed grub over my vista bootloader, so when grub tries to load that it fails. Are you able to mount the windows drive from linux? If linux sees it as corrupted, this could very well be why. I solved the problem by popping in the restore disk for Vista, and told it to fix start up issues.

---

### Post by meierfra. on 2008-12-23
> rootnoveri[COLOR="Red"]t[/COLOR]y (hd0,1)


You had a typo:  it needs to by rootnoveri[COLOR="Red"]f[/COLOR]y

(the t needed to be an f)

> [QUOTE]gksudo gedit /boot/grub/menu.lst

this one doesn't works.[/QUOTE]

Do you get a blank file?   Any error messages?  Check your spelling:  

```
 gksudo gedit /boot/grub/menu.lst
```

(lst is short for list)

Replace your current Windows item by

title Windows Vista/Longhorn (loader)
rootnoverify (hd0,1)
chainloader +1

Don't retype this. Use copy and paste.


> Grub doesn't let me any choice any more, it just starts ubuntu
Look for the line 

"timeout 3" in menu.lst and change it to "timeout 10"

also 

change

"hiddenmenu" to "#hiddenmenu"

---

### Post by getRandomName() on 2008-12-23
> **Sweet666 said:**
> ```
gksudo gedit /boot/grub/menu.lst
```


this one doesn't works.

I've done the rest, now I can't chose any more.
Grub doesn't let me any choice any more, it just starts ubuntu

Please read again the post [#8]("http://ubuntuforums.org/showpost.php?p=6413518&postcount=8").

---

### Post by Sweet666 on 2008-12-30
Hello Meierfra,

I've done what you told me to do,now I can choose again thanks, but my windows still doesn't works

---

