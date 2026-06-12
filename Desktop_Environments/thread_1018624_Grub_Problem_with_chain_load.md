---
title: "Grub Problem with chain load"
date: 2008-12-22
forum: Desktop Environments
---

### Post by lsatenstein on 2008-12-22
My configuration is with two hard disks. 
Disk1 has windows and Ubuntu (50-50) and there is no problem with selection of either XP or Ubuntu 8.10.

Disk2, also 50-50 has Fedora 10 on it using lvm

I can chainload to the second drive, but during the boot of Fedora10, it crashes during the boot because the loader cannot find the /root directory (Fedora uses LVM)

If however, I build the grub.conf file from the disk with Fedora10,
I can chain load to the XP-Ubuntu8.10 disk without problems.

I believe that the GRUB that was modified for 8.10 is not recognizing lvm partitions.

Any suggestions for a grub parameter that would allow me to select the Fedora10 drive.

Another question.

With today's large drives, is there a reason why we need a swap partition? Why not just a swap file?

---

### Post by caljohnsmith on 2008-12-22
> **lsatenstein said:**
> 
Another question.

With today's large drives, is there a reason why we need a swap partition? Why not just a swap file?
Yes, you can certainly use a swap file instead of a swap partition, and to my knowledge I don't think there is any special advantage of having a swap partition vs. a swap file. But about your booting problem, in order to get a clearer picture of your setup, how about doing:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be. It would be best to run that script from Ubuntu and not Fedora, because for one thing Fedora does not use sudo as I understand it.

---

### Post by meierfra. on 2008-12-22
> With today's large drives, is there a reason why we need a swap partition? Why not just a swap file?

A swap file is fine. But if you use hibernation, it is it little bit more difficult to set up.

---

### Post by ogredeschnique on 2009-01-04
I'll bite. 
I'm having trouble with grub chain loading as well. 
I have gentoo on a second drive (hd1), windows and ubuntu on the main (hd0).
I read <[This]("http://www.debuntu.org/how-to-booting-another-grub-from-grub")> and it booted windows.
that section of my grub.conf/"menu.lst" looks like this:```
title Gentoo Linux 2.6.26-r4
root (hd1,0)
chainloader +1
```> **caljohnsmith said:**
> 
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop;
The result was a file called boot_info_script.txt which was an html page saying that personal sites are down. The file is attached.

---

### Post by caljohnsmith on 2009-01-04
Ogredeschnique, I just checked right now and the script is available on the server. How about trying again the commands from post #2 and let us know how it goes.

---

### Post by ogredeschnique on 2009-01-04
```
Your file of 23.1 KB bytes exceeds the forum's limit of 19.5 KB for this filetype. 
```

Here is the text. 
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
              MFT_MFT=$( dd if=$part skip=$MFT_Sector count=1 2>>$Trash| hexdump -e '4/1 "%x"' | grep "432404d046054")
               
	   else 
               MFT_FILE="";
               MFT_MFT="";
           fi;
           MFT_Mirr_Cluster=$(hexdump -s 0x38 -n 4 -e '"%d"' $part);
           MFT_Mirr_Sector=$(( MFT_Mirr_Cluster * SectorsPerCluster ));
           if [[ "$MFT_Mirr_Sector" -lt "$Real_Part_Size" ]];
           then
           MFT_Mirr_FILE=$(dd if=$part skip=$MFT_Mirr_Sector count=1 2>>$Trash | hexdump    -n 4 -e '"%_u"');
  
           MFT_Mirr_MFT=$(dd if=$part skip=$MFT_Mirr_Sector count=1 2>>$Trash |hexdump -e '4/1 "%x"' | grep "432404d046054")
           else 
               MFT_Mirr_FILE="";
               MFT_Mirr_MFT="";
           fi;
           if [[ "$offset" = "$real_offset"  && "$MFT_FILE" = "FILE"  &&  "$MFT_MFT" != "" && "$MFT_Mirr_FILE" = "FILE"  &&  "$MFT_Mirr_MFT" != "" && "$Comp_Size" = "0"  ]];
	    then
	       BSI=$(echo $BSI" "No errors found in the  Boot Parameter Block.);
	    else
            [[ "$offset" = "$real_offset" ]] ||  BSI=$(echo $BSI"  "According to the info in the boot sector, $name starts at sector $offset, but according to the info  from fdisk, $name starts at sector   $real_offset . );
            if  [[ "$MFT_FILE" != "FILE"  ||  "$MFT_MFT" = "" ]]; 
	    then 
                BSI=$(echo $BSI" "The info in boot sector  on  the starting sector of the MFT is wrong.);
                echo MFT Sector of $part >> $Unknown_MBR;
                echo >> $Unknown_MBR
                dd if=$part skip=$MFT_Sector count=1 2>>$Trash| hexdump -C >>$Unknown_MBR;
             fi;
             if [[ "$MFT_Mirr_FILE" != "FILE"  ||  "$MFT_Mirr_MFT" = "" ]];
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

---

### Post by caljohnsmith on 2009-01-05
It looks like you unintentionally posted the contents of the boot_info_script.txt; please post the contents of the "RESULTS.txt" file instead. :)

---

### Post by ogredeschnique on 2009-01-05
Um, whoopsie? 
Where is the RESULTS.txt supposed to be created? It seems to be missing from my desktop, as in it wasn't created there.

---

### Post by caljohnsmith on 2009-01-05
OK, how about deleting any boot_info_script.txt files from your desktop, and try running the script again with this command:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt && gedit RESULTS* &
```
See if that works and let me know how it goes.

---

### Post by ogredeschnique on 2009-01-05
I really appreciate your help, by the way.
I get:```
user@computer:~$ cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt && gedit RESULTS* &
[2] 9224
--10:57:48--  http://home.comcast.net/~ubuntu_grub/boot_info_script.txt
           => `boot_info_script.txt'
Resolving home.comcast.net... hardly@dv8klapt:~$ 216.87.188.9
Connecting to home.comcast.net|216.87.188.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 24,071 (24K) [text/plain]

100%[====================================>] 24,071        --.--K/s             

10:57:48 (167.76 KB/s) - `boot_info_script.txt' saved [24071/24071]

