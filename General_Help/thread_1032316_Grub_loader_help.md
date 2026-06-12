---
title: "Grub loader help"
date: 2009-01-06
forum: General Help
---

### Post by warren181 on 2009-01-06
Hi everyone

im new to linux it general. i resently installed ubuntu which works well but i want to keep it completly seperate from my XP partition. i currently have 2 Hard Disks. the first with XP on it and the second with Ubuntu on it. what i want to do is remove the grub boot loader so that when i turn on my computer it boots strait into XP unless i press F8 and change the boot proity to the second Hard Disk.

I appreciate any help that can be given

thanks Warren

---

### Post by lswb on 2009-01-06
If I understand correctly, F8 accesses the BIOS at boot and you are switching HD there to select the boot drive?

If I could suggest an alternative, you can edit your grub menu so that XP is the default OS and boots automatically after a timeout period of your choice. That way you can select your boot OS without needing to access the BIOS, and your statup time will be that much quicker.

If you still want to switch via the BIOS, you will need to restore the Windows MBR to the windows drive and install grub to the MBR of the linux drive. This site will explain how to do it either way:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by warren181 on 2009-01-06
Thanks for that, the website has some useful information. but i cant find the bid on booting the hard disks seperatly. could you please either give the exact URL or discribe how to do it your self.

thank you for your time

Warren

---

### Post by caljohnsmith on 2009-01-06
If you would like some specific help about how to set up your drives independent of each other as far as booting is concerned, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and what it might take to set up your dual boot.

---

### Post by warren181 on 2009-01-06
Ok here is the code

