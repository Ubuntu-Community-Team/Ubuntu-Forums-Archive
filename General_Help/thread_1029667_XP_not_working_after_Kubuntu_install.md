---
title: "XP not working after Kubuntu install"
date: 2009-01-03
forum: General Help
---

### Post by warnerve on 2009-01-03
Hi, this is my problem.

My HP Pavilion came with XP installed in a 7GB partition, some time ago I installed Ubuntu 7.04 in a 20GB partition in the same drive -160GB, 148 free for use-. So, my hard drive had a C partition with 123GB, a D partition using those 7GB or so with XP files, and a couple partitions for Kubuntu using the rest.

Today I formatted my drive using XP and it didn't recognized the Ubuntu partition after booting. Only the 123GB allocated to the Windows partitions.

I then installed Kubuntu 8.10, it is now working but when I select XP in the GRUB, it sends me directly to the PC recovery app, tries to locate the partition and tells me that I have to try again or contact technical support. Kubuntu now detects a 123GB drive. No sign of the previous 7.04 partition.

---

### Post by CrusaderAD on 2009-01-03
I found this to be real handy in recoverying data and making things work again:

[www.pendrivelinux.com](www.pendrivelinux.com)

boot to an external usb drive with any of those and see what you can do. You might have to re-format.

---

### Post by warnerve on 2009-01-03
Thanks! I'll try that.

---

### Post by CrusaderAD on 2009-01-03
No problem... let me know if it works... I'm pretty sure pendrivelinux has a format tool on it and it's really handy. It also takes about 2 minutes to setup. FYI it's based on Mandriva linux, not ubuntu... but they have options to install the Ubuntu Distros.

---

### Post by caljohnsmith on 2009-01-03
In order to get a clearer picture of your setup, how about opening a Konsole and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Windows booting problem might be.

---

### Post by warnerve on 2009-01-03
Thanks for the reply, I'm having problems here. I am opening Konsole and copy/pasting that code but nothing happens, it gives me this message: 

bash: cd: /home/ricardo/Desktop: No existe el fichero ó directorio

In english *The directory doesn't exist.*

I'm doing something wrong for sure.

---

### Post by caljohnsmith on 2009-01-03
Hmmm, that's really strange; did you accidentally delete your /home/ricardo/Desktop directory at some point? How about instead trying:
```
wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt && kate RESULTS.txt &
```

---

### Post by warnerve on 2009-01-03
No I haven't, it's weird.

The second line worked:

