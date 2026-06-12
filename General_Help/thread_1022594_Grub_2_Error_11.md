---
title: "Grub 2 Error 11"
date: 2008-12-27
forum: General Help
---

### Post by ocajublinky on 2008-12-27
So I in one of my fits of "EVERYTHING MUST BE NEW" upgraded to GRUB 2, now I can't boot into Ubuntu because it says:

Error 11: unrecognized device string

something to that effect, I can obtain a commandline with "Minimal bash-line editing support" so I believe if any of you command wizards out there can conjure me a command to revert to the older grub, I should be in good shape, however, if I am completely wrong, go ahead tell what else to do

in your Mercy

-Ocajublinky

---

### Post by obsrv on 2008-12-27
Can you copy-paste the grub conf? It may be problem with mapping drives.

---

### Post by caljohnsmith on 2008-12-27
If you have internet access from your Live CD, you could set up a chroot environment, chroot into your Ubuntu installation, and then uninstall Grub2 and finally reinstall Legacy Grub. But first, in order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what it will take to reinstall legacy Grub.

---

### Post by ocajublinky on 2008-12-28
#!/bin/bash
#to use this script:
#
#sudo bash boot_info_script.txt
#
#date  12/27/08
#author  meierfra.  (with lots of input from caljohnsmith)
# 
#Looks at all MBRs and identifies the boot loader. 
#   For Grub and Supergrub:  displays the controlling partition.
#   If the  MBR is unknown, displays the whole MBR.
#Looks at all  partitions:
#   Determines their type
#          For ntfs and some fats displays the offset of the partition
#            as recorded  in  the boot sector (no booting fats
#            seems to use 0 as the offset)
#   Identifies their boot sectors.
#         For grub: displays the controlling partition and the offset
#         of the stage2 file as recorded in the boot sector.
#   Identifies the operating system
#   Lists  boot programs.
#   Displays "fdisk -lu
#   Displays "blkid -c /dev/null"
#   Displays "sfdisk -V"
#   Finds  boot directories and displays their contents.
#   Looks in "/" and "NST" for  bootpart codes  and displays the offset
#                and boot drive it is trying to chainload
#   Looks on "/" and "/NST" for stage1 files and displays the offset
#         and bootdrive of the stage 2  files is trying to chainload.
#    displays  boot configuration files.
#All information is written to the file "RESULTS.txt" in the
#    same folder as the script
#
#To do:
#   Information should be displayed in a nicer format.
#   Extract info from BCD? Possible? 
#   List offsets of some boot files (for Grub error 18)
#   Boot sector info for grub is confusing.
#   Examine the  NTFS boot sector more closely to see whether
#     testdisk "RebuildBS" needs to be run.
#   Test the script on different distros.
#   Use command line options, to choose what information to display.
#   On vfat partition "ntldr" and "ntdetect.com" are 
#       list in all lowercase and in all caps
#   Fat partition used for booting seem to record
#        the offset in the same place as NTFS partition. But
#        needs to be examined more closely.
#   Rewrite the whole script. Use functions instead of copying and pasting 
#         whole blocks of codes. Add comments.  

Boot_Codes_Dir="
    /
    /NST/
    "

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
    /NST/menu.lst
    /menu.lst
    /ubuntu/disks/boot/grub/menu.lst
    /ubuntu/disks/install/boot/grub/menu.lst
    /boot/grub/grub.conf
    /grub/grub.conf
    /grub.conf
    /boot.ini
    /etc/fstab
    "