```
#!/bin/bash
#to use this script:
#
#sudo bash boot_info_script.txt
#
#date  1/5/09
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

###### check whether user is root
if [ $(whoami) != "root" ];
then 
   echo  Please use \"sudo\" or become \"root\" to run this script. >&2;
   exit 1;
fi;  

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
#############################################################################################
##########  Determine the embeded location of stage 2  in a stage 1 file,
##########  look  for the stage 2 and, if found, determine the
#########$  the location and the path of the embedded menu.lst

stage2_loc (){
  #echo Entering stage2 function 
  local stage1=$1;
  offset=$(hexdump -s 0x44 -n 4 -e '4 "%u"' $stage1 2>>$Trash);
  dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $stage1);
  pa="T"
  Grub_Version="";
  for hdd in $Hard_Drives;
  do
     if [ $offset -lt  $((2*$(sfdisk -s $hdd))) ];
     then
	 tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump    -n 4 -e '"%x"');
         if [ "$tmp" = 3be5652 ];  ###  If stage2 files was found.
         then
              dd if=$hdd skip=$((offset+1)) count=1 of=$Tmp_Log 2>>$Trash;
              pa=$(hexdump  -s 0xa  -n 1 -e '"%d"' $Tmp_Log);
              stage2_hdd=$hdd;
              Grub_String=$(hexdump -v -s 0x12 -n 94 -e '"%_u"' $Tmp_Log);
              Grub_Version=$(echo $Grub_String|sed -e  s/nul[^$]*//);
              BL=$BL$Grub_Version;
              menu=$(echo $Grub_String |sed -e  s/[^\/]*// -e s/nul[^$]*//);
         fi;
     fi;
 done;
 dr=$((dr-127))
 Stage2_Msg=$(echo  looks at sector $offset )        
 if [ "$dr" = 128 ];
 then
      Stage2_Msg=$(echo $Stage2_Msg of the same hard drive) 
 else
      Stage2_Msg=$(echo $Stage2_Msg on boot drive \#$dr)
 fi;
 Stage2_Msg=$(echo $Stage2_Msg for the stage2 file);
                    
 if [ "$pa" = "T"  ]   #### no stage 2 file found.
 then
      Stage2_Msg=$(echo $Stage2_Msg, but no stage2 files can be found at this location); 
 else
     pa=$((pa+1))
     Stage2_Msg=$(echo $Stage2_Msg  and on )                       
     if [ "$pa" = 256 ];
     then
         Stage2_Msg=$(echo $Stage2_Msg the same partition) 
     else
         Stage2_Msg=$(echo $Stage2_Msg  partition \#$pa )
     fi;
     Stage2_Msg=$(echo $Stage2_Msg for  $menu.)
  fi;
}
#######################################################################################


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
Trash=$Folder/Trash             #  File to catch all usual Standard Errors
                                #these messagges will not be included in the RESULTS       
Mount_Error=$Folder/Mount_Error # File to catch Mounting Errors
Unknown_MBR=$Folder/Unknown_MBR # File to record all unknown MBR and Boot sectors. 
Tmp_Log=$Folder/Tmp_Log         # File to temporarily hold some information.

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
	eb48) dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $drive);
              offset=$(hexdump -s 0x44 -n 4 -e '"%u"' $drive);
              if  [ "$offset" != 1 ];   ###if  Grub is installed without stage1.5 files 
	      then
                  stage2_loc $drive;
                  Message=$(echo $Message and  $Stage2_Msg)
 	      else                         ### if grub is installed with stage1.5 files
                  Grub_String=$(hexdump -v -s 0x412 -n 94 -e '"%_u"' $drive);
                  Grub_Version=$(echo $Grub_String|sed -e  s/nul[^$]*//);
                  stage=$(echo  $Grub_String | sed -e  s/" "[^$]*// -e s/[^\/]*//);
                  menu=$(echo $Grub_String |sed -e  s/[^" "]*" "// -e s/nul[^$]*//);
                  [[ "$menu" = "" ]] || stage=$(echo $stage and $menu);
                  part_info=$((1045 + ${#Grub_Version}));
	          pa=$(hexdump -s $part_info  -n 1 -e '"%d"' $drive);
                  part_info=$((part_info+1));
                  dr=$(hexdump -s $part_info -n 1 -e '"%d"' $drive);
                  dr=$((dr-127));
		  pa=$((pa+1));
		  if [ $dr = 128 ];
                  then
                       Message=$(echo $Message and looks on the same drive in partition \#$pa for $stage.)
                  else
                      Message=$(echo $Message and looks  on boot drive \#$dr in partition \#$pa for $stage.)
              fi;
	    fi;
            BL=Grub$Grub_Version;; 
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
            e9d8) BST="Windows Vista";;
             10f) BST="HP Recovery";;
            3a5e) BST="Recovery:Fat 32";;
            89e) BST="MSDOS5.0: Fat 16";;
            bd0) BST="MSWIN4.1: Fat 32";;
            7cc6)BST="MSWIN4.1: Fat 32";;
            7405) BST="Vista:  Fat 32";;
            e00) BST="Dell Utility: Fat16";;           
	    5272) BST=Grub;
                  stage2_loc $part;
                  BSI=$(echo $BSI Grub$Grub_Version is installed in the boot sector of $part  and $Stage2_Msg);;
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
	    if [[ "$offset" != "$real_offset" ]] 
            then
                BSI=$(echo $BSI"  "According to the info in the boot sector, $name starts at sector $offset.)
                if [[ "$offset" != "63" ||  $part_number -lt 5 ]]
                then
                    BSI=$(echo $BSI" "But according to the info  from fdisk, $name starts at sector   $real_offset.);
                 fi;
            fi;
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
            if [[ "$offset" != "$real_offset" ]] 
            then
                BSI=$(echo $BSI"  "According to the info in the boot sector, $name starts at sector $offset.)
                if [[ "$offset" != "63" ||  $part_number -lt 5 ]]
                then
                    BSI=$(echo $BSI" "But according to the info  from fdisk, $name starts at sector   $real_offset.);
                fi;
            fi;         
            [[ "$Comp_Size" = "0"  ]]  ||  BSI=$(echo $BSI"  "According to the info in the boot sector, $name has    $BPB_Part_Size sectors, but according to the info  from fdisk, it has  $Real_Part_Size sectors.);
              
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
                      sig=$(hexdump -s 0x101 -n 8  -e '8/1 "%_p"' $name$file$loader);
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
                          stage2_loc  $name$file$loader;
                          BSI=$(echo $BSI" "Grub$Grub_Version in the file  $file$loader $Stage2_Msg)
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
exit
```