_


```
And a "thinking" blinking cursor with no prompt.

Crtl+c yields ```
[2]+  Stopped                 cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt && gedit RESULTS*

``` but there doesn't seem to be anything happening.

---

### Post by caljohnsmith on 2009-01-05
Did you give the script at least a minute or two to complete executing? If not, please try again. But if the script hung without completing, how about instead trying:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script21.txt' && sudo bash boot_info_script21.txt && gedit RESULTS* &
```
Let me know how that goes.

---

### Post by ranch hand on 2009-01-05
Yup, I am lurking.  Who knows, I may learn something.  "They" say this is good for people over 50.

---

### Post by ogredeschnique on 2009-01-05
It had definitely hung. 
Well, I ran the txt file script as root and it gave me a Result.txt
```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for its boot files.
 => Grub is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for its boot files.
 => No known boot loader is installed in the MBR of /dev/sdc

```

---

### Post by caljohnsmith on 2009-01-05
Ogredeschnique, can you maybe boot your Ubuntu Live CD and run the script from there? The part you posted about what is installed in your drives' MBR is unfortunately not enough to help you with your problem.

> **ranch hand said:**
> Yup, I am lurking.  Who knows, I may learn something.  "They" say this is good for people over 50.
Great to see you around; have you had any input interface problems with the bovine devices recently? :)

---

