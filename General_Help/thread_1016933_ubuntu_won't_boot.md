---
title: "ubuntu won't boot"
date: 2008-12-20
forum: General Help
---

### Post by 2handband on 2008-12-20
After spending the better part of two days configuring my Intrepid install on my new computer to my liking, I decided to install Fedora 10 on another partition. The Fedora installer gave me the option to use Ubuntu as my default boot, which I accepted. But now when I try to boot to Ubuntu I get the following: 

"error 13: invalid or unsupported executable format"

What does this mean??? Is there a way to get Ubuntu back short of a clean install?

---

### Post by oilchangeguy on 2008-12-20
> **2handband said:**
> After spending the better part of two days configuring my Intrepid install on my new computer to my liking, I decided to install Fedora 10 on another partition. The Fedora installer gave me the option to use Ubuntu as my default boot, which I accepted. But now when I try to boot to Ubuntu I get the following: 

"error 13: invalid or unsupported executable format"

What does this mean??? Is there a way to get Ubuntu back short of a clean install?

google is your friend:
[http://www.google.com/search?q=error+13%3A+invalid+or+unsupported+executable+format&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=error+13%3A+invalid+or+unsupported+executable+format&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by 2handband on 2008-12-20
I've already been thru there and haven't seen anything that applied to my specific situation. Please understand I'm pretty new at this.

---

### Post by caljohnsmith on 2008-12-20
Hi 2handband, nice to bump into you again. :) How about downloading and running the following script in order to clarify your new setup:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "boot_info_results.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

---

### Post by 2handband on 2008-12-20
Hey there John! I got back the following:

"-bash: cd: /root/Desktop: No such file or directory"

I'm working in Fedora here (which I am completely unfamiliar with) because my Ubuntu won't load. Don't know how much difference that makes.

---

### Post by caljohnsmith on 2008-12-20
OK, how about right-clicking this link for the [boot_info_script.txt]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") file, choose "save target as", and save that file to your Fedora desktop. Then do:
```
su -
cd /home/gene/Desktop
bash boot_info_script.txt
```
If for some reason that doesn't work, please copy/paste your terminal session where you run all those commands so I can get an idea of what might be wrong.

---

### Post by 2handband on 2008-12-20
The file copied to my desktop no prolem. However I got the following cli output:

"[root@gene ~]# cd /home/gene
[root@gene gene]# bash boot_info_script.txt
bash: boot_info_script.txt: No such file or directory"

---

### Post by caljohnsmith on 2008-12-20
I'm sorry, that was all ready my brain slippage I see; I corrected my last post, so please try again.

---

### Post by 2handband on 2008-12-20
No prob, I should have caught that one myself. Here's the file (it's big):

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
    Message=$( echo is installed in the MBR of  $drive)
    case $(hexdump   -n  2 -e '/1 "%x"'  $drive) in
	eb48) BL=Grub
              dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $drive);
              offset=$(hexdump -s 0x44 -n 4 -e '"%d"' $drive);
              if  [ $offset != 1 ];
	      then
                  pa=-1
                  for hdd in $Hard_Drives;
		  do
		      tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump    -n 4 -e '"%x"');
                      if [ $tmp = 3be5652 ]; then
                      pa=$(dd if=$hdd skip=$((offset+1)) count=1 2>>$Trash | hexdump  -s 0xa  -n 1 -e '"%d"');
                      stage2_hdd=$hdd
                      fi;
                  done;
                  let dr-127
                  Message=$(echo $Message and looks at sector $offset)         
                  if [ $dr = 128 ];
                      then
                          Message=$(echo $Message of the same hard drive) 
                      else
                           Message=$(echo $Message on boot drive \#$dr)
		  fi;
                    Message=$(echo $Message for the stage2 file.);
                    
                        if [ $pa = -1  ]
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
          case $(hexdump  -s 0x80 -n  2 -e '/1 "%x"'  $part) in
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
                      if [ $tmp = 3be5652 ]; then
                      pa=$(dd if=$hdd skip=$((offset+1)) count=1 2>>$Trash | hexdump  -s 0xa  -n 1 -e '"%d"');
                      stage2_hdd=$hdd
                      fi;
                  done;
                  dr=$((dr-127))
                  BSI=$(echo $BSI Grub is installed to the boot sector of $part and looks at sector $offset )        
                  if [ $dr = 128 ];
                      then
                          BSI=$(echo $BSI of the same hard drive) 
                      else
                          BSI=$(echo $BSI on boot drive \#$dr)
		  fi;
                  BSI=$(echo $BSI for the stage2 file.);
                    
                        if [ $pa = -1  ]
		     then
		        BSI=$(echo $BSI, but no stage2 files can be found at this location); 
                     else
                       pa=$((pa+1))
                       BSI=$(echo $BSI  \(a  stage2 file is  at this location on $stage2_hdd\)  and on )                       
                        if [ $pa = 256 ];
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
               *) BST=Unknown;;
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

### Post by caljohnsmith on 2008-12-20
Actually, that was the "boot_info_[COLOR="Red"]script[/COLOR].txt" that you posted; please post the contents of the "boot_info_[COLOR="Red"]results[/COLOR].txt" file. :)