---

### Post by caljohnsmith on 2009-01-06
It looks like you accidentally posted the boot_info_script.txt file instead of the RESULTS.txt file; please post the contents of the RESULTS.txt file. :)

---

### Post by warren181 on 2009-01-06
ok sorry for that the terminal confused me here is the RESULTS.txt

```
============================= Boot Info Summary: ==============================

 => Drive sdc does not have a valid partition table.
 => Drive sdd does not have a valid partition table.
 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sdb2: _________________________________________________________________________

    File system:       Extended Partition

sdb5: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x99039903

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   409593239   204796588+   7  HPFS/NTFS
/dev/sda2       409593240   976768064   283587412+   f  W95 Ext'd (LBA)
/dev/sda5       409593303   450558989    20482843+   7  HPFS/NTFS
/dev/sda6       511991613   614389859    51199123+   7  HPFS/NTFS
/dev/sda7       614389923   655355609    20482843+   7  HPFS/NTFS
/dev/sda8       655355673   901117979   122881153+   7  HPFS/NTFS

sfdisk -V /dev/sda:

partition 2: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 5: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition [6]: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 6: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition [7]: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 7: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
partition [8]: start: (c,h,s) expected (1023,254,63) found (1023,0,1)
partition 8: start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda: OK

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x22186085

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   390620474   195310206   83  Linux
/dev/sdb2       390620475   394524269     1951897+   5  Extended
/dev/sdb5       390620538   394524269     1951866   82  Linux swap / Solaris

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

sfdisk -V /dev/sdc:

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

sfdisk -V /dev/sdd:

/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="8894E10894E0FA18" TYPE="ntfs" 
/dev/sda5: UUID="DC040EBA040E9822" LABEL="Home" TYPE="ntfs" 
/dev/sda6: UUID="5E44755B447536BD" LABEL="Games" TYPE="ntfs" 
/dev/sda7: UUID="7E6CC9796CC92CA9" LABEL="Software" TYPE="ntfs" 
/dev/sda8: UUID="1AFCBB10FCBAE563" LABEL="itunes" TYPE="ntfs" 
/dev/sdb1: UUID="1b04abb5-bbfd-4e67-ae34-481c7c2c2d1e" TYPE="ext3" 
/dev/sdb5: UUID="690981e8-7002-4496-8a1e-c2e57cde7a79" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/james/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=james)

================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdb1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=1b04abb5-bbfd-4e67-ae34-481c7c2c2d1e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1b04abb5-bbfd-4e67-ae34-481c7c2c2d1e

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		1b04abb5-bbfd-4e67-ae34-481c7c2c2d1e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1b04abb5-bbfd-4e67-ae34-481c7c2c2d1e ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		1b04abb5-bbfd-4e67-ae34-481c7c2c2d1e
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1b04abb5-bbfd-4e67-ae34-481c7c2c2d1e ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		1b04abb5-bbfd-4e67-ae34-481c7c2c2d1e
kernel		/boot/memtest86+.bin
quiet

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


=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=1b04abb5-bbfd-4e67-ae34-481c7c2c2d1e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=690981e8-7002-4496-8a1e-c2e57cde7a79 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================== sdb1/boot: ==================================

total 11948
drwxr-xr-x  3 root root    4096 2009-01-05 20:38 .
drwxr-xr-x 20 root root    4096 2009-01-05 20:38 ..
-rw-r--r--  1 root root  507665 2008-10-24 09:29 abi-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-10-24 09:29 config-2.6.27-7-generic
drwxr-xr-x  2 root root    4096 2009-01-05 20:39 grub
-rw-r--r--  1 root root 8179690 2009-01-05 20:38 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root  124152 2008-09-11 21:11 memtest86+.bin
-rw-r--r--  1 root root 1029585 2008-10-24 09:29 System.map-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-10-24 09:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root 2244272 2008-10-24 09:29 vmlinuz-2.6.27-7-generic

=============================== sdb1/boot/grub: ===============================

total 216
drwxr-xr-x 2 root root   4096 2009-01-05 20:39 .
drwxr-xr-x 3 root root   4096 2009-01-05 20:38 ..
-rw-r--r-- 1 root root    197 2009-01-05 20:38 default
-rw-r--r-- 1 root root     30 2009-01-05 20:38 device.map
-rw-r--r-- 1 root root   8108 2009-01-05 20:38 e2fs_stage1_5
-rw-r--r-- 1 root root   7856 2009-01-05 20:38 fat_stage1_5
-rw-r--r-- 1 root root     16 2009-01-05 20:38 installed-version
-rw-r--r-- 1 root root   8712 2009-01-05 20:38 jfs_stage1_5
-rw-r--r-- 1 root root   4621 2009-01-05 20:39 menu.lst
-rw-r--r-- 1 root root   7352 2009-01-05 20:38 minix_stage1_5
-rw-r--r-- 1 root root   9756 2009-01-05 20:38 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2009-01-05 20:38 stage1
-rw-r--r-- 1 root root 121460 2009-01-05 20:38 stage2
-rw-r--r-- 1 root root   9556 2009-01-05 20:38 xfs_stage1_5

=============================== StdErr Messages: ===============================

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading
```