### Post by ogredeschnique on 2009-01-06
The code you posted did execute completely from a liveCD.
RESULT.txt
```
============================= Boot Info Summary: ==============================

 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for its boot files.
 => Grub is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for its boot files.
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /grub/menu.lst 
                       /boot/grub/grub.conf /grub/grub.conf /boot /boot/grub 
                       /grub

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:   This is
    Boot files/dirs:   /etc/fstab /boot

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1ea71ea6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   135299429    67649683+   7  HPFS/NTFS
/dev/sda3       232332093   234436544     1052226   d7  Unknown
/dev/sda4       135299430   232332029    48516300   83  Linux

Partition table entries are not in disk order

sfdisk -V /dev/sda:

Warning: partition 3 does not start at a cylinder boundary

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30e630e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63       80324       40131   83  Linux
/dev/sdb2       156167865   234436544    39134340   83  Linux
/dev/sdb3           80325    77272649    38596162+  83  Linux
/dev/sdb4        77272650   156167864    39447607+  83  Linux

Partition table entries are not in disk order

sfdisk -V /dev/sdb:

/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x59861d6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63  1465144064   732572001    7  HPFS/NTFS

sfdisk -V /dev/sdc:

/dev/sdc: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="98B8A48EB8A46C86" LABEL="OS" TYPE="ntfs" 
/dev/sda3: UUID="62DC187EDC184EA3" TYPE="ntfs" 
/dev/sda4: UUID="d8c70ea2-e12c-4ca8-ab81-0e95586769b2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="b7a614ac-8e57-4e3c-ba59-b6ec58d5168b" TYPE="ext2" 
/dev/sdb2: UUID="24852b63-5c63-4ac8-bc99-9d23d3bec87d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: UUID="d54f4427-08af-4cf0-9ef1-63993408bbb3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb4: UUID="ef19b32c-b268-431c-8c25-e33ddd14ed32" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
/dev/sdc1: UUID="55D123D9E79ABF54" LABEL="OneTouch4" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdc1 on /media/OneTouch4 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

================================ sda3/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /maxmem=256

=========================== sda4/boot/grub/menu.lst: ===========================

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
#timeout		0

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
# kopt=root=UUID=d8c70ea2-e12c-4ca8-ab81-0e95586769b2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d8c70ea2-e12c-4ca8-ab81-0e95586769b2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=d8c70ea2-e12c-4ca8-ab81-0e95586769b2 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

title Gentoo Linux 2.6.26-r4
root (hd1,0)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		---------Other---------
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=d8c70ea2-e12c-4ca8-ab81-0e95586769b2 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
## usbfs is the USB group in sftab file:
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0

================================== sda4/boot: ==================================

total 54364
drwxr-xr-x  3 root root    4096 2008-12-17 19:28 .
drwxr-xr-x 21 root root    4096 2008-12-29 07:48 ..
-rw-r--r--  1 root root  422607 2008-04-10 16:51 abi-2.6.24-16-generic
-rw-r--r--  1 root root  422838 2008-11-24 22:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root  422838 2008-11-27 22:13 abi-2.6.24-23-generic
-rw-r--r--  1 root root   79964 2008-04-10 16:51 config-2.6.24-16-generic
-rw-r--r--  1 root root   80062 2008-11-24 22:47 config-2.6.24-22-generic
-rw-r--r--  1 root root   80051 2008-11-27 22:13 config-2.6.24-23-generic
drwxr-xr-x  2 root root    4096 2009-01-05 07:54 grub
-rw-r--r--  1 root root 7503114 2008-11-30 01:49 initrd.img-2.6.24-16-generic
-rw-r--r--  1 root root 7892413 2008-11-29 13:22 initrd.img-2.6.24-16-generic.bak
-rw-r--r--  1 root root 7504184 2008-11-30 05:56 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7503341 2008-11-30 01:57 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root 7504951 2008-12-17 19:28 initrd.img-2.6.24-23-generic
-rw-r--r--  1 root root 7504919 2008-12-17 19:28 initrd.img-2.6.24-23-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r--  1 root root  899892 2008-04-10 16:51 System.map-2.6.24-16-generic
-rw-r--r--  1 root root  905617 2008-11-24 22:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root  905633 2008-11-27 22:13 System.map-2.6.24-23-generic
-rw-r--r--  1 root root 1904248 2008-04-10 16:51 vmlinuz-2.6.24-16-generic
-rw-r--r--  1 root root 1921176 2008-11-24 22:47 vmlinuz-2.6.24-22-generic
-rw-r--r--  1 root root 1921976 2008-11-27 22:13 vmlinuz-2.6.24-23-generic

=============================== sda4/boot/grub: ===============================

total 212
drwxr-xr-x 2 root root   4096 2009-01-05 07:54 .
drwxr-xr-x 3 root root   4096 2008-12-17 19:28 ..
-rw-r--r-- 1 root root    197 2008-11-29 13:22 default
-rw-r--r-- 1 root root     45 2008-11-29 13:22 device.map
-rw-r--r-- 1 root root   8056 2008-11-29 13:22 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-11-29 13:22 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-11-29 13:22 installed-version
-rw-r--r-- 1 root root   8608 2008-11-29 13:22 jfs_stage1_5
-rw-r--r-- 1 root root   4637 2009-01-05 07:54 menu.lst
-rw-r--r-- 1 root root   4787 2008-12-17 19:28 menu.lst~
-rw-r--r-- 1 root root   7324 2008-11-29 13:22 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-11-29 13:22 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-11-29 13:22 stage1
-rw-r--r-- 1 root root 108356 2008-11-29 13:22 stage2
-rw-r--r-- 1 root root   9276 2008-11-29 13:22 xfs_stage1_5

=========================== sdb1/boot/grub/menu.lst: ===========================


============================= sdb1/grub/menu.lst: =============================


========================== sdb1/boot/grub/grub.conf: ==========================

ch listing to boot as default. 0 is the first, 1 the second etc.
default 0
# How many seconds to wait before the default listing is booted.
# timeout 30
# Nice, fat splash-image to spice things up :)
# Comment out if you don't have a graphics card installed
splashimage=(hd0,0)/boot/grub/splash.xpm.gz
#
title Gentoo Linux 2.6.26-r4
# Partition where the kernel image (or operating system) is located
root (hd0,2)
kernel (hd0,0)/boot/kernel-2.6.26-.gentoo.-r4 root=/dev/hdb3

title Gentoo Linux 2.6.26-r4 (rescue)
# Partition where the kernel image (or operating system) is located
root (hd0,0)
kernel /boot/kernel-2.6.26-gentoo-r4 root=/dev/hdb3 init=/bin/bb

title GenKernel
root (hd0,0)
kernel /boot/kernel-genkernel-x86-2.6.26-gentoo-r4 root=/dev/hdb3 init=/linuxrc ramdisk=8192 real_root=/dev/hdb3
initrd /boot/initramfs-genkernel-x86-2.6.26-gentoo-r4

# The next four lines are only if you dualboot with a Windows system.
# In this case, Windows is hosted on /dev/sdb1 in relation to THIS DRIVE.
title Windows XP
rootnoverify (hd1,0)
makeactive
chainloader +1
#

============================= sdb1/grub/grub.conf: =============================

ch listing to boot as default. 0 is the first, 1 the second etc.
default 0
# How many seconds to wait before the default listing is booted.
# timeout 30
# Nice, fat splash-image to spice things up :)
# Comment out if you don't have a graphics card installed
splashimage=(hd0,0)/boot/grub/splash.xpm.gz
#
title Gentoo Linux 2.6.26-r4
# Partition where the kernel image (or operating system) is located
root (hd0,2)
kernel (hd0,0)/boot/kernel-2.6.26-.gentoo.-r4 root=/dev/hdb3

title Gentoo Linux 2.6.26-r4 (rescue)
# Partition where the kernel image (or operating system) is located
root (hd0,0)
kernel /boot/kernel-2.6.26-gentoo-r4 root=/dev/hdb3 init=/bin/bb

title GenKernel
root (hd0,0)
kernel /boot/kernel-genkernel-x86-2.6.26-gentoo-r4 root=/dev/hdb3 init=/linuxrc ramdisk=8192 real_root=/dev/hdb3
initrd /boot/initramfs-genkernel-x86-2.6.26-gentoo-r4

# The next four lines are only if you dualboot with a Windows system.
# In this case, Windows is hosted on /dev/sdb1 in relation to THIS DRIVE.
title Windows XP
rootnoverify (hd1,0)
makeactive
chainloader +1
#

================================== sdb1/boot: ==================================

lrwxrwxrwx 1 root root 1 2008-12-16 23:08 sdb1/boot -> .

=============================== sdb1/boot/grub: ===============================

total 334
drwxr-xr-x 2 root root   1024 2009-01-01 07:45 .
drwxr-xr-x 4 root root   1024 2008-12-17 20:00 ..
-rw-r--r-- 1 root root    197 2008-12-17 12:51 default
-rw-r--r-- 1 root root     45 2008-12-17 12:27 device.map
-rw-r--r-- 1 root root   8064 2008-12-17 12:51 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-12-17 12:51 fat_stage1_5
-rw-r--r-- 1 root root   7200 2008-12-17 12:51 ffs_stage1_5
-rw-r--r-- 1 root root   1068 2008-12-18 13:07 grub.conf
-rw-r--r-- 1 root root   7200 2008-12-17 12:51 iso9660_stage1_5
-rw-r--r-- 1 root root   8640 2008-12-17 12:51 jfs_stage1_5
lrwxrwxrwx 1 root root      9 2008-12-17 12:27 menu.lst -> grub.conf
-rw-r--r-- 1 root root   7328 2008-12-17 12:51 minix_stage1_5
-rw-r--r-- 1 root root   9728 2008-12-17 12:51 reiserfs_stage1_5
-rw-r--r-- 1 root root  33856 2008-12-17 12:27 splash.xpm.gz
-rw-r--r-- 1 root root    512 2008-12-17 12:51 stage1
-rw-r--r-- 1 root root 105372 2008-12-17 12:51 stage2
-rw-r--r-- 1 root root 105372 2008-12-17 12:27 stage2_eltorito
-rw-r--r-- 1 root root   7520 2008-12-17 12:51 ufs2_stage1_5
-rw-r--r-- 1 root root   6752 2008-12-17 12:51 vstafs_stage1_5
-rw-r--r-- 1 root root   9384 2008-12-17 12:51 xfs_stage1_5

================================== sdb1/grub: ==================================

total 334
drwxr-xr-x 2 root root   1024 2009-01-01 07:45 .
drwxr-xr-x 4 root root   1024 2008-12-17 20:00 ..
-rw-r--r-- 1 root root    197 2008-12-17 12:51 default
-rw-r--r-- 1 root root     45 2008-12-17 12:27 device.map
-rw-r--r-- 1 root root   8064 2008-12-17 12:51 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-12-17 12:51 fat_stage1_5
-rw-r--r-- 1 root root   7200 2008-12-17 12:51 ffs_stage1_5
-rw-r--r-- 1 root root   1068 2008-12-18 13:07 grub.conf
-rw-r--r-- 1 root root   7200 2008-12-17 12:51 iso9660_stage1_5
-rw-r--r-- 1 root root   8640 2008-12-17 12:51 jfs_stage1_5
lrwxrwxrwx 1 root root      9 2008-12-17 12:27 menu.lst -> grub.conf
-rw-r--r-- 1 root root   7328 2008-12-17 12:51 minix_stage1_5
-rw-r--r-- 1 root root   9728 2008-12-17 12:51 reiserfs_stage1_5
-rw-r--r-- 1 root root  33856 2008-12-17 12:27 splash.xpm.gz
-rw-r--r-- 1 root root    512 2008-12-17 12:51 stage1
-rw-r--r-- 1 root root 105372 2008-12-17 12:51 stage2
-rw-r--r-- 1 root root 105372 2008-12-17 12:27 stage2_eltorito
-rw-r--r-- 1 root root   7520 2008-12-17 12:51 ufs2_stage1_5
-rw-r--r-- 1 root root   6752 2008-12-17 12:51 vstafs_stage1_5
-rw-r--r-- 1 root root   9384 2008-12-17 12:51 xfs_stage1_5

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# noatime turns off atimes for increased performance (atimes normally aren't 
# needed; notail increases performance of ReiserFS (at the expense of storage 
# efficiency).  It's safe to drop the noatime options if you want and to 
# switch between notail / tail freely.
#
# The root filesystem should have a pass number of either 0 or 1.
# All other filesystems should have a pass number of 0 or greater than 1.
#
# See the manpage fstab(5) for more information.
#

# <fs>			<mountpoint>	<type>		<opts>		<dump/pass>

# NOTE: If your BOOT partition is ReiserFS, add the notail option to opts.
/dev/hdb1		/boot		ext2		defaults,noatime	1 2
/dev/hdb3		/		ext3		noatime		0 1
/dev/hdb2		none		swap		sw		0 0
/dev/cdrom		/mnt/cdrom	auto		noauto,user	0 0
#/dev/fd0		/mnt/floppy	auto		noauto		0 0

# glibc 2.2 and above expects tmpfs to be mounted at /dev/shm for 
# POSIX shared memory (shm_open, shm_unlink).
# (tmpfs is a dynamically expandable/shrinkable ramdisk, and will
#  use almost no memory if not populated with files)
shm			/dev/shm	tmpfs		nodev,nosuid,noexec	0 0

================================== sdb3/boot: ==================================

total 24388
drwxr-xr-x  2 root root     4096 2008-12-18 05:38 .
drwxr-xr-x 18 root root     4096 2008-12-19 06:33 ..
-rw-r--r--  1 root root 16417190 2008-12-18 05:38 initramfs-genkernel-x86-2.6.26-gentoo-r4
-rw-r--r--  1 root root  3890784 2008-12-18 04:56 kernel-2.6.26-gentoo-r4
-rw-r--r--  1 root root  3290336 2008-12-18 05:18 kernel-genkernel-x86-2.6.26-gentoo-r4
-rw-r--r--  1 root root  1325687 2008-12-18 05:18 System.map-genkernel-x86-2.6.26-gentoo-r4

=========================== Unknown MBRs or Boot Sectors =======================

Unknown MBR on /dev/sdc

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d5 50 88 46  |......u..1.F.P.F|
00000080  d2 be 68 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..h....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fc cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fc e9 c7 47 fd 92  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 33  ||U........R....3|
00000130  db 8a de 8b 46 0a 33 d2  83 e1 3f f7 f1 91 97 8b  |....F.3...?.....|
00000140  46 08 f7 f7 42 87 ca 3b  da 72 17 43 f7 f3 8a f2  |F...B..;.r.C....|
00000150  86 c5 d1 e8 d1 e8 0a c8  d0 cc d0 cc 0a f4 84 e4  |................|
00000160  74 02 b4 41 5b 8a d3 c3  0d 0a 4d 42 52 20 45 72  |t..A[.....MBR Er|
00000170  72 6f 72 20 00 0d 0a 00  72 65 73 73 20 61 6e 79  |ror ....ress any|
00000180  20 6b 65 79 20 74 6f 20  62 6f 6f 74 20 66 72 6f  | key to boot fro|
00000190  6d 20 66 6c 6f 70 70 79  2e 2e 2e 00 00 00 00 00  |m floppy........|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  6c 1d 86 59 00 00 80 01  |........l..Y....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 c2 52 54 57 00 00  |......?....RTW..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

No errors were reported.
```