```
#!/bin/bash
#to use this script:
#
#sudo bash boot_info_script.txt
#
#date  1/2/09
#authors  meierfra.  and  caljohnsmith
# 
#Looks at all MBRs and identifies the boot loader. 
#   For Grub and Supergrub:  displays the controlling partition.
#   If the  MBR is unknown, displays the whole MBR.
#Looks at all  partitions:
#   Determines their type
#   Identifies their boot sectors.
#         For grub: displays the controlling partition and the offset
#         of the stage2 file as recorded in the boot sector.
#         For NTFS and Fat, examines the Boot Parameter Block for errors.
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


########  List of folders which might contained files used for chainloading
Boot_Codes_Dir="
    /
    /NST/
    "
#################  List of folders whose content will be displayed
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


##############  List of files whose names will be displayed (if they exists)
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

############### List if files whose contents will be displayed.
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


#######  Directory containing the script.

Dir=$(cd $(dirname $0);pwd);

########  To avoid overwriting existing file, look for a non-existing file 
########  RESULT.txt RESULTS1.txt  RESULTS2.txt ... 

LogFile=$Dir/RESULTS
while ( [ -e $LogFile$j.txt ] )
    do  
      ((j++))
      wait;
    done
LogFile=$LogFile$j.txt  #### The RESULTS file.

######  Redirect stdout to RESULT File
exec 6>&1   
exec >$LogFile

########### Create previously non-existing  folder of the form
##########  /tmp/BootInfo  /tmp/BootInfo1, /tmp/BootInfo2 ... 

Folder=/tmp/BootInfo
while (! mkdir $Folder$i 2>/dev/null)
    do  
      ((i++))
      wait;
    done
Folder=$Folder$i

cd $Folder

Log1=$Folder/Log1               #  Most of the information which is not part of
                                #the summary is recorded in this file.
Error_Log=$Folder/Error_Log     #  File to catch all unusal Standar Errors 
Trash=$Folder/Trash             #   File to catch all usual Standard Errors
                                #these messagges will not be included in the RESULTS       
Mount_Error=$Folder/Mount_Error # File to catch Mounting Errors
Unknown_MBR=$Folder/Unknown_MBR # File to record all unknown MBR and Boot sectors. 
Tmp_Log=$Folder/Tmp_Log         #File to temporarily hold some information.

exec 2>$Error_Log              #Redirect all standard error to the file Error_Log


All_Hard_Drives=$(ls /dev/hd? /dev/sd? 2>>$Trash );   ### List of all Hard drives.

echo '============================= Boot Info Summary: =============================='; echo

#####   Search  hard drives which don't exists   or have  corrupt partition tables
#####   All hard drives which a valid partition table are stored   in $Hard_Drives

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


############ Identify the MBR of each  hard drive.

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
                      if [ $offset -lt $((2*$(sfdisk -s $hdd))) ]
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
	33ff) BL='HP/Gateway';;
         ebe) BL=ThinkPad;;
        fa33) BL="No boot loader";; 
        fabe) BL="No boot loader?";;
        fab8) BL="No boot loader";;   
	fceb) BL=BootIt;;
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
      if [ "$type" != "swap" ]  && [ "$type" != "Extended Partition"  ] && [ "$type" != "unknown volume type" ] && [ "$type" != "LVM2_member" ]  && [ "$type" != "linux_raid_member" ] && [ "$type" != "crypto_Luks" ] ;
       then 

          Bytes8081=$(hexdump -v -s 0x80 -n  2 -e '/1 "%x"'  $part)
          case $Bytes8081  in
             8cd) BST="Windows XP";;
            b6d1) BST="Windows XP: Fat32";;
            fa33) BST="Windows XP";;
	    55aa) BST="Windows Vista";;
            100f) BST="HP Recovery";;
            89e) BST="MSDOS5.0: Fat 16";;
            bd0) BST="MSWIN4.1: Fat 32";;
            7405) BST="Vista:  Fat 32";;
            e00) BST="Dell Utility: Fat16";;           
	    5272) BST=Grub;
                  offset=$(hexdump -s 0x44 -n 4 -e '4 "%u"' $part 2>>$Trash);
                  dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $part);
                  pa="T"
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
                    
                        if [ "$pa" = "T"  ]
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
######################   Display the boot sector type.
           echo "    Boot sector type:  "$BST  

####################### Investigate the Boot Parameter Block of an NTFS partition.

           if [[ "$type" = "ntfs" ]]
           then
           offset=$(hexdump -s 0x1c -n 4 -e '"%u"' $part);
           real_offset=$(fdisk -lu $drive | grep "$part "| sed s/*// |awk '{print $2}');
           BPB_Part_Size=$(hexdump -s 0x28 -n 4 -e '"%u"' $part)
           Real_Part_Size=$(sfdisk -s $part);
           Real_Part_Size=$((Real_Part_Size * 2));
           Comp_Size=$(( (BPB_Part_Size - Real_Part_Size)/256 ))
           SectorsPerCluster=$(hexdump -s 0xd -n 1 -e '"%d"' $part);
           MFT_Cluster=$(hexdump -s 0x30 -n 4 -e '"%d"' $part);
           MFT_Sector=$(( MFT_Cluster * SectorsPerCluster ));

           if [[ "$MFT_Sector" -lt "$Real_Part_Size" ]];
           then
               MFT_FILE=$(dd if=$part skip=$MFT_Sector count=1 2>>$Trash | hexdump    -n 4 -e '"%_u"');
               MFT_MFT=$(dd if=$part skip=$MFT_Sector count=1 2>>$Trash | hexdump -s 0xf0  -n 9 -e '1/1 "%x"');     
	   else 
               MFT_FILE="";
               MFT_MFT="";
           fi;
           MFT_Mirr_Cluster=$(hexdump -s 0x38 -n 4 -e '"%d"' $part);
           MFT_Mirr_Sector=$(( MFT_Mirr_Cluster * SectorsPerCluster ));
           if [[ "$MFT_Mirr_Sector" -lt "$Real_Part_Size" ]];
           then
           MFT_Mirr_FILE=$(dd if=$part skip=$MFT_Mirr_Sector count=1 2>>$Trash | hexdump    -n 4 -e '"%_u"');
  
           MFT_Mirr_MFT=$(dd if=$part skip=$MFT_Mirr_Sector count=1 2>>$Trash | hexdump -s 0xf0  -n 9 -e '1/1 "%x"');
           else 
               MFT_Mirr_FILE="";
               MFT_Mirr_MFT="";
           fi;
           if [[ "$offset" = "$real_offset"  && "$MFT_FILE" = "FILE"  &&  "$MFT_MFT" = "432404d046054" && "$MFT_Mirr_FILE" = "FILE"  &&  "$MFT_Mirr_MFT" = "432404d046054" && "$Comp_Size" = "0"  ]];
	    then
	       BSI=$(echo $BSI" "No errors found in the  Boot Parameter Block.);
	    else
            [[ "$offset" = "$real_offset" ]] ||  BSI=$(echo $BSI"  "According to the info in the boot sector, $name starts at sector $offset, but according to the info  from fdisk, $name starts at sector   $real_offset . );
            if  [[ "$MFT_FILE" != "FILE"  ||  "$MFT_MFT" != "432404d046054" ]]; 
	    then 
                BSI=$(echo $BSI" "The info in boot sector  on  the starting sector of the MFT is wrong.);
                echo MFT Sector of $part >> $Unknown_MBR;
                echo >> $Unknown_MBR
                dd if=$part skip=$MFT_Sector count=1 2>>$Trash| hexdump -C >>$Unknown_MBR;
             fi;
             if [[ "$MFT_Mirr_FILE" != "FILE"  ||  "$MFT_Mirr_MFT" != "432404d046054" ]];
	     then
		 BSI=$(echo $BSI" "The info in the boot sector on  the starting sector of the MFT Mirror  is wrong.);
             fi;

             if  [[ "$Comp_Size" != "0"  ]];
             then  
                   BSI=$(echo $BSI"  "According to the info in the boot sector, $name has    $BPB_Part_Size sectors, but according to the info  from fdisk, it has  $Real_Part_Size sectors.);
              dd if=$part skip=$BPB_Part_Size count=2 2>>$Trash |hexdump -C
             fi;
           fi;
          fi;

######################## Investigate the Boot Parameter Block of some Fat partitions

  if [[ "$Bytes8081" = "7cc6" ||  "$Bytes8081" = "7815"  ||  "$Bytes8081" = "B6D1"  || "$Bytes8081" =  "7405" || "$Bytes8081" = "bd0" ||  "$Bytes8081" =  "89e"  ]] ;
           then
           offset=$(hexdump -s 0x1c -n 4 -e '"%d\n"' $part);
           real_offset=$(fdisk -lu $drive | grep "$part "| sed s/*// |awk '{print $2}');
           BPB_Part_Size=$(hexdump -s 0x20 -n 4 -e '"%d"' $part);
           Real_Part_Size=$(sfdisk -s $part);
           Real_Part_Size=$((Real_Part_Size * 2));  
           Comp_Size=$(( (BPB_Part_Size - Real_Part_Size)/256 ))    
           if [[ "$offset" = "$real_offset" && "$Comp_Size" = "0"  ]];
	    then
	       BSI=$(echo $BSI" "No errors found in the  Boot Parameter Block.);
	    else
            [[ "$offset" = "$real_offset" ]] ||  BSI=$(echo $BSI"  "According to the info in the boot sector, $name starts at sector $offset, but according to the info  from fdisk, $name starts at sector   $real_offset . );          
            [[ "$Comp_Size" != "0"  ]]  ||  BSI=$(echo $BSI"  "According to the info in the boot sector, $name has    $BPB_Part_Size sectors, but according to the info  from fdisk, it has  $Real_Part_Size sectors.);
              
            fi; 
          fi;

         
    
       if  mount $part $name 2>$Mount_Error;     ####### Try to mount partition
       then     ############  if partition was mounted
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
                          pa="T"
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
                    
                           if [ "$pa" = "T"  ]
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
		  done; ## End of loop through the files in particular  Boot_Code_Directory
              fi;
           done   ## End of the loop through the Boot_Code_Directories.
 
      echo -n "    Boot sector info:  "
      echo $BSI | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'
      echo "    Operating System:  "$OS
      echo -n "    Boot files/dirs:   "
      echo $BootFiles | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'
     
     umount $name || umount -l $name; 
     else     ############### if partition failed to mount
       echo -n "    Boot sector info:  "
       echo $BSI | fold -s -w 55 |  sed -e '2~1s/.*/                       &/'  
       echo "    Mounting failed:";  
     cat $Mount_Error 
     fi;  ### end of Mounting "if then else"
     fi;  ### end of Partition Type "if then else"
     echo;
 
     done;  ### end of partition loop
     done;  ### end of hard drive loop

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
echo "blkid -c /dev/null: ____________________________________________________________";
echo; blkid -c /dev/null
echo;
echo '=============================== "mount" output: ===============================';
echo; mount
echo >> $Log1

#################   Write the content of Log1 to the RESULTS file
cat $Log1  

if [ -e $Unknown_MBR ]; 
then
 echo "=========================== Unknown MBRs or Boot Sectors =======================";
 echo;
 cat $Unknown_MBR;
 echo
fi;

  

#####################  Write the Error Log to the RESULT file
echo "=============================== StdErr Messages: ==============================="
echo
[ -s $Error_Log ] && cat $Error_Log || echo "No errors were reported."

#####   Make the  user the owner of Result file
chown $(basename ~) $LogFile    

#######  Reset the Standard Output to the Terminal 
exec 1>&-
exec 1>&6
exec 6>&-

echo Finished. The results are in the file $(basename $LogFile) located in $Dir



```