---

### Post by 2handband on 2008-12-20
Oops...


Grub is installed in the MBR of /dev/sda and looks at sector 399806587 of the same hard drive for the stage2 file., but no stage2 files can be found at this location
No known boot loader is installed in the MBR of /dev/sdb

sda1:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Ubuntu 8.10 \n \l
    Boot files/directories present:  /boot/grub/menu.lst /boot /boot/grub

sda2:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: 
    Boot files/directories present: 

sda3:
    File system:  ext3
    Boot sector  type:  Unknown
    Boot sector  info:  
    Operating System: Fedora release 10 (Cambridge) Kernel \r on an \m (\l)
    Boot files/directories present:  /boot/grub/menu.lst /boot/grub/grub.conf /boot /boot/grub


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x87c675e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    58589054    29294496   83  Linux
/dev/sda2        58589055   371085434   156248190   83  Linux
/dev/sda3       371085435   432517994    30716280   83  Linux
/dev/sda1: UUID="3538b7d3-8970-4e8b-91a7-64cc39de4dca" TYPE="ext3" 
/dev/sda2: UUID="ed245138-5562-4c88-abad-a4bc1f254d6d" TYPE="ext3" 
/dev/sda3: LABEL="/" UUID="8d6465b7-dda8-4a57-91e4-2a3aedb2d814" TYPE="ext3" 
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 58588992, Id=83, bootable
/dev/sda2 : start= 58589055, size=312496380, Id=83
/dev/sda3 : start=371085435, size= 61432560, Id=83
/dev/sda4 : start=        0, size=        0, Id= 0

sda1/boot/grub/menu.lst

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
timeout		3

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
# kopt=root=UUID=3538b7d3-8970-4e8b-91a7-64cc39de4dca ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3538b7d3-8970-4e8b-91a7-64cc39de4dca

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

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		3538b7d3-8970-4e8b-91a7-64cc39de4dca
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=3538b7d3-8970-4e8b-91a7-64cc39de4dca ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		3538b7d3-8970-4e8b-91a7-64cc39de4dca
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=3538b7d3-8970-4e8b-91a7-64cc39de4dca ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		3538b7d3-8970-4e8b-91a7-64cc39de4dca
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3538b7d3-8970-4e8b-91a7-64cc39de4dca ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		3538b7d3-8970-4e8b-91a7-64cc39de4dca
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3538b7d3-8970-4e8b-91a7-64cc39de4dca ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		3538b7d3-8970-4e8b-91a7-64cc39de4dca
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

sda1/boot

total 25532
drwxr-xr-x  3 root root    4096 2008-12-18 20:40 .
drwxr-xr-x 21 root root    4096 2008-12-18 21:00 ..
-rw-r--r--  1 root root  503560 2008-11-04 14:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 17:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 14:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 17:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-18 20:39 grub
-rw-r--r--  1 root root 8673518 2008-12-18 20:39 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8673447 2008-12-18 20:40 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 15:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 14:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 17:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 14:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 17:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 14:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 17:30 vmlinuz-2.6.27-9-generic