Ok. I see the problem. 
The windows entry on the gentoo grub
```
title Windows XP
rootnoverify (hd1,0)
makeactive
chainloader +1
```
And my attempt at the chain loader to my gentoo disk
```
title Gentoo Linux 2.6.26-r4
root (hd1,0)
chainloader +1

```
are the same from the perspective of the second drive.
I figured out my problem thanks to you. Much appreciation. :D 
But the solution is beyond me as to how to fix the discrepancy.

---

### Post by caljohnsmith on 2009-01-06
It looks like you have XP installed to both sda1 and sda3, is that true? If the Windows you want to boot is on sda1, then in your Gentoo menu.lst you could use:
```
title Windows XP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

```
And that should work, assuming you boot the Gentoo drive. Note that it is important to include the mapping lines in order to trick Windows into thinking it is booting off the first boot drive (hd0) and not the second boot drive (hd1) where it really is. If you want to boot Gentoo from your Ubuntu menu.lst, you could do:
```
title Gentoo Linux
root (hd1,0)
configfile /boot/grub/menu.lst
```
If you want to instead chainload the Gentoo Grub, you first need to install Grub to its boot sector:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1,0)
grub> quit
```
And then you can use your chainloader entry in the Ubuntu menu.lst:
```
title Gentoo Linux
root (hd1,0)
chainloader +1
```
Let me know how that goes or if you run into problems. :)

---

### Post by ogredeschnique on 2009-01-06
I think there might be a bug in grub that causes grub to name the drives differently depending on where grub is installed. 
I do have grub installed on the gentoo boot partition. (hd1,0)
but the grub.conf on that partition looks like
```
title Gentoo Linux 2.6.26-r4
# Partition where the kernel image (or operating system) is located
root (hd0,2)
kernel (hd0,0)/boot/kernel-2.6.26-.gentoo.-r4 root=/dev/hdb3

