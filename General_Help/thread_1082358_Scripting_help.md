---
title: "Scripting help"
date: 2009-02-27
forum: General Help
---

### Post by BOOBOOJS on 2009-02-27
does anyone know how to reformat the output of
find /directory -print and or
tar -ztf archive.tar.gz 

I am attempting to write a script that:

first runs find to create a list of files that should be present in the backup
find /directory -print >> find.log

then creates the backup with
tar -czpf $backup_archive $backup_dir $exclude_dir

then runs tar to create a list of files actually backed up
tar -ztf $backup_archive >> tar.log

And the compares them with diff
diff -i find.log tar.log >> not_backed_up.log

Here is the complete script.. I'm getting better at BASH!

```

#!/bin/bash
##
## This is a backup script authored by Jonathan Selfridge and is licecensed under the GPLv2
##
#################################################################################################################################################################################################################################
## Declare Variables
#################################################################################################################################################################################################################################
#Sets the date for backup file names
Arc_Date=`date +%Y.%m.%d`
#Location to save backup to                                                                                                 
Backup_File_Location="/home/ubuntu/backup/" 
#Directory to start backup from                                                                                   
Backup_Start_Location="/"    
#Dir to be backed up                                                                                                
Backup_DIR="/home"
#Location to Save Log files to                                                                                                               
Log_Location="$Backup_File_Location""Log" 
#Set the tar options (DO NOT ADD -f or -c) c=create archive v=verbose p=preserve permissions z=gzip (can use j instead if you would like it bzipped - slower) 
TAR_OPTS="zvP"
#Extention for archive (should match tar options                                                                 
TAR_EXT=".tar.gz"            
#Items to be excluded from backup (must have --exclude= as shown)                                               
Exclude_DIRS="--exclude=/tmp --exclude=/mnt --exclude=/media --exclude=/proc --exclude=$Backup_File_Location"   
#Do you want your archive split? 1=yes any other number = no (must be a number)  
Run_Split="1"  
#Size to splt TAR files to                                                                                                           
Split_Size="4378m" 
#Do you want to run DD to create a MBR backup? 1=yes any other number = no (must be a number)                                                  
Run_DD="1"   
#Device you want to backup the MBR of with DD (exsample /dev/sda)                                                            
Device_DD="/dev/sda" 
#Location to put the DD backup                                                                                                        
Output_DD="$Backup_File_Location$Arc_Date.dd"
#Set Location of binaries this app needs
tar=/bin/tar
dd=/bin/dd
split=/usr/bin/split                                                                    
#################################################################################################################################################################################################################################
##
##
printf "%s\n" "$Arc_Date"
##
## Send Date Stamp to log
printf "%s\n" "Backup Started -- `date`" >> ~/"$Arc_Date.log"
##
printf "%s\n" "Preforming Sanity Checks" >> ~/"$Arc_Date.log"
## Make sure that the Backup Dir exists
#
if [ ! -d "$Backup_File_Location" ]; then
    printf "%s\n" "$Backup_File_Location" "Backup File Location Does not exist: Exiting" >> ~/"$Arc_Date.log"
    exit 192
fi
#
## Make sure the Backup DIR exists
#
if [ ! -d "$Backup_DIR" ]; then
    printf "%s\n" "$Backup_DIR" "Directory to be backed up Does not exist: Exiting" >> ~/"$Arc_Date.log"
    exit 192
fi
#
## Make sure the Backup Start Location exists
#
if [ ! -d "$Backup_Start_Location" ]; then
    printf "%s\n" "$Backup_Start_Location" "Backup Start Location Does not exist: Exiting" >> ~/"$Arc_Date.log"
    exit 192
fi
#
## Make sure the Log Location exists
#
if [ ! -d "$Log_Location" ]; then
    printf "%s\n" "$Log_Location" "Log Location does not exist: Exiting" >> ~/"$Arc_Date.log"
    exit 192
fi
#
## Make sure that tar exits
#
if [ ! -x "$tar" ]; then
    printf "%s\n" "tar does not exist please correct your path variable - Aborting" >> ~/"$Arc_Date.log"
    exit 192
fi
#
## Make sure that split exists
#
if [ ! -x "$split" ]; then
    printf "%s\n" "split does not exist please correct your path variable or comment out split from this script - Aborting" >> ~/"$Arc_Date.log"
    exit 192 
fi
#
## Make sure dd exists
#
if [ ! -x "$dd" ]; then
    printf "%s\n" "dd does not exist please correct your path variable or comment out dd from this script - Aborting"  >> ~/"$Arc_Date.log"
    exit 192
fi
##
printf "%s\n" "Sanity Checks finished" >> ~/"$Arc_Date.log"
#
#Print file list that we can compare with the archive
find $Backup_DIR  -print >> ~/"$Arc_Date.find.log"
#
## Run DD if needed
#
case $Run_DD in
1)
    printf "%s\n" "Run DD set to 1, Running DD" >> ~/"$Arc_Date.log"
    dd if="$Device_DD" bs=512 count=1 of="$Output_DD"
    ;;
*)
    printf "%s\n" "Skipped DD -- Run_DD set to other than 1" >> ~/"$Arc_Date.log"
    ;;
esac
#
## Split archive if needed
#
case $Run_Split in
1)
     printf "%s\n" "Creating Archive -- Splitting into $Split_Size files" >> ~/"$Arc_Date.log"
     cd "$Backup_Start_Location"
     mkdir "$Backup_File_Location$Arc_Date"
     tar -c -$TAR_OPTS "$Exclude_DIRS" -f - "$Backup_DIR" | split -b "$Split_Size" - \
          "$Backup_File_Location$Arc_Date/Backup$Arc_Date$TAR_EXT" >> ~/"$Arc_Date.log"
     printf "%s\n" "Backup Finished -- `date`" >> ~/"$Arc_Date.log"
     printf "%s\n" "Building Archive File List" >> ~/"$Arc_Date.log"
     cat "$Backup_File_Location$Arc_Date/Backup$Arc_Date$TAR_EXT"* | tar -zt  >> ~/"$Arc_Date.tar.log"
     printf "%s\n" "Moving logs to Log_Location" >> ~/"$Arc_Date.log"
     mkdir $Log_Location
     mv ~/*log "$Log_Location/"
     ;;
*)
     printf "%s\n" "Skipped Split -- Run_Split set to other than 1" >> ~/"$Arc_Date.log"
     printf "%s\n" "Creating Archive"\n >>"~/$Arc_Date.log"
     cd "$Backup_Start_Location"
     mkdir "$Backup_File_Location""$Arc_Date"
     tar -c -"$TAR_OPTS" -f "$Backup_File_Location$Arc_Date/Backup$Arc_Date$TAR_EXT" "$Backup_DIR" "$Exclude_DIRS" >> ~/"$Arc_Date.log"
     printf "%s\n" "Backup Finished -- $Date" >> ~/"$Arc_Date.log"
     printf "%s\n" "Building Archive File List" >> ~/"$Arc_Date.log"
     tar -ztf "$Backup_File_Location$Arc_Date/Backup$Arc_Date$TAR_EXT" >> ~/"$Arc_Date.tar.log"
     printf "%s\n" "Moving log to Log_Location" >> ~/"$Arc_Date.log"
     mkdir $Log_Location
     mv ~/*log "$Log_Location/"
     ;;
esac
exit
```