sda1/boot/grub

total 224
drwxr-xr-x 2 root root   4096 2008-12-18 20:39 .
drwxr-xr-x 3 root root   4096 2008-12-18 20:40 ..
-rw-r--r-- 1 root root    197 2008-12-18 20:03 default
-rw-r--r-- 1 root root     15 2008-12-18 20:03 device.map
-rw-r--r-- 1 root root   8108 2008-12-18 20:03 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2008-12-18 20:03 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-12-18 20:03 installed-version
-rw-r--r-- 1 root root   8712 2008-12-18 20:03 jfs_stage1_5
-rw-r--r-- 1 root root   4792 2008-12-18 20:39 menu.lst
-rw-r--r-- 1 root root   4708 2008-12-18 20:39 menu.lst~
-rw-r--r-- 1 root root   7352 2008-12-18 20:03 minix_stage1_5
-rw-r--r-- 1 root root   9756 2008-12-18 20:03 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-12-18 20:03 stage1
-rw-r--r-- 1 root root 121460 2008-12-18 20:03 stage2
-rw-r--r-- 1 root root   9556 2008-12-18 20:03 xfs_stage1_5

sda3/boot/grub/menu.lst

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,2)
#          kernel /boot/vmlinuz-version ro root=/dev/sda3
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=1
timeout=5
splashimage=(hd0,2)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.27.7-134.fc10.x86_64)
	root (hd0,2)
	kernel /boot/vmlinuz-2.6.27.7-134.fc10.x86_64 ro root=UUID=8d6465b7-dda8-4a57-91e4-2a3aedb2d814 rhgb quiet
	initrd /boot/initrd-2.6.27.7-134.fc10.x86_64.img

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		3538b7d3-8970-4e8b-91a7-64cc39de4dca
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=3538b7d3-8970-4e8b-91a7-64cc39de4dca ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

sda3/boot/grub/grub.conf

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,2)
#          kernel /boot/vmlinuz-version ro root=/dev/sda3
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=1
timeout=5
splashimage=(hd0,2)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.27.7-134.fc10.x86_64)
	root (hd0,2)
	kernel /boot/vmlinuz-2.6.27.7-134.fc10.x86_64 ro root=UUID=8d6465b7-dda8-4a57-91e4-2a3aedb2d814 rhgb quiet
	initrd /boot/initrd-2.6.27.7-134.fc10.x86_64.img

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		3538b7d3-8970-4e8b-91a7-64cc39de4dca
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=3538b7d3-8970-4e8b-91a7-64cc39de4dca ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

sda3/boot

total 7404
drwxr-xr-x  4 root root    4096 2008-12-20 12:18 .
drwxr-xr-x 23 root root    4096 2008-12-20 14:27 ..
-rw-r--r--  1 root root   85054 2008-12-01 21:33 config-2.6.27.7-134.fc10.x86_64
drwxr-xr-x  3 root root    4096 2008-12-20 12:12 efi
drwxr-xr-x  2 root root    4096 2008-12-20 14:25 grub
-rw-------  1 root root 3404046 2008-12-20 12:18 initrd-2.6.27.7-134.fc10.x86_64.img
-rw-r--r--  1 root root 1406414 2008-12-01 21:33 System.map-2.6.27.7-134.fc10.x86_64
-rwxr-xr-x  1 root root 2638112 2008-12-01 21:33 vmlinuz-2.6.27.7-134.fc10.x86_64

sda3/boot/grub