title Gentoo Linux 2.6.26-r4 (rescue)
# Partition where the kernel image (or operating system) is located
root (hd0,0)
kernel /boot/kernel-2.6.26-gentoo-r4 root=/dev/hdb3 init=/bin/bb

title GenKernel
root (hd0,0)
kernel /boot/kernel-genkernel-x86-2.6.26-gentoo-r4 root=/dev/hdb3 init=/linuxrc ramdisk=8192 real_root=/dev/hdb3
initrd /boot/initramfs-genkernel-x86-2.6.26-gentoo-r4

```
and it works like that. It's the only way I could get it to boot. Is this a grub bug/feature where grub sees partitions and names them differently according to where it is operating from?
The current entry for gentoo on the ubuntu grub was exactly as you suggested
```
title Gentoo Linux
root (hd1,0)
chainloader +1
```
but that boots Windows, and is identical to the grub.conf entry for windows on the gentoo boot partition except for the "title". 
Windows is only installed on the first partition of the first drive, just like it likes to be. 
When grub is installed on (hd1,0) does it see that as (hd0,0)  from the perspective of the second drive? 
Because that is what I'm experiencing.

The "working" grub entry on [COLOR="Blue"]**(hd1,0)**[/COLOR]
```
title Gentoo Linux 2.6.26-r4
# Partition where the kernel image (or operating system) is located
root [COLOR="Blue"]**(hd0,2)**[/COLOR]
kernel [COLOR="Blue"]**(hd0,0)**[/COLOR]/boot/kernel-2.6.26-.gentoo.-r4 root=**[COLOR="Blue"]/dev/hdb3[/COLOR]**