## "titlebar_gen" generates the $name$file title bar to always be either 79 or 80 chars total in length:
titlebar_gen () {
		name_file="$1$2:"; name_file_length=${#name_file}
		equal_signs_line_length=$(((80-name_file_length)/2-1)); equal_signs_line=""
		for length in $(seq $equal_signs_line_length); do
  			equal_signs_line='='$equal_signs_line
		done
		echo "$equal_signs_line $name_file $equal_signs_line" >> $Log1; }

Dir=$(cd $(dirname $0);pwd);

LogFile=$Dir/RESULTS
while ( [ -e $LogFile$j.txt ] )
    do  
      ((j++))
      wait;
    done
LogFile=$LogFile$j.txt



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


All_Hard_Drives=$(ls /dev/hd? /dev/sd? 2>>$Trash );

echo '============================= Boot Info Summary: =============================='; echo
for drive in  $All_Hard_Drives;
do
        size=$(sfdisk -s $drive);        
        if [ 0 -lt $size 2>>$Trash ];
	then
	 Hard_Drives=$Hard_Drives" "$drive; 
        else
          echo " => Drive $(basename $drive) does not have a valid partition table."
    fi;
done;

for drive in $Hard_Drives;
  do 
    Message=$(echo is installed in the MBR of $drive)
    case $(hexdump -v -n  2 -e '/1 "%x"' $drive) in
	eb48) BL=Grub
             dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $drive);
             offset=$(hexdump -s 0x44 -n 4 -e '"%u"' $drive);
              if  [ "$offset" != 1 ];
	      then
                  pa=-1
                  for hdd in $Hard_Drives;
		  do
                      if [[ $offset -lt $((2*$(sfdisk -s $hdd))) ]]
			      then
		      tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump    -n 4 -e '"%x"');
                      if [ "$tmp" = 3be5652 ]; then
                      pa=$(dd if=$hdd skip=$((offset+1)) count=1 2>>$Trash | hexdump  -s 0xa  -n 1 -e '"%d"');
                      stage2_hdd=$hdd
                      fi;
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
                    Message=$(echo $Message for the stage2 file);
                    
                        if [ "$pa" = -1  ]
		     then
		         Message=$(echo $Message, but no stage2 files can be found at this location); 
                     else
                       pa=$((pa+1))
                        Message=$(echo $Message \(a stage2 file is at this location on $stage2_hdd\) and on)
                        if [ $pa = 256 ];
                        then
                            Message=$(echo $Message the same partition) 
                        else
                           Message=$(echo $Message partition \#$pa) 
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
                Message=$(echo $Message and looks on the same drive in partition \#$pa for its boot files.)
              else
               Message=$(echo $Message and looks  on boot drive \#$dr in partition \#$pa for its boot files.)
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
        ##Output message at beginning of summary that gives MBR info for each drive:
        echo -n " => "
        echo "$BL $Message" | fold -s -w 75 | sed -e '2~1s/.*/    &/'   
 
    done
    echo;

for drive in $Hard_Drives;
 do
for part  in  $(ls $drive?* 2>>$Trash)
   do
      BSI=""      
      part_number=${part:8}
      part_type=$(sfdisk -c $drive $part_number)
      name=$(basename $part);
      echo $name: _________________________________________________________________________; echo
      mkdir $name 
      type=$( /lib/udev/vol_id -t $part 2>$Tmp_Log );
      if [ $part_type = 5 ] || [ $part_type = f ] && [ "$type" = "" ] ;
         then
	 type="Extended Partition";
	 cat $Tmp_Log>>$Trash;
	 else
         cat $Tmp_Log>>$Error_Log
      fi;
      echo "    File system:       "$type;
      if [ "$type" != "swap" ]  && [ "$type" != "Extended Partition"  ] && [ "$type" != "unknown volume type" ] && [ "$type" != "LVM2_member" ]  ;
       then 

          Bytes8081=$(hexdump -v -s 0x80 -n  2 -e '/1 "%x"'  $part)
          case $Bytes8081  in
             8cd) BST="Windows XP";;
            b6d1) BST="Windows XP: Fat32";;
            fa33) BST="Windows XP";;
	    55aa) BST="Windows Vista";;           
	    5272) BST=Grub;
                  offset=$(hexdump -s 0x44 -n 4 -e '4 "%u"' $part 2>>$Trash);
                  dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $part);
                  pa=-1
                  for hdd in $Hard_Drives;
		  do
                      if [ $offset -lt  $((2*$(sfdisk -s $hdd))) ];
			      then
		      tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump    -n 4 -e '"%x"');
                      if [ "$tmp" = 3be5652 ]; then
                      pa=$(dd if=$hdd skip=$((offset+1)) count=1 2>>$Trash | hexdump  -s 0xa  -n 1 -e '"%d"');
                      stage2_hdd=$hdd
                      fi;
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
                  BSI=$(echo $BSI for the stage2 file);
                    
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
	    7815) BST=Fat32;;
            6f74) BST=Fat32;;
            696e) BST=Fat16;;
            6616) BST=Fat16;;
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
           if [[ "$type" = "ntfs"  ||   "$Bytes8081" = "7cc6" ||  "$Bytes8081" = "7815"  ||  "$Bytes8081" = "B6D1"   ]] ;
         then
         offset=$(hexdump -s 0x1c -n 4 -e '"%d\n"' $part);
         BSI=$(echo  According to the info in the boot sector, $name starts at sector $offset.)   
      fi;


            echo "    Boot sector type:  "$BST
       if  mount $part $name 2>$Mount_Error; then
       OS=""
       [ -e $name"/Windows/System32/config/BCD-Template" ] ||  [ -e $name"/windows/system32/config/bcd-template" ] || [ -e $name"/WINDOWS/System32/config/BCD-Template" ] ||
  [ -e $name"/WINDOWS/system32/config/BCD-Template" ] && OS="Windows Vista"

       [ -e $name"/Windows/System32/config/SecEvent.Evt" ] ||  [ -e $name"/WINDOWS/system32/config/SecEvent.Evt" ] || [ -e $name"/WINDOWS/system32/config/secevent.evt" ] || [ -e $name"/windows/system32/config/secevent.evt" ] && OS="Windows XP"
  
       [ -e $name"/etc" ] && OS=$(cat $name/etc/issue) && OS=${OS%%\\*}
     

       BootFiles=""
       for file in $Boot_Files;
       do
           if [ -f $name$file ];
              then BootFiles=$(echo $BootFiles"  "$file);
	      echo >> $Log1
              titlebar_gen $name $file	##generates a titlebar above each file/dir listed
              echo >> $Log1
              if ! [ -h $name$file ];
              then
                 cat $name$file >> $Log1;
              fi;
	   fi;
       done;

       for file in $Boot_Prog;
       do
           if [ -f $name$file ];
              then BootFiles=$(echo $BootFiles"  "$file);          
	   fi;
       done;


       for file in $Boot_Dir;
       do
          if [ -d $name$file ];
          then
	      BootFiles=$(echo $BootFiles"  "$file); 
	      echo >> $Log1
              titlebar_gen $name $file	##generates a titlebar above each file/dir listed
              echo >> $Log1
              ls -la  $name$file >> $Log1 ; 
             
	  fi;
       done;

       for file in $Boot_Codes_Dir
       do
	   if [ -d $name$file ];
	   then  
		  for loader in $( ls  $name$file );
		  do
                   if [ -f $name$file$loader ];
		   then		     
                      sig=$(hexdump -s 0x101 -n 8  -e '8/1 "%_p"' $name$file$loader)
                      if [ "$sig"  = "BootPart" ]
			  then
                          offset=$(hexdump -s 0xf1 -n 4 -e '"%d"' $name$file$loader);
                              dr=$(hexdump -s 0x6f -n 1 -e '"%d"' $name$file$loader);
			      dr=$((dr -127))
 			  BSI=$(echo $BSI "  "BootPart in the file $file$loader is trying to chain load sector \#$offset on boot drive \#$dr);
		       fi;
		      sig=$(hexdump -s 0x17f -n 4  -e '4/1 "%_p"' $name$file$loader)
                      if [ "$sig"  = "GRUB" ];
                      then
                          offset=$(hexdump -s 0x44 -n 4 -e '4 "%u"' $name$file$loader 2>>$Trash);
                          dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $name$file$loader);
                          pa=-1
                          for hdd in $Hard_Drives;
		          do
                             if [ $offset -lt  $((2*$(sfdisk -s $hdd))) ];
			     then
		                  tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump    -n 4 -e '"%x"');
                                  if [ "$tmp" = 3be5652 ];
                                  then
                                      pa=$(dd if=$hdd skip=$((offset+1)) count=1 2>>$Trash | hexdump  -s 0xa  -n 1 -e '"%d"');
                                       stage2_hdd=$hdd
                                   fi;
		              fi;
                           done;
                           dr=$((dr-127))
                            BSI=$(echo $BSI Grub in the file $file$loader  looks at sector $offset )        
                           if [ "$dr" = 128 ];
                           then
                                BSI=$(echo $BSI of the same hard drive) 
                           else
                                BSI=$(echo $BSI on boot drive \#$dr)
		           fi;
                           BSI=$(echo $BSI for the stage2 file);
                    
                           if [ "$pa" = T  ]
		           then
		                BSI=$(echo $BSI, but no stage2 files can be found at this location); 
                           else
                                 pa=$((pa+1))
                                 BSI=$(echo $BSI  \(a stage2 file is at this location on $stage2_hdd\)  and on )                       
                                 if [ "$pa" = 256 ];
                                 then
                                     BSI=$(echo $BSI the same partition) 
                                 else
                                       BSI=$(echo $BSI partition \#$pa )
	                         fi;
                                 BSI=$(echo $BSI for menu.lst.)
                            fi;
                         fi;
 		       fi;
		  done;
              fi;
           done
 
      echo -n "    Boot sector info:  "
      echo $BSI | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'
      echo "    Operating System:  "$OS
      echo -n "    Boot files/dirs:   "
      echo $BootFiles | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'
     
     umount $name || umount -l $name; 
     else
     echo "    Mounting failed:  ";  
     cat   $Mount_Error;
     fi;
     fi;
     echo;
 
     done;
     done;

echo '=========================== Drive/Partition Info: ============================='; echo
for drive in $All_Hard_Drives;
 do
     echo "Drive $(basename $drive): _____________________________________________________________________"
     echo
     echo "fdisk -lu $drive:"
     fdisk -lu $drive;
     echo;
     echo "sfdisk -V $drive:"; echo
     sfdisk -V $drive 2>&1
     echo   
 done
echo "blkid -c /dev/null: ____________________________________________________________"; echo
blkid -c /dev/null
echo;
echo '=============================== "mount" output: ==============================='; echo
mount
echo >> $Log1
echo "=============================== StdErr Messages: ===============================">>$Log1
echo >> $Log1
cat $Log1
[ -e $Unknown_MBR ] && cat $Unknown_MBR
[ -s $Error_Log ] && cat $Error_Log || echo "No errors were reported."
chown $(basename ~) $LogFile
exec 1>&-
exec 1>&6
exec 6>&-
echo Finished. The results are in the file $(basename $LogFile) located in $Dir

---

### Post by caljohnsmith on 2008-12-28
Please post the results in the "RESULTS.txt" file on your desktop, not the contents of the boot_info_script.txt. :)

---

### Post by ocajublinky on 2008-12-28
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for its boot files.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda6: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf9d10e91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    83907494    41953716    7  HPFS/NTFS
/dev/sda2        83907495   312576704   114334605    5  Extended
/dev/sda5        83907558   303194744   109643593+  83  Linux
/dev/sda6       303194808   312576704     4690948+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

/dev/sda: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="3480FFB86C85C2FC" TYPE="ntfs" 
/dev/sda5: UUID="582383bb-acc1-4098-85ed-3fbe9dc52b9d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="e3a4ed3f-d85e-4a34-9563-3a9fd7e36c3e" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

================================ sda1/boot.ini: ================================

[boot loader]

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS



[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=582383bb-acc1-4098-85ed-3fbe9dc52b9d

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
##      altoptions=(single-user) single
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

title		Chainload into GRUB 2
root		582383bb-acc1-4098-85ed-3fbe9dc52b9d
kernel		/boot/grub/core.img

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
		
title		When you have verified GRUB 2 works, you can use this command to
root

title		complete the upgrade:  upgrade-from-grub-legacy
root

title		ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title		Debian GNU/Linux, kernel 2.6.27-9-generic
root		582383bb-acc1-4098-85ed-3fbe9dc52b9d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro quiet splash
initrd		/boot/initrd.img-2.6.27-9-generic

title		Debian GNU/Linux, kernel 2.6.27-9-generic (recovery mode)
root		582383bb-acc1-4098-85ed-3fbe9dc52b9d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Debian GNU/Linux, kernel 2.6.27-7-generic
root		582383bb-acc1-4098-85ed-3fbe9dc52b9d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic

title		Debian GNU/Linux, kernel 2.6.27-7-generic (recovery mode)
root		582383bb-acc1-4098-85ed-3fbe9dc52b9d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Debian GNU/Linux, kernel memtest86+
root		582383bb-acc1-4098-85ed-3fbe9dc52b9d
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=e3a4ed3f-d85e-4a34-9563-3a9fd7e36c3e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda5/boot: ==================================

total 23772
drwxr-xr-x  3 root root    4096 2008-12-18 23:18 .
drwxr-xr-x 20 root root    4096 2008-12-24 07:35 ..
-rw-r--r--  1 root root  507665 2008-11-04 21:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 23:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   91364 2008-11-04 21:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 23:46 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2008-12-24 08:44 grub
-rw-r--r--  1 root root 8185934 2008-12-18 23:17 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8185353 2008-12-18 23:18 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-11-04 21:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 23:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 21:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 23:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2244464 2008-11-04 21:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 23:46 vmlinuz-2.6.27-9-generic

=============================== sda5/boot/grub: ===============================

total 840
drwxr-xr-x 2 root root   4096 2008-12-24 08:44 .
drwxr-xr-x 3 root root   4096 2008-12-18 23:18 ..
-rw-r--r-- 1 root root   2236 2008-12-24 08:44 acorn.mod
-rw-r--r-- 1 root root   4876 2008-12-24 08:44 affs.mod
-rw-r--r-- 1 root root   6808 2008-12-24 08:44 afs.mod
-rw-r--r-- 1 root root   2612 2008-12-24 08:44 amiga.mod
-rw-r--r-- 1 root root   1144 2008-12-24 08:44 aout.mod
-rw-r--r-- 1 root root   2680 2008-12-24 08:44 apple.mod
-rw-r--r-- 1 root root   4724 2008-12-24 08:44 ata.mod
-rw-r--r-- 1 root root   4300 2008-12-24 08:44 biosdisk.mod
-rw-r--r-- 1 root root   2568 2008-12-24 08:44 bitmap.mod
-rw-r--r-- 1 root root   2248 2008-12-24 08:44 blocklist.mod
-rw-r--r-- 1 root root    512 2008-12-24 08:44 boot.img
-rw-r--r-- 1 root root   1456 2008-12-24 08:44 boot.mod
-rw-r--r-- 1 root root   8756 2008-12-24 08:44 _bsd.mod
-rw-r--r-- 1 root root   2324 2008-12-24 08:44 bsd.mod
-rw-r--r-- 1 root root   2076 2008-12-24 08:44 cat.mod
-rw-r--r-- 1 root root    512 2008-12-24 08:44 cdboot.img
-rw-r--r-- 1 root root   2508 2008-12-24 08:44 _chain.mod
-rw-r--r-- 1 root root   1816 2008-12-24 08:44 chain.mod
-rw-r--r-- 1 root root   2312 2008-12-24 08:44 cmp.mod
-rw-r--r-- 1 root root    713 2008-12-24 08:44 command.lst
-rw-r--r-- 1 root root   1908 2008-12-24 08:44 configfile.mod
-rw-r--r-- 1 root root  28746 2008-12-24 08:44 core.img
-rw-r--r-- 1 root root   3208 2008-12-24 08:44 cpio.mod
-rw-r--r-- 1 root root   1588 2008-12-24 08:44 cpuid.mod
-rw-r--r-- 1 root root    197 2008-12-18 01:21 default
-rw-r--r-- 1 root root     15 2008-12-24 08:44 device.map
-rw-r--r-- 1 root root    512 2008-12-24 08:44 diskboot.img
-rw-r--r-- 1 root root   8108 2008-12-18 01:21 e2fs_stage1_5
-rw-r--r-- 1 root root   2096 2008-12-24 08:44 echo.mod
-rw-r--r-- 1 root root   4484 2008-12-24 08:44 elf.mod
-rw-r--r-- 1 root root   4352 2008-12-24 08:44 ext2.mod
-rw-r--r-- 1 root root   4972 2008-12-24 08:44 fat.mod
-rw-r--r-- 1 root root   7856 2008-12-18 01:21 fat_stage1_5
-rw-r--r-- 1 root root   2716 2008-12-24 08:44 font.mod
-rw-r--r-- 1 root root   2564 2008-12-24 08:44 fshelp.mod
-rw-r--r-- 1 root root     83 2008-12-24 08:44 fs.lst
-rw-r--r-- 1 root root   8548 2008-12-24 08:44 gfxterm.mod
-rw-r--r-- 1 root root   2896 2008-12-24 08:44 gpt.mod
-r--r--r-- 1 root root   1860 2008-12-24 08:44 grub.cfg
-rw-r--r-- 1 root root   7860 2008-12-24 08:44 gzio.mod
-rw-r--r-- 1 root root   1632 2008-12-24 08:44 halt.mod
-rw-r--r-- 1 root root   1384 2008-12-24 08:44 hello.mod
-rw-r--r-- 1 root root   2084 2008-12-24 08:44 help.mod
-rw-r--r-- 1 root root   3104 2008-12-24 08:44 hexdump.mod
-rw-r--r-- 1 root root   6348 2008-12-24 08:44 hfs.mod
-rw-r--r-- 1 root root   6432 2008-12-24 08:44 hfsplus.mod
-rw-r--r-- 1 root root     16 2008-12-18 01:21 installed-version
-rw-r--r-- 1 root root   5576 2008-12-24 08:44 iso9660.mod
-rw-r--r-- 1 root root   5208 2008-12-24 08:44 jfs.mod
-rw-r--r-- 1 root root   8712 2008-12-18 01:21 jfs_stage1_5
-rw-r--r-- 1 root root   6568 2008-12-24 08:44 jpeg.mod
-rw-r--r-- 1 root root  30924 2008-12-24 08:44 kernel.img
-rw-r--r-- 1 root root   4872 2008-12-24 08:44 _linux.mod
-rw-r--r-- 1 root root   1576 2008-12-24 08:44 linux.mod
-rw-r--r-- 1 root root   1024 2008-12-24 08:44 lnxboot.img
-rw-r--r-- 1 root root   3156 2008-12-24 08:44 loopback.mod
-rw-r--r-- 1 root root   3928 2008-12-24 08:44 ls.mod
-rw-r--r-- 1 root root   4236 2008-12-24 08:44 lspci.mod
-rw-r--r-- 1 root root   5424 2008-12-24 08:44 lvm.mod
-rw-r--r-- 1 root root   2216 2008-12-24 08:44 memdisk.mod
-rw-r--r-- 1 root root   5531 2008-12-24 08:44 menu.lst
-rw-r--r-- 1 root root   5103 2008-12-24 08:44 menu.lst~
-rw-r--r-- 1 root root   5103 2008-12-24 08:44 menu.lst_backup_by_grub2_postinst
-rw-r--r-- 1 root root   4344 2008-12-24 08:44 minix.mod
-rw-r--r-- 1 root root   7352 2008-12-18 01:21 minix_stage1_5
-rw-r--r-- 1 root root    990 2008-12-24 08:44 moddep.lst
-rw-r--r-- 1 root root  11924 2008-12-24 08:44 _multiboot.mod
-rw-r--r-- 1 root root   1660 2008-12-24 08:44 multiboot.mod
-rw-r--r-- 1 root root  41436 2008-12-24 08:44 normal.mod
-rw-r--r-- 1 root root   3400 2008-12-24 08:44 ntfscomp.mod
-rw-r--r-- 1 root root   8600 2008-12-24 08:44 ntfs.mod
-rw-r--r-- 1 root root     29 2008-12-24 08:44 partmap.lst
-rw-r--r-- 1 root root    936 2008-12-24 08:44 pci.mod
-rw-r--r-- 1 root root   3328 2008-12-24 08:44 pc.mod
-rw-r--r-- 1 root root   2292 2008-12-24 08:44 play.mod
-rw-r--r-- 1 root root   6576 2008-12-24 08:44 png.mod
-rw-r--r-- 1 root root   1024 2008-12-24 08:44 pxeboot.img
-rw-r--r-- 1 root root   5192 2008-12-24 08:44 raid.mod
-rw-r--r-- 1 root root   1784 2008-12-24 08:44 read.mod
-rw-r--r-- 1 root root   1372 2008-12-24 08:44 reboot.mod
-rw-r--r-- 1 root root   9760 2008-12-24 08:44 reiserfs.mod
-rw-r--r-- 1 root root   9756 2008-12-18 01:21 reiserfs_stage1_5
-rw-r--r-- 1 root root   3272 2008-12-24 08:44 search.mod
-rw-r--r-- 1 root root   5588 2008-12-24 08:44 serial.mod
-rw-r--r-- 1 root root   4484 2008-12-24 08:44 sfs.mod
-rw-r--r-- 1 root root   2300 2008-12-24 08:44 sleep.mod
-rw-r--r-- 1 root root    512 2008-12-18 01:21 stage1
-rw-r--r-- 1 root root 121460 2008-12-18 01:21 stage2
-rw-r--r-- 1 root root   2632 2008-12-24 08:44 sun.mod
-rw-r--r-- 1 root root   1980 2008-12-24 08:44 terminal.mod
-rw-r--r-- 1 root root  10040 2008-12-24 08:44 terminfo.mod
-rw-r--r-- 1 root root   1664 2008-12-24 08:44 test.mod
-rw-r--r-- 1 root root   2960 2008-12-24 08:44 tga.mod
-rw-r--r-- 1 root root   5028 2008-12-24 08:44 udf.mod
-rw-r--r-- 1 root root   5128 2008-12-24 08:44 ufs.mod
-rw-r--r-- 1 root root   2292 2008-12-24 08:44 vbeinfo.mod
-rw-r--r-- 1 root root  14084 2008-12-24 08:44 vbe.mod
-rw-r--r-- 1 root root   3172 2008-12-24 08:44 vbetest.mod
-rw-r--r-- 1 root root   3944 2008-12-24 08:44 vga.mod
-rw-r--r-- 1 root root   4084 2008-12-24 08:44 video.mod
-rw-r--r-- 1 root root   2884 2008-12-24 08:44 videotest.mod
-rw-r--r-- 1 root root   6624 2008-12-24 08:44 xfs.mod
-rw-r--r-- 1 root root   9556 2008-12-18 01:21 xfs_stage1_5

=============================== StdErr Messages: ===============================

No errors were reported.

---

### Post by caljohnsmith on 2008-12-28
OK, from your Live CD try:
```
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
apt-get purge grub2
apt-get install grub
```
If the above commands complete succesfully (they assume you have internet access from the Live CD), continue with:
```
mv /boot/grub/menu.lst /boot
rm -fr /boot/grub
grub-install /dev/sda
update-grub
cat /boot/grub/menu.lst
exit
```
And after running the update-grub command, type "y" to create a new menu.lst. Please post the output of all the above commands, and if they successfully complete, reboot and let me know how far you get.

---

### Post by ocajublinky on 2008-12-28
ubuntu@ubuntu:~$ cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
--2008-12-28 17:51:28--  [http://home.comcast.net/~ubuntu_grub/boot_info_script.txt](http://home.comcast.net/~ubuntu_grub/boot_info_script.txt)
Resolving home.comcast.net... 216.87.188.9
Connecting to home.comcast.net|216.87.188.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17625 (17K) [text/plain]
Saving to: `boot_info_script.txt'

100%[======================================>] 17,625      62.8K/s   in 0.3s    

2008-12-28 17:51:28 (62.8 KB/s) - `boot_info_script.txt' saved [17625/17625]

Finished. The results are in the file RESULTS.txt located in /home/ubuntu/Desktop
ubuntu@ubuntu:~/Desktop$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~/Desktop$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~/Desktop$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~/Desktop$ cudo chroot /mnt
^[[A^[[Abash: cudo: command not found
ubuntu@ubuntu:~/Desktop$ sudo chroot /mnt
root@ubuntu:/# apt-get purge grub2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub2*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 94.2kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 129603 files and directories currently installed.)
Removing grub2 ...
Purging configuration files for grub2 ...
root@ubuntu:/# apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-doc mdadm
The following packages will be REMOVED:
  grub-pc
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 1 to remove and 1 not upgraded.
Need to get 402kB of archives.
After this operation, 1851kB disk space will be freed.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main grub 0.97-29ubuntu45
  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub/grub_0.97-29ubuntu45_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub/grub_0.97-29ubuntu45_i386.deb)  Could not resolve 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@ubuntu:/# mv /boot/grub/menu.lst /boot
root@ubuntu:/# rm -fr /boot/grub
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
root@ubuntu:/# update-grub
Updating /boot/grub/grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.27-9-generic
Found initrd image: /boot/initrd.img-2.6.27-9-generic
Found linux image: /boot/vmlinuz-2.6.27-7-generic
Found initrd image: /boot/initrd.img-2.6.27-7-generic
Found memtest86+ image: /boot/memtest86+.bin
done
root@ubuntu:/# cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
root@ubuntu:/# exit
exit

---

### Post by ocajublinky on 2008-12-28
It was succesful, I am now greeting you from my original installation. thank you.

Is there a way I make your rating go up? because it says like times thanked and I would like to know how to do that formally.

---

### Post by ocajublinky on 2008-12-28
wait never mind I think i figured it out, thanks again

---

### Post by caljohnsmith on 2008-12-28
You're welcome, I'm glad that seemed to work; but according to the output you posted, installing the legacy Grub package was not successful because of a DNS problem where your networking could not resolve the Ubuntu repository site host name. I thought that might happen, and we could have fixed that by copying over the /etc/resolv.conf file before you did the chroot command. But since you are in Ubuntu now, please check your Grub version by posting the output of the following commands:
```
apt-cache policy grub
ls -l /boot/grub
cat /boot/grub/grub.cfg
```

---

### Post by ocajublinky on 2008-12-28
Hey wait now I can't boot into windows xp,

Did i mention I am dual booting lol

---

### Post by ocajublinky on 2008-12-28
pierce@Xerxestririme:~$ apt-cache policy grub
grub:
  Installed: (none)
  Candidate: 0.97-29ubuntu45
  Version table:
     0.97-29ubuntu45 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status
pierce@Xerxestririme:~$ ls -l /boot/grub
total 612
-rw-r--r-- 1 root root  2236 2008-12-28 10:15 acorn.mod
-rw-r--r-- 1 root root  4876 2008-12-28 10:15 affs.mod
-rw-r--r-- 1 root root  6808 2008-12-28 10:15 afs.mod
-rw-r--r-- 1 root root  2612 2008-12-28 10:15 amiga.mod
-rw-r--r-- 1 root root  1144 2008-12-28 10:15 aout.mod
-rw-r--r-- 1 root root  2680 2008-12-28 10:15 apple.mod
-rw-r--r-- 1 root root  4724 2008-12-28 10:15 ata.mod
-rw-r--r-- 1 root root  4300 2008-12-28 10:15 biosdisk.mod
-rw-r--r-- 1 root root  2568 2008-12-28 10:15 bitmap.mod
-rw-r--r-- 1 root root  2248 2008-12-28 10:15 blocklist.mod
-rw-r--r-- 1 root root   512 2008-12-28 10:15 boot.img
-rw-r--r-- 1 root root  1456 2008-12-28 10:15 boot.mod
-rw-r--r-- 1 root root  8756 2008-12-28 10:15 _bsd.mod
-rw-r--r-- 1 root root  2324 2008-12-28 10:15 bsd.mod
-rw-r--r-- 1 root root  2076 2008-12-28 10:15 cat.mod
-rw-r--r-- 1 root root   512 2008-12-28 10:15 cdboot.img
-rw-r--r-- 1 root root  2508 2008-12-28 10:15 _chain.mod
-rw-r--r-- 1 root root  1816 2008-12-28 10:15 chain.mod
-rw-r--r-- 1 root root  2312 2008-12-28 10:15 cmp.mod
-rw-r--r-- 1 root root   713 2008-12-28 10:15 command.lst
-rw-r--r-- 1 root root  1908 2008-12-28 10:15 configfile.mod
-rw-r--r-- 1 root root 28746 2008-12-28 10:15 core.img
-rw-r--r-- 1 root root  3208 2008-12-28 10:15 cpio.mod
-rw-r--r-- 1 root root  1588 2008-12-28 10:15 cpuid.mod
-rw-r--r-- 1 root root    15 2008-12-28 10:15 device.map
-rw-r--r-- 1 root root   512 2008-12-28 10:15 diskboot.img
-rw-r--r-- 1 root root  2096 2008-12-28 10:15 echo.mod
-rw-r--r-- 1 root root  4484 2008-12-28 10:15 elf.mod
-rw-r--r-- 1 root root  4352 2008-12-28 10:15 ext2.mod
-rw-r--r-- 1 root root  4972 2008-12-28 10:15 fat.mod
-rw-r--r-- 1 root root  2716 2008-12-28 10:15 font.mod
-rw-r--r-- 1 root root  2564 2008-12-28 10:15 fshelp.mod
-rw-r--r-- 1 root root    83 2008-12-28 10:15 fs.lst
-rw-r--r-- 1 root root  8548 2008-12-28 10:15 gfxterm.mod
-rw-r--r-- 1 root root  2896 2008-12-28 10:15 gpt.mod
-r--r--r-- 1 root root  1761 2008-12-28 10:16 grub.cfg
-rw-r--r-- 1 root root  7860 2008-12-28 10:15 gzio.mod
-rw-r--r-- 1 root root  1632 2008-12-28 10:15 halt.mod
-rw-r--r-- 1 root root  1384 2008-12-28 10:15 hello.mod
-rw-r--r-- 1 root root  2084 2008-12-28 10:15 help.mod
-rw-r--r-- 1 root root  3104 2008-12-28 10:15 hexdump.mod
-rw-r--r-- 1 root root  6348 2008-12-28 10:15 hfs.mod
-rw-r--r-- 1 root root  6432 2008-12-28 10:15 hfsplus.mod
-rw-r--r-- 1 root root  5576 2008-12-28 10:15 iso9660.mod
-rw-r--r-- 1 root root  5208 2008-12-28 10:15 jfs.mod
-rw-r--r-- 1 root root  6568 2008-12-28 10:15 jpeg.mod
-rw-r--r-- 1 root root 30924 2008-12-28 10:15 kernel.img
-rw-r--r-- 1 root root  4872 2008-12-28 10:15 _linux.mod
-rw-r--r-- 1 root root  1576 2008-12-28 10:15 linux.mod
-rw-r--r-- 1 root root  1024 2008-12-28 10:15 lnxboot.img
-rw-r--r-- 1 root root  3156 2008-12-28 10:15 loopback.mod
-rw-r--r-- 1 root root  3928 2008-12-28 10:15 ls.mod
-rw-r--r-- 1 root root  4236 2008-12-28 10:15 lspci.mod
-rw-r--r-- 1 root root  5424 2008-12-28 10:15 lvm.mod
-rw-r--r-- 1 root root  2216 2008-12-28 10:15 memdisk.mod
-rw-r--r-- 1 root root  4344 2008-12-28 10:15 minix.mod
-rw-r--r-- 1 root root   990 2008-12-28 10:15 moddep.lst
-rw-r--r-- 1 root root 11924 2008-12-28 10:15 _multiboot.mod
-rw-r--r-- 1 root root  1660 2008-12-28 10:15 multiboot.mod
-rw-r--r-- 1 root root 41436 2008-12-28 10:15 normal.mod
-rw-r--r-- 1 root root  3400 2008-12-28 10:15 ntfscomp.mod
-rw-r--r-- 1 root root  8600 2008-12-28 10:15 ntfs.mod
-rw-r--r-- 1 root root    29 2008-12-28 10:15 partmap.lst
-rw-r--r-- 1 root root   936 2008-12-28 10:15 pci.mod
-rw-r--r-- 1 root root  3328 2008-12-28 10:15 pc.mod
-rw-r--r-- 1 root root  2292 2008-12-28 10:15 play.mod
-rw-r--r-- 1 root root  6576 2008-12-28 10:15 png.mod
-rw-r--r-- 1 root root  1024 2008-12-28 10:15 pxeboot.img
-rw-r--r-- 1 root root  5192 2008-12-28 10:15 raid.mod
-rw-r--r-- 1 root root  1784 2008-12-28 10:15 read.mod
-rw-r--r-- 1 root root  1372 2008-12-28 10:15 reboot.mod
-rw-r--r-- 1 root root  9760 2008-12-28 10:15 reiserfs.mod
-rw-r--r-- 1 root root  3272 2008-12-28 10:15 search.mod
-rw-r--r-- 1 root root  5588 2008-12-28 10:15 serial.mod
-rw-r--r-- 1 root root  4484 2008-12-28 10:15 sfs.mod
-rw-r--r-- 1 root root  2300 2008-12-28 10:15 sleep.mod
-rw-r--r-- 1 root root  2632 2008-12-28 10:15 sun.mod
-rw-r--r-- 1 root root  1980 2008-12-28 10:15 terminal.mod
-rw-r--r-- 1 root root 10040 2008-12-28 10:15 terminfo.mod
-rw-r--r-- 1 root root  1664 2008-12-28 10:15 test.mod
-rw-r--r-- 1 root root  2960 2008-12-28 10:15 tga.mod
-rw-r--r-- 1 root root  5028 2008-12-28 10:15 udf.mod
-rw-r--r-- 1 root root  5128 2008-12-28 10:15 ufs.mod
-rw-r--r-- 1 root root  2292 2008-12-28 10:15 vbeinfo.mod
-rw-r--r-- 1 root root 14084 2008-12-28 10:15 vbe.mod
-rw-r--r-- 1 root root  3172 2008-12-28 10:15 vbetest.mod
-rw-r--r-- 1 root root  3944 2008-12-28 10:15 vga.mod
-rw-r--r-- 1 root root  4084 2008-12-28 10:15 video.mod
-rw-r--r-- 1 root root  2884 2008-12-28 10:15 videotest.mod
-rw-r--r-- 1 root root  6624 2008-12-28 10:15 xfs.mod
pierce@Xerxestririme:~$ cat /boot/grub/grub.cfg
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/update-grub using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=5
set root=(hd0,5)
if font (hd0,5)/usr/share/grub/unicode.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, linux 2.6.27-9-generic" {
	linux	(hd0,5)/boot/vmlinuz-2.6.27-9-generic root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro quiet splash 
	initrd	(hd0,5)/boot/initrd.img-2.6.27-9-generic
}
menuentry "Ubuntu, linux 2.6.27-9-generic (single-user mode)" {
	linux	(hd0,5)/boot/vmlinuz-2.6.27-9-generic root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro single
	initrd	(hd0,5)/boot/initrd.img-2.6.27-9-generic
}
menuentry "Ubuntu, linux 2.6.27-7-generic" {
	linux	(hd0,5)/boot/vmlinuz-2.6.27-7-generic root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro quiet splash 
	initrd	(hd0,5)/boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu, linux 2.6.27-7-generic (single-user mode)" {
	linux	(hd0,5)/boot/vmlinuz-2.6.27-7-generic root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro single
	initrd	(hd0,5)/boot/initrd.img-2.6.27-7-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux	(hd0,5)/boot/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###
pierce@Xerxestririme:~$

---

### Post by caljohnsmith on 2008-12-28
OK, try doing:
```
sudo apt-get purge grub-pc
sudo apt-get install grub
sudo rm -fr /boot/grub
sudo grub-install /dev/sda
sudo update-grub
cat /boot/grub/menu.lst
```
And say "y" to create a new menu.lst. Please post the output of all the above commands, and I would not recommend rebooting in the meantime until we are sure Grub is installed OK.

---

### Post by ocajublinky on 2008-12-28
pierce@Xerxestririme:~$ sudo apt-get purge grub-pc
[sudo] password for pierce: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grub-pc*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 2789kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 130776 files and directories currently installed.)
Removing grub-pc ...
Purging configuration files for grub-pc ...
Processing triggers for man-db ...
pierce@Xerxestririme:~$ sudo apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  liblzo2-2 os-prober grub-common
Use 'apt-get autoremove' to remove them.
Suggested packages:
  grub-doc mdadm
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 402kB of archives.
After this operation, 938kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main grub 0.97-29ubuntu45 [402kB]
Fetched 402kB in 5s (70.1kB/s)
Preconfiguring packages ...
Selecting previously deselected package grub.
(Reading database ... 130646 files and directories currently installed.)
Unpacking grub (from .../grub_0.97-29ubuntu45_i386.deb) ...
Processing triggers for man-db ...
Setting up grub (0.97-29ubuntu45) ...

pierce@Xerxestririme:~$ sudo rm -fr /boot/grub
pierce@Xerxestririme:~$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
pierce@Xerxestririme:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

pierce@Xerxestririme:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=582383bb-acc1-4098-85ed-3fbe9dc52b9d

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
uuid		582383bb-acc1-4098-85ed-3fbe9dc52b9d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		582383bb-acc1-4098-85ed-3fbe9dc52b9d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		582383bb-acc1-4098-85ed-3fbe9dc52b9d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		582383bb-acc1-4098-85ed-3fbe9dc52b9d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		582383bb-acc1-4098-85ed-3fbe9dc52b9d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
pierce@Xerxestririme:~$

---

### Post by caljohnsmith on 2008-12-28
Great, looks like installing Grub was successful this time. Next do:
```
gksudo gedit /boot/grub/menu.lst
```
And right now your Grub menu is set to be hidden on start up, so if you always want to see it, you can put a pound sign in front of the "hiddenmenu" line:
```
# hiddenmenu
```
And at the bottom of your menu.lst add:
```
title Windows XP
root (hd0,0)
chainloader +1
```
Then you should be all set, so go ahead and reboot and make sure you can boot into both Ubuntu and Windows.

---

### Post by ocajublinky on 2008-12-28
```
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
**_# hiddenmenu_**

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
# kopt=root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=582383bb-acc1-4098-85ed-3fbe9dc52b9d

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
uuid		582383bb-acc1-4098-85ed-3fbe9dc52b9d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		582383bb-acc1-4098-85ed-3fbe9dc52b9d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		582383bb-acc1-4098-85ed-3fbe9dc52b9d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		582383bb-acc1-4098-85ed-3fbe9dc52b9d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		582383bb-acc1-4098-85ed-3fbe9dc52b9d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

okay so Help me out here, The 3rd line down from the hidden menu part where i have bolded and underlined is where i put the "#" sign, and I am confused as to where to put the other thing, If you could post back this, when you have added the line, please bold it and underline it so I know where and how

---

### Post by caljohnsmith on 2008-12-28
```
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
**_# hiddenmenu_**

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
# kopt=root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=582383bb-acc1-4098-85ed-3fbe9dc52b9d

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
uuid		582383bb-acc1-4098-85ed-3fbe9dc52b9d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		582383bb-acc1-4098-85ed-3fbe9dc52b9d
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		582383bb-acc1-4098-85ed-3fbe9dc52b9d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		582383bb-acc1-4098-85ed-3fbe9dc52b9d
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=582383bb-acc1-4098-85ed-3fbe9dc52b9d ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		582383bb-acc1-4098-85ed-3fbe9dc52b9d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

[COLOR="Blue"]title Windows XP
root (hd0,0)
chainloader +1[/COLOR]

```
Just add the above text highlighted in blue and you should be OK. Let me know how it goes when you reboot.

---

### Post by ocajublinky on 2008-12-28
Thanks I think that did the trick

---

### Post by Slug71 on 2008-12-28
I did the same things as you by installing Grub2 a little while ago and got the same error. I just did a reinstall though.
In order to use Grub2 you need to change the boot menu list so that your devices start at 1 instead of 0 which is how Grub Legacy does it.

Trying to find a how-to now to try it again.

---

### Post by Slug71 on 2009-01-01
> **ocajublinky said:**
> So I in one of my fits of "EVERYTHING MUST BE NEW" upgraded to GRUB 2, now I can't boot into Ubuntu because it says:

Error 11: unrecognized device string

something to that effect, I can obtain a commandline with "Minimal bash-line editing support" so I believe if any of you command wizards out there can conjure me a command to revert to the older grub, I should be in good shape, however, if I am completely wrong, go ahead tell what else to do

in your Mercy

-Ocajublinky


I've been dealing with this same error trying to get Grub2 to work.
I got it when trying to chainload into grub2 and when that didnt work i scrolled down to the Kernel below and still got that damn error.

If you still want it, this did it for me.

Install grub2-(should be 3 files, Grub2, grub-pc and grub-common)
A 'Configuring grub-pc' box will pop-up during the installation.
Just leave it as is(my box under Linux command line was blank) and click 'Forward'.
Installation should finish. 
Then go to Terminal and run the following commands.

```
sudo update-grub2

sudo upgrade-from-grub-legacy

sudo update-grub
```

Reboot and it should work.
If youre dual booting with Windows or something then Windows won't be in the Grub menu when you reboot. 
After rebooting go to Terminal and enter

```
sudo apt-get install os-prober

sudo os-prober

sudo update-grub
```
And everything should work as it once did. After entering the code sudo os-prober you should see you windows partition show up.

---

### Post by Norm24 on 2009-01-17
> **Slug71 said:**
> I've been dealing with this same error trying to get Grub2 to work.
I got it when trying to chainload into grub2 and when that didnt work i scrolled down to the Kernel below and still got that damn error.

If you still want it, this did it for me.

Install grub2-(should be 3 files, Grub2, grub-pc and grub-common)
A 'Configuring grub-pc' box will pop-up during the installation.
Just leave it as is(my box under Linux command line was blank) and click 'Forward'.
Installation should finish. 
Then go to Terminal and run the following commands.

```
sudo update-grub2

sudo upgrade-from-grub-legacy

sudo update-grub
```

Reboot and it should work.
If youre dual booting with Windows or something then Windows won't be in the Grub menu when you reboot. 
After rebooting go to Terminal and enter

```
sudo apt-get install os-prober

sudo os-prober

sudo update-grub
```
And everything should work as it once did. After entering the code sudo os-prober you should see you windows partition show up.

Will this work for Ibex or this only for Jaunty?

As you know I've had my issues with Grub2 but would still like to give it a shot.

Nevermind.It worked!

Btw os-prober is part of the initial install so only the first three commands are necessary.

Mods:this procedure should be a sticky.Slug71 saved some many of us some serious BS.

---

### Post by jaithehulk on 2009-04-03
root@ubuntu:/# grub-install
The program 'grub-install' can be found in the following packages:
 * grub
 * grub-efi (You will have to enable component called 'universe')
 * grub-pc (You will have to enable component called 'universe')
Try: apt-get install <selected package>
bash: grub-install: command not found

I executed the**_ commands above _**"grub-install" perfectly!
now it says i dont have grub at all!!
pls help i cant boot untill i fix this!!!! HELP NEEDED BADLYY!
even right now talking to u guys from the LIVE CD..

and also even if i try to install grub2 it says no intallation candidate and pkg is replaced by grub-pc whic cannot be installed either!!!

---

### Post by bruno9779 on 2009-06-12
> **caljohnsmith said:**
> OK, from your Live CD try:
```
sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
apt-get purge grub2
apt-get install grub
```
If the above commands complete succesfully (they assume you have internet access from the Live CD), continue with:
```
mv /boot/grub/menu.lst /boot
rm -fr /boot/grub
grub-install /dev/sda
update-grub
cat /boot/grub/menu.lst
exit
```
And after running the update-grub command, type "y" to create a new menu.lst. Please post the output of all the above commands, and if they successfully complete, reboot and let me know how far you get.

I have followed this how-to to restore my grub after getting error 11 in grub2.

all is working now, but :
```
cat /boot/grub/menu.lst
```
says that menu.lst does not exist, and i have not been prompted for anything after ```
update-grub
```

As i said all seems to be working now, but i would like to know what i have done wrong and what the effects of this could be

---

### Post by thearkive on 2009-07-08
Hey, all first post. So I've been sitting on this problem for about a month, and finally decided to do something about it today. Then I stumbled onto this   [http://www.ubuntu-inside.me/2009/06/howto-upgrade-to-grub2-on-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/06/howto-upgrade-to-grub2-on-ubuntu-jaunty.html)     This part in particular was helpful > *There is a bug at Ubuntu Jaunty (ONLY JAUNTY, not Karmic Koala) where it modifies the existing grub configuration incorrectly.To fix it :  At the &quot;Chainload into Grub 2&quot; menu item, press 'e' to edit the configuration.Press 'e' a second time to edit the top boot line and change:  root xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx To uuid xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx Then press Enter and &quot;b&quot; to boot Grub2.that got me into my ubuntu partition, and then I used Slug71's commands to make it permanent. that's how I got it to work, anyway.

---

### Post by stalker145 on 2009-07-29
> **thearkive said:**
> Hey, all first post. So I've been sitting on this problem for about a month, and finally decided to do something about it today. Then I stumbled onto this   [http://www.ubuntu-inside.me/2009/06/howto-upgrade-to-grub2-on-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/06/howto-upgrade-to-grub2-on-ubuntu-jaunty.html)     This part in particular was helpful that got me into my ubuntu partition, and then I used Slug71's commands to make it permanent. that's how I got it to work, anyway.

Worked PERFECTLY!! Thank you, Thank you, Thank you, Thank you, Thank you!!

I almost had a seizure when I couldn't boot and then I found your post. No chroot'ing, no magic pixie dust. One change and it works fine after reboot.

Now where'd that doggone "thank you" button go?

---

### Post by b0z0n3 on 2009-08-07
Thanks alot, **caljohnsmith **I had the same problem after installing grub2 and your solution really helped me get it fixed quickly! :D

---

### Post by OnlyTim on 2009-08-19
Same here guys! After pulling my hair out for hours, this fixed it in a jiffy! Thanks

---

### Post by humaneasy on 2009-09-01
> **bruno9779 said:**
> I have followed this how-to to restore my grub after getting error 11 in grub2.

My problem is that I have the same issue BUT my structure is as follows:

[INDENT]> 
/boot  at  /dev/sda1
/var   at  /dev/sda5
/      at  /dev/sda6
/home  at  /dev/sda8
<swap> at  /dev/sda7
[/INDENT]

So this neat instructions do not work on mine since proc and dev are on /dev/sda6 and the boot is at /dev/sda1

I only have access to the harddisk using the Ubuntu Jaunty DVD.

Help, please.

---

### Post by humaneasy on 2009-09-01
content removed. duplicated.

---

### Post by Oceanwatcher on 2009-10-09
> **caljohnsmith said:**
> If you have internet access from your Live CD, you could set up a chroot environment, chroot into your Ubuntu installation, and then uninstall Grub2 and finally reinstall Legacy Grub. But first, in order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what it will take to reinstall legacy Grub.

Thank you for pointing me to this script. I used it this morning to gather information to get my system back up again! My errormessage was error 15 and my system did not even get the boot menu up. I have written about it here:

[http://kubuntuforums.net/forums/index.php?topic=3106892.0](http://kubuntuforums.net/forums/index.php?topic=3106892.0)

Again - thank you for the nice tip :-)

---

### Post by nealklomp on 2009-11-27
[http://ubuntuguide.net/fix-grub-2-error-11-unrecognized-device-string/comment-page-1#comment-2126](http://ubuntuguide.net/fix-grub-2-error-11-unrecognized-device-string/comment-page-1#comment-2126)

The Fix.

---