Hope this helps.

---

### Post by caljohnsmith on 2009-01-03
You actually posted the contents of the script, and not the results. if you look in the same directory where the boot_info_script.txt was downloaded to, you should find a "RESULTS.txt" file; please post the contents of that file. :)

---

### Post by warnerve on 2009-01-03
:confused:

I'm not getting the results.txt file, only the boot_info_script.txt file.

:(

---

### Post by caljohnsmith on 2009-01-03
OK, how about trying again with:
```
cd /tmp && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt && kate RESULTS.txt &
```
The last command in the above chain of commands should pull up a text editor (kate) with the RESULTS.txt file; if it doesn't, please copy/paste your terminal session where you ran the commands so I can get a better idea of what happened.

---

### Post by warnerve on 2009-01-03
Not working, here's the terminal session log

```
ricardo@ric:~$ cd /tmp && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt && kate RESULTS.txt &
--2009-01-03 21:12:30--  http://home.comcast.net/~ubuntu_grub/boot_info_script.txt
Resolviendo home.comcast.net... [1] 6112
ricardo@ric:~$ 216.87.188.9
Conectando a home.comcast.net|216.87.188.9|:80... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 23641 (23K) [text/plain]
Guardando: «boot_info_script.txt.1»

100%[======================================>] 23,641      48.8K/s   en 0.5s

2009-01-03 21:12:31 (48.8 KB/s) - `boot_info_script.txt.1' guardado [23641/23641]


```

---

### Post by caljohnsmith on 2009-01-03
Something is really strange about your terminal session. How about trying these commands (copy them over one at a time):
```
cd /tmp
wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt'
sudo bash boot_info_script.txt
kate RESULTS.txt &
```

---

### Post by warnerve on 2009-01-03
Great it worked!

```
============================= Boot Info Summary: ==============================

 => Drive sdb does not have a valid partition table.
 => Drive sdc does not have a valid partition table.
 => Drive sdd does not have a valid partition table.
 => Drive sde does not have a valid partition table.
 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for its boot files.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTLDR /NTDETECT.COM /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Mounting failed:
mount: debe especificar el tipo de sistema de ficheros

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda7: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros, 312581808 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x1549f232

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *          63    29302559    14651248+  8e  Linux LVM
/dev/sda2        29302560   312576704   141637072+   5  Extendida
/dev/sda5       312078753   312576704      248976   83  Linux
/dev/sda6        29302686   306472004   138584659+  83  Linux
/dev/sda7       306472068   312078689     2803311   82  Linux swap / Solaris

Las entradas de la tabla de particiones no están en el orden del disco

sfdisk -V /dev/sda:

Atención: la partición 5 no empieza en un límite de cilindro

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

sfdisk -V /dev/sdb:

/dev/sdb: No se ha encontrado el medio

sfdisk: No se puede abrir /dev/sdb para lectura

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

sfdisk -V /dev/sdc:

/dev/sdc: No se ha encontrado el medio

sfdisk: No se puede abrir /dev/sdc para lectura

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

sfdisk -V /dev/sdd:

/dev/sdd: No se ha encontrado el medio

sfdisk: No se puede abrir /dev/sdd para lectura

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

sfdisk -V /dev/sde:

/dev/sde: No se ha encontrado el medio

sfdisk: No se puede abrir /dev/sde para lectura

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="HP_RECOVERY" UUID="434F-C48E" TYPE="vfat" 
/dev/sda6: UUID="82ff14d1-73a4-4bdd-8259-44aae5ad37c4" TYPE="ext3" 
/dev/sda7: UUID="578ec6db-d757-4a13-bfd0-5d80851da0bf" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
/home/ricardo/.Private on /home/ricardo/Private type ecryptfs (rw,ecryptfs_sig=a850e9262b7ee941,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,user=ricardo)

================================ sda1/boot.ini: ================================

[boot loader]
timeout=0
default=C:\CMDCONS\BOOTSECT.DAT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=82ff14d1-73a4-4bdd-8259-44aae5ad37c4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=82ff14d1-73a4-4bdd-8259-44aae5ad37c4

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
uuid		82ff14d1-73a4-4bdd-8259-44aae5ad37c4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=82ff14d1-73a4-4bdd-8259-44aae5ad37c4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		82ff14d1-73a4-4bdd-8259-44aae5ad37c4
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=82ff14d1-73a4-4bdd-8259-44aae5ad37c4 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		82ff14d1-73a4-4bdd-8259-44aae5ad37c4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=82ff14d1-73a4-4bdd-8259-44aae5ad37c4 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		82ff14d1-73a4-4bdd-8259-44aae5ad37c4
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=82ff14d1-73a4-4bdd-8259-44aae5ad37c4 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		82ff14d1-73a4-4bdd-8259-44aae5ad37c4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=82ff14d1-73a4-4bdd-8259-44aae5ad37c4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=578ec6db-d757-4a13-bfd0-5d80851da0bf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sda6/boot: ==================================

total 25532
drwxr-xr-x  3 root root    4096 2009-01-03 15:31 .
drwxr-xr-x 20 root root    4096 2009-01-03 15:28 ..
-rw-r--r--  1 root root  503560 2008-11-04 14:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-20 17:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 14:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-20 17:30 config-2.6.27-9-generic
drwxr-xr-x  2 root root    4096 2009-01-03 15:28 grub
-rw-r--r--  1 root root 8674502 2009-01-03 15:28 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8672658 2009-01-03 15:31 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 14:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 14:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-20 17:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 14:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-20 17:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 14:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-20 17:30 vmlinuz-2.6.27-9-generic

=============================== sda6/boot/grub: ===============================

total 232
drwxr-xr-x 2 root root   4096 2009-01-03 15:28 .
drwxr-xr-x 3 root root   4096 2009-01-03 15:31 ..
-rw-r--r-- 1 root root    197 2009-01-03 14:32 default
-rw-r--r-- 1 root root     15 2009-01-03 14:32 device.map
-rw-r--r-- 1 root root   8108 2009-01-03 14:32 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-03 14:32 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-03 14:32 installed-version
-rw-r--r-- 1 root root   8712 2009-01-03 14:32 jfs_stage1_5
-rw-r--r-- 1 root root   5088 2009-01-03 15:28 menu.lst
-rw-r--r-- 1 root root   5004 2009-01-03 15:28 menu.lst~
-rw-r--r-- 1 root root   4606 2009-01-03 14:43 menu.lst_original
-rw-r--r-- 1 root root   7352 2009-01-03 14:32 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-03 14:32 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-03 14:32 stage1
-rw-r--r-- 1 root root 121460 2009-01-03 14:32 stage2
-rw-r--r-- 1 root root   9556 2009-01-03 14:32 xfs_stage1_5

=========================== Unknown MBRs or Boot Sectors =======================

Unknown BootLoader  on /dev/sda1

00000000  e9 a7 00 52 45 43 4f 56  45 52 59 00 02 08 20 00  |...RECOVERY... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 f0 00 3f 00 00 00  |........?...?...|
00000020  31 19 df 00 c8 37 00 00  00 00 00 00 02 00 00 00  |1....7..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 8e c4 4f 43 4e  4f 20 4e 41 4d 45 20 20  |..)..OCNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 8b d0 c1 e2 02 80  |  FAT32   ......|
00000060  e6 01 66 c1 e8 07 66 3b  46 f8 74 2a 66 89 46 f8  |..f...f;F.t*f.F.|
00000070  66 03 46 f4 66 0f b6 5e  28 80 e3 0f 74 0f 3a 5e  |f.F.f..^(...t.:^|
00000080  10 0f 83 90 00 66 0f af  5e 24 66 03 c3 bb e0 07  |.....f..^$f.....|
00000090  b9 01 00 e8 cf 00 8b da  66 8b 87 00 7e 66 25 ff  |........f...~f%.|
000000a0  ff ff 0f 66 3d f8 ff ff  0f c3 33 c9 8e d9 8e c1  |...f=.....3.....|
000000b0  8e d1 66 bc f4 7b 00 00  bd 00 7c 66 0f b6 46 10  |..f..{....|f..F.|
000000c0  66 f7 66 24 66 0f b7 56  0e 66 03 56 1c 66 89 56  |f.f$f..V.f.V.f.V|
000000d0  f4 66 03 c2 66 89 46 fc  66 c7 46 f8 ff ff ff ff  |.f..f.F.f.F.....|
000000e0  66 8b 46 2c 66 50 e8 af  00 bb 70 00 b9 01 00 e8  |f.F,fP....p.....|
000000f0  73 00 bf 00 07 b1 0b be  a9 7d f3 a6 74 2a 03 f9  |s........}..t*..|
00000100  83 c7 15 81 ff 00 09 72  ec 66 40 4a 75 db 66 58  |.......r.f@Ju.fX|
00000110  e8 47 ff 72 cf be b4 7d  ac 84 c0 74 09 b4 0e bb  |.G.r...}...t....|
00000120  07 00 cd 10 eb f2 cd 19  66 58 ff 75 09 ff 75 0f  |........fX.u..u.|
00000130  66 58 bb 00 20 66 83 f8  02 72 da 66 3d f8 ff ff  |fX.. f...r.f=...|
00000140  0f 73 d2 66 50 e8 50 00  0f b6 4e 0d e8 16 00 c1  |.s.fP.P...N.....|
00000150  e1 05 03 d9 66 58 53 e8  00 ff 5b 72 d8 8a 56 40  |....fXS...[r..V@|
00000160  ea 00 00 00 20 66 60 66  6a 00 66 50 53 6a 00 66  |.... f`fj.fPSj.f|
00000170  68 10 00 01 00 8b f4 b8  00 42 8a 56 40 cd 13 be  |h........B.V@...|
00000180  c7 7d 72 94 67 83 44 24  06 20 66 67 ff 44 24 08  |.}r.g.D$. fg.D$.|
00000190  e2 e3 83 c4 10 66 61 c3  66 48 66 48 66 0f b6 56  |.....fa.fHfHf..V|
000001a0  0d 66 f7 e2 66 03 46 fc  c3 4e 54 4c 44 52 20 20  |.f..f.F..NTLDR  |
000001b0  20 20 20 20 0d 0a 4e 6f  20 53 79 73 74 65 6d 20  |    ..No System |
000001c0  44 69 73 6b 20 6f 72 0d  0a 44 69 73 6b 20 49 2f  |Disk or..Disk I/|
000001d0  4f 20 65 72 72 6f 72 0d  0a 50 72 65 73 73 20 61  |O error..Press a|
000001e0  20 6b 65 79 20 74 6f 20  72 65 73 74 61 72 74 0d  | key to restart.|
000001f0  0a 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

/dev/sdb: No se ha encontrado el medio

sfdisk: No se puede abrir /dev/sdb para lectura
/dev/sdc: No se ha encontrado el medio

sfdisk: No se puede abrir /dev/sdc para lectura
/dev/sdd: No se ha encontrado el medio

sfdisk: No se puede abrir /dev/sdd para lectura
/dev/sde: No se ha encontrado el medio

sfdisk: No se puede abrir /dev/sde para lectura
/dev/sda5: unknown volume type
```

This last part in spanish says
[I]Can't open /dev/sdc for read
/dev/sdd:Media not found
[/I]

---

### Post by caljohnsmith on 2009-01-03
Unfortunately something happened to your Windows sda1 partition; currently it is listed in the partition table as having a "Linux LVM" file system, when actually it looks like it uses a FAT32 file system. Also, it looks like the Windows partition boot sector might be damaged. I would begin by doing the following:
```
sudo sfdisk -c /dev/sda 1 c
```
Next download and run "testdisk":
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After that, rerun testdisk again, go through the same steps until after you choose "Boot", but this time choose "Backup BS" instead of "Rebuild BS"; if testdisk says the sectors are not identical or something like that, choose "write". Then reboot, try and boot Windows from your Grub menu, and let me know exactly what happens. We can work from there.

---

### Post by warnerve on 2009-01-03
It's a bit slow but working. I'll post the results in a few hours. Thanks for your support. :D

---

### Post by warnerve on 2009-01-04
Hi caljohnsmith, I'm getting this after the first run of testdisk.

```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition                  Start        End    Size in sectors
 1 * hid. FAT32 LBA           0   1  1  1823 254 63   29302497

FAT : 32
cluster_size 16
reserved     32
total_sect   29274000
fat32_length 14280
root_cluster 0
flags        0000
version      0.0
root_cluster 0
info_sector  1
backup_boot  6
free_count   18446744073709551615
next_free    18446744073709551615
Extrapolated boot sector and current boot sector are identical.

```

Options are DUMP, LIST and QUIT.

---

### Post by caljohnsmith on 2009-01-04
OK, you can quit testdisk then since the backup boot sector is the same as your current boot sector (that's a good sign). How about posting the output of:
```
sudo mount /dev/sda1 /mnt && ls -l /mnt
```
And we can go from there. :)

---