total 312
drwxr-xr-x 2 root root   4096 2008-12-20 14:25 .
drwxr-xr-x 4 root root   4096 2008-12-20 12:18 ..
-rw-r--r-- 1 root root     63 2008-12-20 12:45 device.map
-rw-r--r-- 1 root root  11736 2008-12-20 12:45 e2fs_stage1_5
-rw-r--r-- 1 root root  11512 2008-12-20 12:45 fat_stage1_5
-rw-r--r-- 1 root root  10744 2008-12-20 12:45 ffs_stage1_5
-rw------- 1 root root    903 2008-12-20 14:25 grub.conf
-rw------- 1 root root    715 2008-12-20 12:45 grub.conf~
-rw-r--r-- 1 root root  10736 2008-12-20 12:45 iso9660_stage1_5
-rw-r--r-- 1 root root  12328 2008-12-20 12:45 jfs_stage1_5
lrwxrwxrwx 1 root root     11 2008-12-20 12:45 menu.lst -> ./grub.conf
-rw-r--r-- 1 root root  10968 2008-12-20 12:45 minix_stage1_5
-rw-r--r-- 1 root root  13360 2008-12-20 12:45 reiserfs_stage1_5
-rw-r--r-- 1 root root  40685 2008-10-24 09:40 splash.xpm.gz
-rw-r--r-- 1 root root    512 2008-12-20 12:45 stage1
-rw-r--r-- 1 root root 111020 2008-12-20 12:45 stage2
-rw-r--r-- 1 root root  11008 2008-12-20 12:45 ufs2_stage1_5
-rw-r--r-- 1 root root  10344 2008-12-20 12:45 vstafs_stage1_5
-rw-r--r-- 1 root root  12984 2008-12-20 12:45 xfs_stage1_5

StdErr Messages 

Unknown MBR on /dev/sdb


boot_info_script.txt: line 124: [: =: unary operator expected
hexdump: /dev/sdb: No medium found
hexdump: /dev/sdb: Bad file descriptor
hexdump: /dev/sdb: No medium found
hexdump: /dev/sdb: Bad file descriptor
/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading

---

### Post by caljohnsmith on 2008-12-20
OK, let me first make sure I understand correctly: when you boot up, you get the Fedora Grub menu, but when you choose "Ubuntu 8.10, kernel 2.6.27-9-generic" from the menu, you get a Grub error 13? If so, how about doing the following, and please post the output of the Grub commands:
```
su -
grub
grub> root (hd0,0)
grub> setup (hd0,0)
grub> quit
gedit /boot/grub/menu.lst
```
Then change the "Ubuntu 8.10, kernel 2.6.27-9-generic" entry to instead be:
```
title Ubuntu 8.10 Grub Menu
root (hd0,0)
chainloader +1
```
Reboot, try the new "Ubuntu 8.10 Grub Menu" entry in the Fedora menu, and it should give you the Ubuntu Grub menu where you can boot Ubuntu. Or if the Fedora Grub menu is unchanged, then boot back into Fedora and instead do:
```
su - 
gedit /boot/grub/grub.conf
```
And replace the Ubuntu entry with the one above. Please let me know though if you have to modify the grub.conf file to get it to work.

---

### Post by 2handband on 2008-12-20
I try that shortly... just now I have to go pick my wife up from work. Here's a thought... I'm planning to put Kubuntu on a third partition. What will happen if I do that?

---

### Post by caljohnsmith on 2008-12-20
> **2handband said:**
> I try that shortly... just now I have to go pick my wife up from work. Here's a thought... I'm planning to put Kubuntu on a third partition. What will happen if I do that?
Actually, since you all ready have Ubuntu installed, it is easy to install the equivalent of Kubuntu inside of Ubuntu; just do the following (once you are able to boot into Ubuntu):
```
sudo apt-get install kubuntu-desktop
```
And then when you go to login to Ubuntu, you can select which desktop to use: Gnome (Ubuntu) or KDE (Kubuntu). I would recommend that rather than giving Kubuntu a whole partition for itself, but it's up to you.

---

### Post by 2handband on 2008-12-20
Okay, I changed the code as per your instructions. Now when I reboot I get a sort of limited command line that looks like this

grub>

I'm not sure what to do with that.

Thanks for the advice regarding Kubuntu. The reason I asked is because I was wondering if doing that install would fix the grub menu.

---

### Post by caljohnsmith on 2008-12-20
OK, while you are in the Grub command line on start up, try:
```
grub> root (hd0,0)
grub> chainloader +1
grub> boot
```
And if your previous Grub command were successful, doing the above should get you the Ubuntu Grub menu. If that allows you to boot into Ubuntu, then please post:
```
sudo mount /dev/sda3 /mnt
cat /mnt/boot/grub/menu.lst
cat /mnt/boot/grub/grub.conf
```

---

### Post by 2handband on 2008-12-20
Here's the output. I'm going to try that reboot now. Back in a moment...



grub
Probing devices to guess BIOS drives. This may take a long time.


    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename.]