---

### Post by heindsight on 2009-02-27
I'm not sure I understand exactly what your problem is. find -print will print a list of files found and tar -t will print a list of files in the archive, so I don't think you really need to do any formatting. However, if you want, you could use the -printf action with the find command to format your output any way you want. Have a look at the manual:
```
man find
```for details.

By the way, if you want to compare the output from find and tar, you may want to sort it first, just to make sure that differences encountered are not simply due to differences in ordering...

---

### Post by BOOBOOJS on 2009-02-27
I am having issues added or removing trailing and leading slashes so that their output matches line for line. Is there a way to compare them with diff ignoring those discrepancies, or a way to reformat the output with awk or grep etc?

---

### Post by heindsight on 2009-02-28
I see what you mean.

Doing a comparison like this will always be a bit tricky. If you want it to work, you should make sure to supply the same path to find as to tar, that way the leading portion of the paths printed by tar -t and find -print will be the same (except perhaps if you used absolute paths in which case tar will strip off leading slashes).

If you use absolute pathnames, you could either supply the -P option to tar when you're creating the archive (to prevent it from stripping leading slashes) or you could pipe the output from find through the cut command to cut of leading slashes. That is, you can either do:
```
tar -czPf $archive $dir
``` to create the archive, or:
```
find $dir -print | cut -c '2-'
```to generate the list of files to compare to the tar -t output.

-- BEGIN EDIT --
If you don't want to indiscriminately cut the first character off each line of find output (eg. if you're not sure beforehand whether $dir will be an absolute path or not), you can also use a simple sed script to strip leading slashes:
```
find $dir -print | sed -e 's/^\///'
```
-- END EDIT --

As for trailing slashes, it seems tar -t always prints trailing slashes for names of directories in the archive, while find prints trailing slashes only for directories named as command line arguments (and only if those command line arguments were given with trailing slashes). Again there are two solutions to this. Firstly, you could use a slightly more complicated find command to ensure that directories are always printed with trailing slashes:
```
find $dir \( -type d -printf '%p/\n' \) -o \( -not -type d -print \)
```
Or you could pipe both the find and tar -t output through a simple sed script that strips off all trailing slashes.
```
tar -tzf $archive | sed -e 's/\/$//'
``` AND
```
find $dir -print | sed -e 's/\/$//'
```

Of course, as I mentioned before, it's probably also a good idea to pipe both the tar -t and find output through sort before doing the comparison.

---

### Post by heindsight on 2009-02-28
Having read through my last post again, I should probably add that I think your safest options are to use the sed script to cut leading slashes from the find output (that way you don't have to worry about whether you have absolute paths or not). The same goes for dealing with trailing slashes - use the sed method to get rid of all trailing slashes, there's less that can go wrong that way. For find you can even combine those two sed scripts into one command like:
```
find $dir -print | sed -e 's/^\///' -e 's/\/$//'
```

---

### Post by BOOBOOJS on 2009-03-02
Thanks, looks promising!
I am getting really upset with Tar though...
tried to run this script to backup / but the tar exclusions are not working.I tried all different variations of:

```
 tar -c -$TAR_OPTS "$Exclude_DIRS" -f - "$Backup_DIR" | split -b "$Split_Size" - \
          "$Backup_File_Location$Arc_Date/Backup$Arc_Date$TAR_EXT" >> ~/"$Arc_Date.log"
```

But no matter what order I put in in the tar exclusions do not work
I have tried everything found on the net but just can't figure it out.

Got anything for that?
I would be most appreciative if someone could help me out with that. Thanks in advance!

---