by the way can i still use ctrl + c and ctrl + v to copy and paste in ubuntu

thanks

warren

---

### Post by caljohnsmith on 2009-01-06
[QUOTE=warren181]by the way can i still use ctrl + c and ctrl + v to copy and paste in ubuntu[/QUOTE]
If you mean copy/paste from the terminal, it is actually Ctrl-Shift-C or V, because Ctrl-C and Ctrl-V have special meaning in the terminal (i.e. Ctrl-C for example is used to interrupt a currently running program). Most other apps use the standard Ctrl-C or V though.

But about your booting problem, how about doing the following in a terminal (Applications > Accessories > Terminal):
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
That will restore a Windows MBR (Master Boot Record) to your Windows sda drive, so you should be able to boot directly into Windows again when you boot that drive. To install Grub to the MBR of your sdb drive, you could do:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1) 
grub> quit
```
And please post the output of the above commands before doing the "quit". Next open up your Grub's menu.lst:
```
sudo mount /dev/sdb1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And at the bottom where it has the Windows entry, change it to:
```
title       Windows XP
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Save, reboot, set your BIOS to boot the Ubuntu sdb drive, and you should get the Grub menu on start up; if all goes well you should also be able to boot both Ubuntu and Windows from your Grub menu. Let me know how it goes or if you run into problems.

---

### Post by warren181 on 2009-01-06
That looks good and I will try it tomorrow. one thing that I'm not sure about is the first 2 bits of code you have put down where do I type them in.

thanks for your help

warren

---

### Post by warren181 on 2009-01-10
this is the result
```

grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

```

but when i try to bring up the menu.1st it come up blank

any idears

warren

---

### Post by fubbleskag on 2009-01-10
it's **menu.lst** - that's an L not the number 1 :)

---

### Post by ranch hand on 2009-01-10
Try  gksudo gedit /boot/grub/menulst

---

### Post by warren181 on 2009-01-10
Hey dude

thanks for the help i can now boot straight into XP or press F8 to boot into ubuntu

again thanks

warren

---

### Post by caljohnsmith on 2009-01-10
Glad to hear it all worked out OK; cheers and have fun with Windows and Ubuntu. :)

---

