---
title: "XBOX Hbmc installer cd"
date: 2010-01-08
forum: Gaming &amp; Leisure
---

### Post by konnorrigby on 2010-01-08
First: Sorry if this is in the wrong section.

So, heres my story...
I wanted to make a sort of NDURE installer cd except not NDURE, i have based it off of the NDURE installer but made an XBMC installer script rather that NDURE so...

my cd loks like this...
```

.../XBMCinstaller
/eeprom
/F
/isolinux
/XBMC
/xbox

```
and more importantly my installer script...
/XBMC/XBMC

```
 

#!/bin/sh
#
# Softmod Installer For XBMC.
#
cd
tmpdir="/XBMC"
echo="echo -e"
clear
/usr/bin/find-cd2 check
CDDEV="`df | grep CD | cut -c 1-8`"
if [ "$CDDEV" = "" ]; then
   $echo "\nLinux CD not found! Insert it and try again...\n"
   exit 1
fi
PMASTER=`fdisk -l | grep Disk | grep hda`
PMASTER=`detectpm | grep Model | cut -d ':' -f 2`
PMLOCK=`detectpm | grep 'Security locked' | cut -d ':' -f 2`
#
clear
if [ "$PMASTER" = "" ]; then
   $echo "No xbox hard drive found on /dev/hda (primary master)"
   $echo "This script assumes /dev/hda be the device to be used"
   $echo "Please shut down you PC - connect your Xbox drive to the"
   $echo "primary master and try again!\n\n"
   exit 1
else
   $echo "Found Harddrive on primary Master"
fi
$echo "We will now search /dev/hda for an xbox partition table...\n"
sleep 2
PART=TRUE
for nn in 50 51 52 53 54; do
   if [ "`ls /dev/hda* | grep $nn`" = "" ]; then
      PART=FALSE
   fi
done
if [ "$PART" = "FALSE" ]; then
   $echo "No xbox-partition table found on /dev/hda"
   if [ "$PMLOCK" = "Yes" ]; then
      $echo "Drive Primary Master is locked !"
   fi
   exit 1
else
   $echo "Xbox-partition table found on /dev/hda"
fi
if [ -f /CD/ndure/checkid ]; then
   $echo "\nFound sofmod package on CDROM...\n"
else
   $echo "\nDid not find softmod installer package on CDROM..."
   $echo "To install softmod with this tool you must DL"
   $echo "and burn the sminstaller folder to the xboxhdm CD"
   exit 1
fi
###### this part is experiment #####
mkdir -p $tmpdir
mkdir -p /xbox
mkdir -p /xbox/hack
mkdir -p /xbox/C
mkdir -p /xbox/E
##/bin/mount -o loop /CD/sminstaller/softmod /xbox/hack/
###########
printheader() {
   clear
   $echo "=================================================="
   $echo "         XBMC INSTALLER FOR XBOXHDM" 
   $echo "=================================================="
              }
printheader
   $echo "              You have the following options :\n\n"
   $echo "           [1] Install XBMC Onto new Hard Drive\n"
   read cmd

##################
   if [ $cmd -eq 1 ]; then
#
#  Installs XBMC C replace
#
   clear
   printheader
   $echo "   Installing Ndure"
   $echo "   This will completely remove contents of C"
   $echo "   And replace them with contents of XBMC/C/"
   $echo "   Please wait"
   $echo "   Part 1 of 3:" 
mount -t fatx /dev/hda51 /xbox/C
mount -t fatx /dev/hda50 /xbox/E
mkdir -p /xbox/E/dash
if [ -f /xbox/E/backup/xboxdash.xbe ]; then
   $echo "               C drive backup found"
else
   $echo "               Could not find C drive backup"
   $echo "               Creating backup"
mkdir -p /xbox/E/backup
cp -R /xbox/C/* /xbox/E/backup/
fi
   sleep 2
   $echo "   Part 2 of 3:"
   $echo "               Copying files"
             if [ -f /CD/ndure/C/xboxdash.xbe ]; then 
rm -rf /xbox/C/*
             else
   $echo "\nDid not find C drive files"
cd /   
umount /dev/hda51
umount /dev/hda50 
             exit 1
             fi
   sleep 2
cp -R /CD/XBMC/C/* /xbox/C/
cp -R /CD/XBMC/E/* /xbox/E/
if [ -f /xbox/C/shadowc/shadowc.img ]; then
   $echo "               Copying C drive backup"
   $echo "               to shadowc"
/bin/mount -t fatx -oloop /xbox/C/shadowc/shadowc.img /xbox/hack/
cp -R /xbox/E/backup/* /xbox/hack/
/bin/umount /xbox/hack/
fi 
##chmod 777 /xbox/C/shadowc/*
   sleep 2
   $echo "   Part 3 of 3:"
cd /   
umount /dev/hda51
umount /dev/hda50 
        $echo "\n        Done.. now exiting"
        $echo "Thanks to konnorrigby for the XBMC script"\n
        $echo "konnorrigby@yahoo.com"
    exit 1
   fi
done

```

Can someone tell me if they find any errors in this, i can't test it yet.  Notice YET   That would be so amazing.  
:P

---

### Post by Project PWNED on 2010-01-08
Wrong section? How about wrong forum entirely. I'd check some XBMC or Xbox IRC channels, which you can find on some of these websites that could help you out. I think theres one on Freenode if I remember right.

---

### Post by konnorrigby on 2010-01-08
Sorry i tried a quite a few different sights and nothing. i don't normally post here at all, but this was just my last try.

---