grub> root (hd0,0)
root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
grub> setup (hd0,0)
setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/grub.conf "... succeeded
Done.
grub> quit
quit

---

### Post by 2handband on 2008-12-20
after I do the "boot" command i get the following two lines:

starting up
grub loading stage 2

after that it just goes back to the command line and doesn't do anything.

---

### Post by caljohnsmith on 2008-12-20
I'm sure I'm missing something again, because the Grub commands from your post #17 show that your sda1 partition uses a "grub.conf" file instead of a "menu.lst" file. Did you run those commands while you were in Fedora I assume? I think that has to be the issue. Ubuntu is on sda1, correct? How about booting your Ubuntu Live CD, and from there do:
```
sudo grub
grub> root (hd0,2)
grub> blocklist /boot/grub/stage2
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
And please post the output of all the above commands. That will give your Ubuntu sda1 partition control of Grub on start up, so you should get the Ubuntu Grub menu instead of the Fedora Grub menu. How about trying that and let me know what happens.

---

### Post by 2handband on 2008-12-20
Okay, I'm on the live CD and just put in those commands. Here is the output:

"ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit"

I will now attempt the restart.

---

### Post by 2handband on 2008-12-20
Okay, Ubuntu is badk in business! Only now the grub menu does not give me the option to get into Fedora. Any way I can fix that?

---

### Post by caljohnsmith on 2008-12-20
> **2handband said:**
> Okay, Ubuntu is badk in business! Only now the grub menu does not give me the option to get into Fedora. Any way I can fix that?
OK, please first post the output of:
```
sudo grub
grub> root (hd0,2)
grub> blocklist /boot/grub/stage2
grub> quit
```
And then open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And at the bottom add:
```
title Fedora Grub Menu
configfile (hd0,2)/boot/grub/menu.lst
```
Reboot, select the "Fedora Grub Menu" entry, and let me know if that works OK.

---

### Post by 2handband on 2008-12-20
Here's that output:

"gene@gene-laptop:~$ sudo grub
[sudo] password for gene: 
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,2)
root (hd0,2)
grub> blocklist /boot/grub/stage2
blocklist /boot/grub/stage2
(hd0,2)28721152+96,28721256+121
grub> quit
quit"

reooting now

---

### Post by 2handband on 2008-12-20
That worked. That's the 2nd time in as many days you've saved my butt. If we're ever in the same neck of the woods I'll buy you a drink. By the way, was this problem caused by something I did wrong on the Fedora install?

---

### Post by caljohnsmith on 2008-12-20
> **2handband said:**
> That worked. That's the 2nd time in as many days you've saved my butt. If we're ever in the same neck of the woods I'll buy you a drink. By the way, was this problem caused by something I did wrong on the Fedora install?
I'm really glad to hear that worked. It wasn't really your fault about doing something wrong with the Fedora install; truthfully I don't know why you were getting that Grub error 13 when booting Ubuntu from the Fedora Grub menu. I'll have to look over all the results that you posted more carefully, because I'm still curious why you would get that error. 

In order to avoid problems in the future though, just keep in mind that when you install a new distro, usually the distro installs its boot loader to the MBR (Master Boot Record) of the HDD by default, and thus takes over the booting process. I would recommend letting Ubuntu stay in charge of your booting process right now since it works; if you install another distro, just specify to have its boot loader installed to the boot sector of the partition you are installing it to, instead of the MBR. In Ubuntu you can do that by clicking the "advanced" button near the end of the installation, and have Grub installed to say /dev/sda1 if sda1 is where you are installing Ubuntu to. 

Anyway, cheers and have fun with all your distros. :)

---

### Post by 2handband on 2008-12-20
Actually I'm in the installer looking at that option right now. Install bootloader is checked, device for bootloader installation is (hd0), everything else is blank. What do I change to keep my original ubuntu partition as default? Do I change the bootloader device to /dev/sda1?

---

### Post by caljohnsmith on 2008-12-20
There should be an option in that dialog box to install Grub to a partition like /dev/sda5 or whichever partition you are installing Grub to. I think it will look like:


[IMG]http://www.herman.linuxmaniac.net/p23/035..png[/IMG]


So you would click the drop-down box to select the partition. Which distro are you installing right now and to which partition? Just install Grub to the same partition as the new distro.

---

### Post by 2handband on 2008-12-20
The box on mine isn't a drop-down, just an ordinary box. Otherwise my screen is identical to your screenshot. I'm putting Kubuntu on sda5. I decided to do the seperate install because I tried adding kde to my hardy installation a couple weeks back and it messed up a bunch of stuff (for instance it wiped my install of OOo 3 and reinstalled 2.4).

---

### Post by TeXtonyx on 2008-12-20
It would be a lot more convenient if you could install grub to
/boot partition at this step by clicking on that little down arrow.

But if not and you decide to install to the MBR, then
you can put it back into the /boot partition

grub-install /dev/sdxx
(where sdxx is your root partition, such as sda1, sda2, etc.)

So if you just installed Debian (for instance) and it went 
to sda7, then you would type grub-install /dev/sda7

Then of course you have to reinstall your Ubuntu grub back to 
the MBR, which is all and all a bit of a pita, so it's so
much easier to do it at Step 7 Advanced. 

 ________________________
|(hd0) ......................                       |_*_|<--little drop down arrow, far right
|________________________        click to access dropdown menu

If this doesn't work this way in Kubuntu then its a bug.

---

### Post by 2handband on 2008-12-20
There's definitely no dropdown in kubuntu. I couldhowever manually typein what I want. Should it just be /boot?

---

### Post by TeXtonyx on 2008-12-20
I haven't had to do it this way.
Hmmm, try /boot and see if it works.
I'm not sure of the input format: /boot , (hd0,3) or sda4 ?

Maybe it works with sda4 = (hd0,3)
Do you what partition kubuntu will install to?
It's going to be the same partition you install grub to.

sda5 = (hd0,4)
sda6 = (hd0,5)
sda7 = (hd0,6)
and so on.

---

### Post by caljohnsmith on 2008-12-21
> **2handband said:**
> There's definitely no dropdown in kubuntu. I couldhowever manually typein what I want. Should it just be /boot?
Try just typing in /dev/sda5 if that is your new Kubuntu partition. If it won't let you do that, go ahead and let Kubuntu install to the MBR and we can restore Grub back to Ubuntu afterwards.

---

### Post by 2handband on 2008-12-22
Okay, in the last 24 hours I've gone through the whole series of installs again using default settings only, just in the interest of science to see what would happen. The only differences are the Fedora is now on sda1, Ubuntu is on sda3, and I ditched Kubuntu (since I'm starting from scratch I can put the KDE option on my Ubuntu install without fear of messing up my setup) and put Ubuntu server 8.10 on sda4. sda2 is still my data partition. My conclusion is this: for some reason the grub installers for Ubuntu and Fedora do not recognize each other. I can't be the only person who has this problem but I haven't seen anything about it online. My question is this: is it a Fedora problem (I suspect it probably is) or is it an Ubuntu problem? Who do I send a bug report to?

I installed Ubuntu last so it currently has control of the grub. I a now going to see if I understand the procedure John gave me well enough to get Fedora into the grub menu. I'll let you know...

---

### Post by 2handband on 2008-12-22
Success! I think I even understand what I did and why. John, you're awesome.

---

### Post by caljohnsmith on 2008-12-22
> **2handband said:**
> Success! I think I even understand what I did and why. John, you're awesome.
That's great news you have it working and you're getting the hang of it. I hope you don't run into any other major problems, but if you do, you can always come back to the forums and ask for assistance, and we'll do our best to help you. :)

---