```
That /dev/hdb3 would be (hd0,2) in grub terms.


[What if I delete the Windows entry grom the gentoo grub.conf since it is already in the ubuntu menu.lst. Then the chainload would work I think. Also I think that is where you got my second Windows install, the windows grub entry on the gentoo grub.conf. The first being the ubuntu menu.lst. I will try deleting the Wondows entry on the gentoo grub.conf.]

---

### Post by meierfra. on 2009-01-06
> causes grub to name the drives differently depending on where grub is installed.

The names depend on the drive you are booting from: During boot up, grub gets its information about the hard drives from the bios. The bios will always report the drive you are booting from as the first hard drive.  Grub starts counting at zero, so the boot drive will always be (hd0).  

> title Gentoo Linux
root (hd1,0)
chainloader +1

but that boots Windows, 

That is strange. A possible explanation:

When you boot from the Ubuntu drive, the bios report your drives in the order

/dev/sda  (hd0)
/dev/sdc  (hd1)
/dev/sdb  (hd2)


So (hd1,0) is your only partition on /dev/sdc. It has a Windows XP boot sector.   A Windows XP boot sector  always looks for the  boot files on  the drive you are booting from. (that's why you need the map lines for windows)  So it looks for the boot files on (hd0,0).  This happens to be your windows partitions and you end up booting into Windows.

But I'm not sure about this.  Anyway, I suggest to try
[B]
title Gentoo Linux 2.6.26-r4
kernel (hd2,0)/boot/kernel-2.6.26-.gentoo.-r4 root=/dev/hdb3[/B]


> What if I delete the Windows entry grom the gentoo grub.conf since it is already in the ubuntu menu.lst

That will not make any difference.

---

### Post by ogredeschnique on 2009-01-06
Yeah, I finally noticed that my external hard drive was getting in the way. That was my /dev/sdc. I pulled the usb cable for the external out of the computer, and now the chainloader to gentoo the second drive attempts to boot a stage2. Isn't that an attempt to boot the actual OS?

I'm slowly getting my head around this, but what I want is to be able to boot grub on /dev/sdb from /dev/sda*

THis isn't even my thread, so I won't be able to change the title to SOLVED, which will be disappointing to me after all this help.

---

### Post by caljohnsmith on 2009-01-06
> **ogredeschnique said:**
> Yeah, I finally noticed that my external hard drive was getting in the way. That was my /dev/sdc. I pulled the usb cable for the external out of the computer, and now the chainloader to gentoo the second drive attempts to boot a stage2. Isn't that an attempt to boot the actual OS?

I'm slowly getting my head around this, but what I want is to be able to boot grub on /dev/sdb from /dev/sda*

THis isn't even my thread, so I won't be able to change the title to SOLVED, which will be disappointing to me after all this help.
If you want to boot Grub on sdb from your sda drive, how about setting your BIOS to boot the sda drive, and then add this as an entry in your Ubuntu menu.lst:
```
title Gentoo HDD
rootnoverify (hd1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
I believe that should work assuming you only have the two drives connected (with sdc disconnected), but let us know if you run into problems.

---

### Post by ogredeschnique on 2009-01-06
That reloads the main ubuntu grub. Something tells me that it shouldn't.

---

### Post by caljohnsmith on 2009-01-06
> **ogredeschnique said:**
> That reloads the main ubuntu grub. Something tells me that it shouldn't.
So you are booting the Ubuntu drive, you added that entry from my previous post to your Ubuntu menu.lst, and using it reloads the Ubuntu Grub menu? How about posting the output of the script again so we can get a better idea of what's going on. Is your goal to boot from the Ubuntu sda drive on start up, and just have an entry in Grub to boot the sdb Gentoo drive? If not, please state clearly what you want to accomplish. :)

---

### Post by ogredeschnique on 2009-01-06
This thread is about chainloading. If I wanted something else I'd be in the wrong place. I would like to be able to boot from the sda grub to the sdb grub.

This info will be different as I got rid of some of the confusion and extra partitions that I was preparing. Oh, and that other windows install was a quick boot type OS for playing DVDs. either way it is gone now.

The second partition on sda is sda4. Is that an fstab issue? 
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of /dev/sdb1
                       and looks at sector 55431 of the same hard drive for
                       the stage2 file and on partition #1 for
                       /boot/grub/menu.lst .
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /grub/menu.lst
                       /boot/grub/grub.conf /grub/grub.conf /boot /boot/grub
                       /grub

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:   This is
    Boot files/dirs:   /etc/fstab /boot

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1ea71ea6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   135299429    67649683+   7  HPFS/NTFS
/dev/sda4       135299430   234436544    49568557+  83  Linux

sfdisk -V /dev/sda:

/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30e630e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63       80324       40131   83  Linux
/dev/sdb3           80325    77272649    38596162+  83  Linux

sfdisk -V /dev/sdb:

/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="98B8A48EB8A46C86" LABEL="OS" TYPE="ntfs"
/dev/sda4: UUID="d8c70ea2-e12c-4ca8-ab81-0e95586769b2" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb1: LABEL="/gentoo/boot" UUID="b7a614ac-8e57-4e3c-ba59-b6ec58d5168b" TYPE="ext2"
/dev/sdb3: LABEL="gentoo" UUID="d54f4427-08af-4cf0-9ef1-63993408bbb3" SEC_TYPE="ext2" TYPE="ext3"
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
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

=========================== sda4/boot/grub/menu.lst: ===========================

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
#timeout        0

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
# kopt=root=UUID=d8c70ea2-e12c-4ca8-ab81-0e95586769b2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=d8c70ea2-e12c-4ca8-ab81-0e95586769b2 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=d8c70ea2-e12c-4ca8-ab81-0e95586769b2 ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.2, memtest86+
root        (hd0,3)
kernel        /boot/memtest86+.bin
quiet


title        Gentoo HDD
rootnoverify     (hd1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        ---------Other---------
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows XP Media Center Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=d8c70ea2-e12c-4ca8-ab81-0e95586769b2 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
## usbfs is the USB group in sftab file:
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0

================================== sda4/boot: ==================================

total 54360
drwxr-xr-x  3 root root    4096 2009-01-06 21:07 .
drwxr-xr-x 21 root root    4096 2008-12-29 07:48 ..
-rw-r--r--  1 root root  422607 2008-04-10 16:51 abi-2.6.24-16-generic
-rw-r--r--  1 root root  422838 2008-11-24 22:47 abi-2.6.24-22-generic
-rw-r--r--  1 root root  422838 2008-11-27 22:13 abi-2.6.24-23-generic
-rw-r--r--  1 root root   79964 2008-04-10 16:51 config-2.6.24-16-generic
-rw-r--r--  1 root root   80062 2008-11-24 22:47 config-2.6.24-22-generic
-rw-r--r--  1 root root   80051 2008-11-27 22:13 config-2.6.24-23-generic
drwxr-xr-x  2 root root    4096 2009-01-06 18:13 grub
-rw-r--r--  1 root root 7503114 2008-11-30 01:49 initrd.img-2.6.24-16-generic
-rw-r--r--  1 root root 7892413 2008-11-29 13:22 initrd.img-2.6.24-16-generic.bak
-rw-r--r--  1 root root 7504184 2008-11-30 05:56 initrd.img-2.6.24-22-generic
-rw-r--r--  1 root root 7503341 2008-11-30 01:57 initrd.img-2.6.24-22-generic.bak
-rw-r--r--  1 root root 7503798 2009-01-06 21:07 initrd.img-2.6.24-23-generic
-rw-r--r--  1 root root 7504951 2008-12-17 19:28 initrd.img-2.6.24-23-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r--  1 root root  899892 2008-04-10 16:51 System.map-2.6.24-16-generic
-rw-r--r--  1 root root  905617 2008-11-24 22:47 System.map-2.6.24-22-generic
-rw-r--r--  1 root root  905633 2008-11-27 22:13 System.map-2.6.24-23-generic
-rw-r--r--  1 root root 1904248 2008-04-10 16:51 vmlinuz-2.6.24-16-generic
-rw-r--r--  1 root root 1921176 2008-11-24 22:47 vmlinuz-2.6.24-22-generic
-rw-r--r--  1 root root 1921976 2008-11-27 22:13 vmlinuz-2.6.24-23-generic

=============================== sda4/boot/grub: ===============================

total 212
drwxr-xr-x 2 root root   4096 2009-01-06 18:13 .
drwxr-xr-x 3 root root   4096 2009-01-06 21:07 ..
-rw-r--r-- 1 root root    197 2008-11-29 13:22 default
-rw-r--r-- 1 root root     45 2008-11-29 13:22 device.map
-rw-r--r-- 1 root root   8056 2008-11-29 13:22 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-11-29 13:22 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-11-29 13:22 installed-version
-rw-r--r-- 1 root root   8608 2008-11-29 13:22 jfs_stage1_5
-rw-r--r-- 1 root root   4666 2009-01-06 18:13 menu.lst
-rw-r--r-- 1 root root   4787 2008-12-17 19:28 menu.lst~
-rw-r--r-- 1 root root   7324 2008-11-29 13:22 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-11-29 13:22 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-11-29 13:22 stage1
-rw-r--r-- 1 root root 108356 2008-11-29 13:22 stage2
-rw-r--r-- 1 root root   9276 2008-11-29 13:22 xfs_stage1_5

=========================== sdb1/boot/grub/menu.lst: ===========================


============================= sdb1/grub/menu.lst: =============================


========================== sdb1/boot/grub/grub.conf: ==========================

ch listing to boot as default. 0 is the first, 1 the second etc.
default 0
# How many seconds to wait before the default listing is booted.
# timeout 30
# Nice, fat splash-image to spice things up :)
# Comment out if you don't have a graphics card installed
splashimage=(hd0,0)/boot/grub/splash.xpm.gz
#
title Gentoo Linux 2.6.26-r4
# Partition where the kernel image (or operating system) is located
root (hd0,2)
kernel (hd0,0)/boot/kernel-2.6.26-.gentoo.-r4 root=/dev/hdb3

title Gentoo Linux 2.6.26-r4 (rescue)
# Partition where the kernel image (or operating system) is located
root (hd0,0)
kernel /boot/kernel-2.6.26-gentoo-r4 root=/dev/hdb3 init=/bin/bb

title GenKernel
root (hd0,0)
kernel /boot/kernel-genkernel-x86-2.6.26-gentoo-r4 root=/dev/hdb3 init=/linuxrc ramdisk=8192 real_root=/dev/hdb3
initrd /boot/initramfs-genkernel-x86-2.6.26-gentoo-r4

# The next four lines are only if you dualboot with a Windows system.
# In this case, Windows is hosted on /dev/sdb1 in relation to THIS DRIVE.
#title Windows XP
#rootnoverify (hd1,0)
#makeactive
#chainloader +1
#

============================= sdb1/grub/grub.conf: =============================

ch listing to boot as default. 0 is the first, 1 the second etc.
default 0
# How many seconds to wait before the default listing is booted.
# timeout 30
# Nice, fat splash-image to spice things up :)
# Comment out if you don't have a graphics card installed
splashimage=(hd0,0)/boot/grub/splash.xpm.gz
#
title Gentoo Linux 2.6.26-r4
# Partition where the kernel image (or operating system) is located
root (hd0,2)
kernel (hd0,0)/boot/kernel-2.6.26-.gentoo.-r4 root=/dev/hdb3

title Gentoo Linux 2.6.26-r4 (rescue)
# Partition where the kernel image (or operating system) is located
root (hd0,0)
kernel /boot/kernel-2.6.26-gentoo-r4 root=/dev/hdb3 init=/bin/bb

title GenKernel
root (hd0,0)
kernel /boot/kernel-genkernel-x86-2.6.26-gentoo-r4 root=/dev/hdb3 init=/linuxrc ramdisk=8192 real_root=/dev/hdb3
initrd /boot/initramfs-genkernel-x86-2.6.26-gentoo-r4

# The next four lines are only if you dualboot with a Windows system.
# In this case, Windows is hosted on /dev/sdb1 in relation to THIS DRIVE.
#title Windows XP
#rootnoverify (hd1,0)
#makeactive
#chainloader +1
#

================================== sdb1/boot: ==================================

lrwxrwxrwx 1 root root 1 2008-12-16 23:08 sdb1/boot -> .

=============================== sdb1/boot/grub: ===============================

total 334
drwxr-xr-x 2 root root   1024 2009-01-06 06:38 .
drwxr-xr-x 4 root root   1024 2008-12-17 20:00 ..
-rw-r--r-- 1 root root    197 2008-12-17 12:51 default
-rw-r--r-- 1 root root     45 2008-12-17 12:27 device.map
-rw-r--r-- 1 root root   8064 2008-12-17 12:51 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-12-17 12:51 fat_stage1_5
-rw-r--r-- 1 root root   7200 2008-12-17 12:51 ffs_stage1_5
-rw-r--r-- 1 root root   1072 2009-01-06 06:38 grub.conf
-rw-r--r-- 1 root root   7200 2008-12-17 12:51 iso9660_stage1_5
-rw-r--r-- 1 root root   8640 2008-12-17 12:51 jfs_stage1_5
lrwxrwxrwx 1 root root      9 2008-12-17 12:27 menu.lst -> grub.conf
-rw-r--r-- 1 root root   7328 2008-12-17 12:51 minix_stage1_5
-rw-r--r-- 1 root root   9728 2008-12-17 12:51 reiserfs_stage1_5
-rw-r--r-- 1 root root  33856 2008-12-17 12:27 splash.xpm.gz
-rw-r--r-- 1 root root    512 2008-12-17 12:51 stage1
-rw-r--r-- 1 root root 105372 2008-12-17 12:51 stage2
-rw-r--r-- 1 root root 105372 2008-12-17 12:27 stage2_eltorito
-rw-r--r-- 1 root root   7520 2008-12-17 12:51 ufs2_stage1_5
-rw-r--r-- 1 root root   6752 2008-12-17 12:51 vstafs_stage1_5
-rw-r--r-- 1 root root   9384 2008-12-17 12:51 xfs_stage1_5

================================== sdb1/grub: ==================================

total 334
drwxr-xr-x 2 root root   1024 2009-01-06 06:38 .
drwxr-xr-x 4 root root   1024 2008-12-17 20:00 ..
-rw-r--r-- 1 root root    197 2008-12-17 12:51 default
-rw-r--r-- 1 root root     45 2008-12-17 12:27 device.map
-rw-r--r-- 1 root root   8064 2008-12-17 12:51 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-12-17 12:51 fat_stage1_5
-rw-r--r-- 1 root root   7200 2008-12-17 12:51 ffs_stage1_5
-rw-r--r-- 1 root root   1072 2009-01-06 06:38 grub.conf
-rw-r--r-- 1 root root   7200 2008-12-17 12:51 iso9660_stage1_5
-rw-r--r-- 1 root root   8640 2008-12-17 12:51 jfs_stage1_5
lrwxrwxrwx 1 root root      9 2008-12-17 12:27 menu.lst -> grub.conf
-rw-r--r-- 1 root root   7328 2008-12-17 12:51 minix_stage1_5
-rw-r--r-- 1 root root   9728 2008-12-17 12:51 reiserfs_stage1_5
-rw-r--r-- 1 root root  33856 2008-12-17 12:27 splash.xpm.gz
-rw-r--r-- 1 root root    512 2008-12-17 12:51 stage1
-rw-r--r-- 1 root root 105372 2008-12-17 12:51 stage2
-rw-r--r-- 1 root root 105372 2008-12-17 12:27 stage2_eltorito
-rw-r--r-- 1 root root   7520 2008-12-17 12:51 ufs2_stage1_5
-rw-r--r-- 1 root root   6752 2008-12-17 12:51 vstafs_stage1_5
-rw-r--r-- 1 root root   9384 2008-12-17 12:51 xfs_stage1_5

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# noatime turns off atimes for increased performance (atimes normally aren't
# needed; notail increases performance of ReiserFS (at the expense of storage
# efficiency).  It's safe to drop the noatime options if you want and to
# switch between notail / tail freely.
#
# The root filesystem should have a pass number of either 0 or 1.
# All other filesystems should have a pass number of 0 or greater than 1.
#
# See the manpage fstab(5) for more information.
#

# <fs>            <mountpoint>    <type>        <opts>        <dump/pass>

# NOTE: If your BOOT partition is ReiserFS, add the notail option to opts.
/dev/hdb1        /boot        ext2        defaults,noatime    1 2
/dev/hdb3        /        ext3        noatime        0 1
/dev/hdb2        none        swap        sw        0 0
/dev/cdrom        /mnt/cdrom    auto        noauto,user    0 0
#/dev/fd0        /mnt/floppy    auto        noauto        0 0

# glibc 2.2 and above expects tmpfs to be mounted at /dev/shm for
# POSIX shared memory (shm_open, shm_unlink).
# (tmpfs is a dynamically expandable/shrinkable ramdisk, and will
#  use almost no memory if not populated with files)
shm            /dev/shm    tmpfs        nodev,nosuid,noexec    0 0

================================== sdb3/boot: ==================================

total 24388
drwxr-xr-x  2 root root     4096 2008-12-18 05:38 .
drwxr-xr-x 18 root root     4096 2008-12-19 06:33 ..
-rw-r--r--  1 root root 16417190 2008-12-18 05:38 initramfs-genkernel-x86-2.6.26-gentoo-r4
-rw-r--r--  1 root root  3890784 2008-12-18 04:56 kernel-2.6.26-gentoo-r4
-rw-r--r--  1 root root  3290336 2008-12-18 05:18 kernel-genkernel-x86-2.6.26-gentoo-r4
-rw-r--r--  1 root root  1325687 2008-12-18 05:18 System.map-genkernel-x86-2.6.26-gentoo-r4

=============================== StdErr Messages: ===============================

No errors were reported.

```

---

### Post by meierfra. on 2009-01-06
You bios seem to behave like mine. If I use

root (hd1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

it also still boots from the boot drive.

Try

title Gentoo
root (hd0)
map (hd1) (hd0)
chainloader +1


and 

title Gentoo
root (hd1)
map  (hd1) (hd0)
chainloader +1

I know that this makes no sense, but both of those  work for me.
You can also try rootnoverify in place of root, but that did not make any difference for me.

---

### Post by ogredeschnique on 2009-01-06
Unrecognized device string. both ways. 

@meierfra:
I totally understand that you mean about some of this stuff making no sense.
I feel like someone who knew what they were doing #-o could have it working in a flash. I guess that's kind of a joke.

---

### Post by meierfra. on 2009-01-06
```
Unrecognized device string. both 
```

Sound like a typo. For example there needs to be a space between (hd0) and (hd1) in  map (hd0) (hd1)

Also  where should  be no space between + and 1 in chainloader +1.

Just copy and paste my entries. That should avoid any typos.

---

### Post by ogredeschnique on 2009-01-07
> **meierfra. said:**
> Sound like a typo. For example there needs to be a space between (hd0) and (hd1) in  map (hd0) (hd1).
Awesome. That works. 
Thank you meiefra.
And thank you caljohnsmith for your patience and perseverance. 

The best part is I learned something, with the help of others. Now I'll never have trouble with this exact problem again.  :D

---

### Post by meierfra. on 2009-01-07
Glad you  got it to work.  Chain loading a partition on a different hard drive can be tricky, in particular if on  tries to set it up so that the drives stay independent: You can boot into Gentoo not only from the Ubuntu Grub menu, but also  by setting your bios to boot from the Gentoo drive. So if your Ubuntu partition gets corrupted you still will be able boot into Gentoo.


Could you do me a favour?  There seems to be a small bug in the script.:

>  Operating System:   This is 

That line in RESULT.txt really should have said "Gentoo" somewhere.

Next time you boot into Gentoo, could you  open a terminal  a post the output of

```
cat  /etc/issue
```

Thanks

---

### Post by ogredeschnique on 2009-01-07
Now, this is my first gentoo install, so take it easy. lol:wink:
```
This is \n.\O (\s \m \r) \t
```

---

