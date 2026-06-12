---
title: "Mount ISO BIN/CUE IMG/CUE NRG with Nautilus"
date: 2006-03-25
forum: Desktop Environments
---

### Post by adamkane on 2006-03-25
[B]See:
Thread 2: install cdemu
Thread 3: mount-iso Nautilus-script (iso nrg bin/cue)
Thread 6: cue sheet Nautilus-script

Background:[/B]

It's odd that there still isn't an all-in-one Nautilus-script for mounting and unmounting ISO, BIN/CUE, IMG/CUE and NRG images. I've been studying the KDE MountISO service menu, and can see that it would be easy to translate much of the code, and create a script for Nautilus users.

I'm going to post a separate Nautilus-script for each type of image, and then try to create an all-inclusive mount script. (One script to rule them all.) I also want the script to allow the user to unmount an image by right-clicking the original file or by right-clicking a link on the desktop. 

The cdemu package is required to mount BIN/CUE images, and requires multiple steps to install. I would like to create a simple install script for the cdemu package that will work on 386, 686 and k7 systems.

**Any help would be appreciated.**

References:
[http://www.kde-apps.org/content/show.php?content=11577]("http://www.kde-apps.org/content/show.php?content=11577")
[http://rattyman.blogspot.com/2005/11/mount-umount-naultilus-scripts.html]("http://rattyman.blogspot.com/2005/11/mount-umount-naultilus-scripts.html")
[http://www.ubuntuforums.org/showthread.php?t=144236]("http://www.ubuntuforums.org/showthread.php?t=144236")

I've already translated the original mountiso-sh script from KDE to Gnome. This script is unusable in my opinion, because it tries to do much, and is slow and unresponsive.

These are the commands I converted from KDE to Gnome:

KDE command -> GNOME equivalent
kdialog --title "TITLE" --msgbox "MESSAGE" -> zenity --info --text "TEXT"
kdialog --inputbox "INPUT" -> zenity --entry "ENTRY"
kfmclient openURL -> gnome-open
kdesu -> foo=`gksudo -u root -k -m "enter your password for root terminal access" /bin/echo "got r00t?"` sudo

This section of the original script was completely whigged out:

```

if ( test -d "$MOUNTDIR" )
then
/usr/bin/cdemu $NODE "$1" &&
mount /dev/cdemu/$DEV "$MOUNTDIR" ||
/usr/bin/cdemu -u $NODE
fi

``` 

and has been replaced by this:

```

if ( test -d "$MOUNTDIR" )
then
foo=`gksudo -u root -k -m "enter your password for root terminal access" /bin/echo "got r00t?"`
/usr/bin/cdemu $NODE "$1"
sudo mount -t iso9660 /dev/cdemu/${NODE} "$MOUNTDIR"
fi

``` 

One way to use the original MountISo script is to use helper scripts like this one:

```

#!/bin/bash
# MountISOImage

~/.gnome2/nautilus-scripts/MountISO/mountiso.sh "$1" mount

``` 
in conjunction with the main mountiso-sh script:

```

#!/bin/sh
# Mount-ISO v0.9.1
BSNAME="`basename "$1"`"

if ( `echo "$BSNAME" | grep "Mount-ISO" > /dev/null` ) then
  MOUNTDIR="$1"
else
  MOUNTDIR="$HOME/Desktop/Mount-ISO ($BSNAME)"
fi

function dialog {
  zenity --info --text "$1"
}

function err {
  case "$1" in
   1)
     ERROR_MESSAGE="\"$2\" is not readable, check file permissions!"
     ;;
   2)
     ERROR_MESSAGE="\"$2\" is already mounted!"
     ;;
   3)
     ERROR_MESSAGE="\"$2\" could not be created!"
     ;;
   4)
     ERROR_MESSAGE="\"$2\" is not mounted!"
     ;;
   5)
     ERROR_MESSAGE="Folder \"$2\" exists but \"$3\" is not mounted!"
     ;;
   6)
     ERROR_MESSAGE="Could not mount \"$2\"! Check your system settings."
     ;;
   7)
     ERROR_MESSAGE="\"$2\" has data error! File might be of wrong type or corrupted."
     ;;
   8)
     ERROR_MESSAGE="\"$2\" is not a directory!"
     ;;
   9)
     ERROR_MESSAGE="Error creating ISO image from directory \"$2\"!"
     ;;
   10)
     ERROR_MESSAGE="\"$2\" is a directory - MD5 sum can not be calculated!"
     ;;
   11)
     ERROR_MESSAGE="\"$2\" file does not exist!"
     ;;
   12)
     ERROR_MESSAGE="ISO creation failed! Check if you have CD in your CDROM and if you have required permissions."
     ;;
   13)
     ERROR_MESSAGE="Unmounting \"$2\" failed! Check if some programs are using it, close them and try again."
     ;;
   *)
     return 0
     ;;
  esac
  dialog "ERROR: $ERROR_MESSAGE"
  exit 0
}

function msg {
  case "$1" in
    1)
      INFO_MESSAGE="ISO image \"$2\" successfully created in \"$3\"!"
      ;;
    2)
      INFO_MESSAGE="MD5 checksum of \"$2\" is: \"$3\""
      ;;
    3)
      INFO_MESSAGE="Tracks were saved as \"$2XX.iso\" in \"$3\""
      ;;
    4)
      INFO_MESSAGE="UDF image \"$2\" successfully created in \"$3\"!"
      ;;
    5)
      INFO_MESSAGE="CloneCD image was converted into \"$2\" and saved in \"$3\""
      ;;
    6)
      INFO_MESSAGE="Image file \"$2\" is of type \"$3\""
      ;;
    *)
      return 0
      ;;
  esac
  dialog "$INFO_MESSAGE"
  exit 0
}

function check_mount {
  DEV="`mount | grep "$1" | cut -f 1 -d " "`"
  if ( test ! -z "$DEV" ) then
    return 0
  else
    return 1
  fi
}

function check_cdemu {
  if ( `/usr/bin/cdemu -s | grep "$1" > /dev/null` ) then
    return 0
  else
    return 1
  fi
}

function check_iso {
  TYPE=`head "$1" | od -Ax -s | head -n 1 | cut -f 1 -d " " `
    case "$TYPE" in
      008008)
        # ISO image
        CHECK="Standard ISO9660 image"
        ;;
      008028)
        # ISO image (by WinISO)
        CHECK="Standard ISO9660 image (by WinISO)"
        ;;
      053008)
        # NRG image
        CHECK="NRG image (by Nero)"
        ;;
      007a69)
        # XDVDFS image
        CHECK="XBOX DVD image"
        ;;  
      *)
        # Anything else
        CHECK="Unknown format"
        ;;
    esac
}

case "$2" in
  mount)
    if (test -d "$MOUNTDIR") then
      check_mount "$MOUNTDIR" &&
      err 2 "$1"
    else
      test -r "$1" ||
      err 1 "$1"
      mkdir -p "$MOUNTDIR"
    fi
    if ( test -d "$MOUNTDIR" )
    then
      TYPE=`head "$1" | od -Ax -s | head -n 1 | cut -f 1 -d " " `
      case "$TYPE" in
        008008)
          # ISO image
          MODE=",defaults"
          ;;
        008028)
          # ISO image (by WinISO)
          MODE=",defaults"
          ;;
        053008)
          # NRG image
          MODE=",offset=307200"
          ;;
        007a69)
          # XDVDFS image
          rmdir "$MOUNTDIR"
          err 7 "$1"
          ;;  
        *)
          # Anything else
          rmdir "$MOUNTDIR"
          err 7 "$1"
          ;;
      esac
      foo=`gksudo -u root -k -m "enter your password for root terminal access" /bin/echo "got r00t?"`
      sudo mount -t udf,iso9660 -o loop,ro,nodev,noexec,nosuid${MODE} "$1" "$MOUNTDIR"
    fi
    if ( check_mount "$MOUNTDIR" ) then
      gnome-open "$MOUNTDIR"
    else
      rmdir "$MOUNTDIR"
      err 6 "$MOUNTDIR"
    fi
    ;;
  unmount)
    if (test ! -d "$MOUNTDIR") then
      err 4 "$1"
    elif (check_mount "$MOUNTDIR") then
      foo=`gksudo -u root -k -m "enter your password for root terminal access" /bin/echo "got r00t?"`
      sudo umount "$MOUNTDIR" &&
      rmdir "$MOUNTDIR" ||
      err 13 "$1"
      if ( test "${DEV##/dev/cdemu/}" -ge 0 2>/dev/null ) then
        /usr/bin/cdemu -u ${DEV##/dev/cdemu/}
      fi
    else
      err 5 "$MOUNTDIR" "$1"
    fi
    ;;
  createiso)
    ISOFILE="`basename "$1"`.iso"
    SAVEDIR="`dirname "$1"`"
    
    if ( test ! -w "$SAVEDIR" ) then
      SAVEDIR="$HOME/Desktop"
    fi
    
    if ( test ! -d "$1" ) then
      err 8 "$1"
    fi
   
    mkisofs -joliet -rock -quiet -no-bak -o "$SAVEDIR/$ISOFILE" "$1" &&
    msg 1 "$ISOFILE" "$SAVEDIR" ||
    err 9 "$1"
    ;;
  createudf)
    ISOFILE="`basename "$1"`.iso"
    SAVEDIR="`dirname "$1"`"
    
    if ( test ! -w "$SAVEDIR" ) then
      SAVEDIR="$HOME/Desktop"
    fi
    
    if ( test ! -d "$1" ) then
      err 8 "$1"
    fi
   
    mkisofs -dvd -quiet -no-bak -o "$SAVEDIR/$ISOFILE" "$1" &&
    msg 4 "$ISOFILE" "$SAVEDIR" ||
    err 9 "$1"
    ;;
  calc)
    if ( test -d "$1" ) then
      err 10 "$1"
    elif ( test -f "$1" ) then
      SUM=`md5sum "$1" | cut -f 1 -d " "`
      msg 2 "$BSNAME" "$SUM"
    fi
    ;;
  bin2iso)
    SAVEDIR="`dirname "$1"`"
    BASE="${BSNAME%.*}"
    BINFILE="$SAVEDIR/"`head -n 1 "$1" | cut -f 2 -d " " | sed -e "s/^\"//" -e "s/\"$//"`
    
    if ( test ! -w "$SAVEDIR" ) then
      SAVEDIR="$HOME/Desktop"
    fi
    
    if ( test ! -f "$BINFILE" ) then
      err 11 "`basename "$BINFILE"`"
    else
      /usr/bin/bchunk "$BINFILE" "$1" "$BASE" > /dev/null
      ls -1b "${BASE}"*.iso | while read file; do mv "$file" $SAVEDIR; done
      msg 3 "$BASE" "$SAVEDIR"
    fi
    ;;
  ccd2iso)
    SAVEDIR="`dirname "$1"`"
    BASE="${BSNAME%.*}"
    IMGFILE="$SAVEDIR/$BASE.img"
    
    if ( test ! -w "$SAVEDIR" ) then
      SAVEDIR="$HOME/Desktop"
    fi
    
    if ( test ! -f "$IMGFILE" ) then
      err 11 "$BASE.img"
    else
      /usr/local/bin/ccd2iso "$IMGFILE" "$SAVEDIR/$BASE.iso" > /dev/null
      msg 5 "$BASE.iso" "$SAVEDIR"
    fi
    ;;
  grabiso)
    if ( test ! -w "$1" ) then
      IMGFILE="`zenity --inputbox "This directory is read-only, saving to Desktop! Choose name for ISO-image:" "$HOME/Desktop/mount.iso"`" || exit 0
    else
      IMGFILE="`zenity --inputbox "Choose name for ISO-image:" "$1/mount.iso"`" || exit 0
    fi
    SAVEDIR="`dirname "$IMGFILE"`"
                 
    while ( ( test ! -w "$SAVEDIR" ) || ( test -f "$IMGFILE" ) )
    do
      if ( test -f "$IMGFILE" ) then
        IMGFILE="`zenity --inputbox "File with this name already exists! Choose another name:" "$IMGFILE"`" ||
        exit 0
      elif ( test ! -w "$SAVEDIR" ) then
        IMGFILE="`zenity --inputbox "Permission to write here is denied! Choose another name:" "$IMGFILE"`" ||
        exit 0
      fi
      SAVEDIR="`dirname "$IMGFILE"`"
        
    done
    
    if ( test "$SAVEDIR" != "$IMGFILE" ) then
      dd if="/dev/cdrom" of="$IMGFILE" &&
      msg 1 "`basename "$IMGFILE"`" "$SAVEDIR" ||
      err 
    fi
    ;;
  nrg2iso)
    SAVEDIR="`dirname "$1"`"
    BASE="${BSNAME%.*}"
    IMGFILE="$SAVEDIR/$BASE.iso"
    
    if ( test ! -w "$SAVEDIR" ) then
      SAVEDIR="$HOME/Desktop"
    fi
    
    TYPE=`head "$1" | od -Ax -s | head -n 1 | cut -f 1 -d " " `
    case "$TYPE" in
      053008)
        dd if="$1" of="$IMGFILE" bs=512 skip=600 > /dev/null &&
        msg 5 "$BASE.iso" "$SAVEDIR" || 
        err 3 "$IMGFILE"
        ;;
      *)
        err 7 "$1"
        ;;
    esac
    ;;
  mountcb)
    BASE="${BSNAME%.*}"
    BINFILE="$SAVEDIR/"`head -n 1 "$1" | cut -f 2 -d " " | sed -e "s/^\"//" -e "s/\"$//"`
    NODE=$((`/usr/bin/cdemu -s | cut -f 8 -d " " | grep 0 -n -m 1 | cut -c 1`-2))
        
    if (test -d "$MOUNTDIR") then
      check_mount "$MOUNTDIR" &&
      err 2 "$1"
    else
      mkdir -p "$MOUNTDIR"
    fi
    if ( test -d "$MOUNTDIR" )
    then
      foo=`gksudo -u root -k -m "enter your password for root terminal access" /bin/echo "got r00t?"`
      /usr/bin/cdemu $NODE "$1"
      sudo mount -t iso9660 /dev/cdemu/${NODE} "$MOUNTDIR"
    fi
    if ( check_mount "$MOUNTDIR" ) then
      gnome-open "$MOUNTDIR"
    else
      rmdir "$MOUNTDIR"
      err 6 "$MOUNTDIR"
    fi
    ;;
  xbx2iso)
    SAVEDIR="`dirname "$1"`"
    BASE="${BSNAME%.*}"
    IMGFILE="$SAVEDIR/$BASE.img"
    
    if ( test ! -w "$SAVEDIR" ) then
      SAVEDIR="$HOME/Desktop"
    fi
    
    if ( test ! -f "$IMGFILE" ) then
      err 11 "$BASE.img"
    else
      /usr/local/bin/ccd2iso "$IMGFILE" "$SAVEDIR/$BASE.iso" > /dev/null
      msg 5 "$BASE.iso" "$SAVEDIR"
    fi
    ;;
  createxbx)
    ISOFILE="`basename "$1"`.iso"
    SAVEDIR="`dirname "$1"`"
    
    if ( test ! -w "$SAVEDIR" ) then
      SAVEDIR="$HOME/Desktop"
    fi
    
    if ( test ! -d "$1" ) then
      err 8 "$1"
    fi
   
    /usr/bin/extract-xiso -c "$1" "$SAVEDIR/$ISOFILE"  &&
    msg 4 "$ISOFILE" "$SAVEDIR" ||
    err 9 "$1"
    ;;
  checkiso)
    check_iso "$1"
    msg 6 "$BSNAME" "$CHECK"
    ;;
esac

``` 

But, like I said, this script is too unwieldy, and I would like to create something that is both simple and useful.

---

### Post by adamkane on 2006-03-25
**The following is an install script for cdemu bchunk nrg2iso ccd2iso:**

** Add the universe repository**, if you haven't already:
 [http://easylinux.info/wiki/Ubuntu#Ho...a_repositories]("http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories")
 
Open a text editor and paste the following code:

cdemu-etc
 ```

#!/bin/bash
#
# cdemu nrg2iso ccd2iso bchunk installer
# linux linux-image linux-headers linux-restricted-modules installer

echo
echo --------------------------------------
echo cdemu nrg2iso ccd2iso bchunk installer
echo system optimizer
echo --------------------------------------
echo
echo Select one of these download mirrors
echo or type quit.
echo
echo You must type the name exactly.
echo
echo belnet easynews heanet internap
echo jaist keihanna kent mesh ovh
echo superb surfnet switch ufpr umn
echo

read MIRROR

if [ $MIRROR == q -o $MIRROR == quit ]; then
echo
echo Good-bye.
echo
exit
fi

if [ $MIRROR == belnet -o $MIRROR == easynews -o $MIRROR == heanet -o $MIRROR == internap -o $MIRROR == jaist -o $MIRROR == keihanna -o $MIRROR == kent -o $MIRROR == mesh -o $MIRROR == ovh -o $MIRROR == superb -o $MIRROR == surfnet -o $MIRROR == switch -o $MIRROR == ufpr -o $MIRROR == umn ]; then
echo
else
echo
echo You failed to select a mirror.
echo
echo Good-bye.
echo
exit
fi

PROCESSOR=$(uname -m) # Outputs i386 i686 or k7
PROC_TEMP=$(uname -m | cut -d "i" -f2) # Outputs 386 686 or k7
KERNEL=$(uname -r | cut -d "-" -f3) # Outputs 386 686 or k7

if [ $PROC_TEMP != $KERNEL ]; then
echo
echo ------------------------------------------
echo You have $KERNEL kernel files installed.
echo Ubuntu says your computer is ${PROCESSOR}.
echo
echo Is your system $KERNEL?
echo
echo 1 - Yes
echo 2 - No
echo

read SYS_OK_OR_NOT

if [ $SYS_OK_OR_NOT == "2" -o $SYS_OK_OR_NOT == "n" ]; then

echo
echo -------------------------------------------
echo You are about to install new kernel files.
echo There is a chance that you will not be able
echo to log in to your system again.
echo Please be sure that you have a sound
echo back-up policy before proceeding.
echo
echo Which system do you have?
echo
echo 1 - Legacy Pentium
echo 2 - Pentium
echo 3 - AMD
echo 4 - Quit
echo

read SYS_TO_INSTALL

if [ $SYS_TO_INSTALL == 4 -o $SYS_TO_INSTALL == q ]; then
echo
echo Good-bye.
echo
fi

if [ $SYS_TO_INSTALL == 1 ]; then

echo
apt-get install linux-386 linux-image-386 linux-headers-386 linux-restricted-modules-386
KERNEL=386
fi

if [ $SYS_TO_INSTALL == 2 ]; then

echo
apt-get install linux-686 linux-image-686 linux-headers-686 linux-restricted-modules-686
KERNEL=686
fi

if [ $SYS_TO_INSTALL == 3 ]; then

echo
apt-get install linux-k7 linux-image-k7 linux-headers-k7 linux-restricted-modules-k7
KERNEL=k7
fi

echo
echo Reboot, then re-run this script.
echo
exit
fi
fi

echo
echo ------------------------------------
echo Install build-tools bchunk nrg2iso?
echo
echo build-tools are necessary to install
echo cdemu and ccd2iso.
echo
echo bchunk converts BIN/CUE files to ISO.
echo nrg2iso converts NRG files to ISO.
echo
echo 1 - Yes
echo 2 - No
echo 3 - Quit
echo

read CONTINUE_BUILD

if [ $CONTINUE_BUILD == 3 -o $CONTINUE_BUILD == q ]; then
echo
echo Good-bye
echo
exit
fi

if [ $CONTINUE_BUILD == 1 -o $CONTINUE_BUILD == y ]; then
apt-get install build-essential checkinstall automake1.6 libtool gcc-3.4 bchunk nrg2iso
echo Done
fi

echo
echo ---------------------------
echo Install cdemu?
echo
echo cdemu mounts BIN/CUE files.
echo
echo 1 - Yes
echo 2 - No
echo 3 - Quit
echo

read CONTINUE_CDEMU

if [ $CONTINUE_CDEMU == 3 -o $CONTINUE_CDEMU == q ]; then
echo
echo Good-bye
echo
exit
fi

if [ $CONTINUE_CDEMU == 1 -o $CONTINUE_CDEMU == y ]; then
cd ~/Desktop
wget http://robert.private.outertech.com/virtualcd/cdemu-0.7.tar.bz2
tar xjf ~/Desktop/cdemu-0.7.tar.bz2
cd ~/Desktop/cdemu-0.7
ls -la /lib/modules/`uname -r`/build
make
make install

echo
echo Done
echo

echo
echo ------------------------------------
echo Add the word "cdemu" 
echo to the end of the /etc/modules file,
echo then close the file.
echo
echo Example:
echo
echo -----------------------------------------------------------------------
echo "# /etc/modules: kernel modules to load at boot time."
echo "#"
echo "# This file contains the names of kernel modules that should be loaded"
echo "# at boot time, one per line. Lines beginning with "#" are ignored."
echo
echo lp
echo mousedev
echo psmouse
echo cdemu
echo ------------------------------------------------------------------------
echo

gedit /etc/modules
fi

echo
echo --------------------------------------
echo Install ccd2iso?
echo
echo ccd2iso converts CCD/IMG files to ISO.
echo
echo 1 - Yes
echo 2 - No
echo 3 - Quit
echo

read CONTINUE_CCD2ISO

if [ $CONTINUE_CCD2ISO == 3 -o $CONTINUE_CCD2ISO == q ]; then
echo
echo Good-bye
echo
exit
fi

if [ $CONTINUE_CCD2ISO == 1 -o $CONTINUE_CCD2ISO == y ]; then
cd ~/Desktop
wget http://${MIRROR}.dl.sourceforge.net/sourceforge/ccd2iso/ccd2iso-0.2.tar.gz

echo
echo Did the download succeed?
echo
echo 1 - Yes
echo 2 - No
echo

read DOWNLOAD_SUCCEEDED

if [ $DOWNLOAD_SUCCEEDED == 2 -o $DOWNLOAD_SUCCEEDED == n ]; then
echo
echo Good-bye
echo
exit
fi

tar xzf ~/Desktop/ccd2iso-0.2.tar.gz
cd ~/Desktop/ccd2iso
./configure --prefix=/usr # CC=gcc-3.4 CPP=g++-3.4
make
checkinstall -y --pkgname=ccd2iso-0.2 --pkgversion=0.2
fi
echo
echo Clean up temporary installation files?
echo
echo 1 - Yes
echo 2 - No
echo

read CLEAN_UP_OR_NOT

if [ $CLEAN_UP_OR_NOT == 1 ]; then
rm -R ~/Desktop/cdemu-0.7
rm -R ~/Desktop/cdemu-0.7.tar.bz2*
rm -R ~/Desktop/ccd2iso
rm -R ~/Desktop/ccd2iso-0.2.tar.gz*
fi

```Save the file to your desktop as cdemu-etc and execute the script:

```

cd ~/Desktop
sudo chmod +x cdemu-etc
sudo sh cdemu-etc

```After cdemu is installed, you will need to reboot or load cdemu this way:

```

sudo modprobe cdemu

```I don't yet know the best way to remove cdemu. 

You can remove ccd2iso nrg2iso bchunk with Synaptic or this way:
```

sudo apt-get remove ccd2iso nrg2iso bchunk

```Note: You can also download ccd2iso from here:
 [http://rarewares.org/debian/packages...2-0.1_i386.deb]("http://rarewares.org/debian/packages/unstable/ccd2iso_0.2-0.1_i386.deb")[URL="http://g-scripts.sourceforge.net/"]
[/URL]

---

### Post by adamkane on 2006-03-25
[B]Nautilus-script mini-HOWTO:
[/B]
Save Nautilus-scripts as text files here:

~/.gnome2/nautilus-scripts/

Then mark the scripts to be executable:

```

sudo chmod 700 ~/.gnome2/nautilus-scripts/*.*

``` Reference:
[http://g-scripts.sourceforge.net/]("http://g-scripts.sourceforge.net/")

**Mount/Unmount ISO Nautilus-scripts:**

You can mount multiple ISO and NRG files, and you can mount up to 8 BIN/CUE files. 

A shortcut will be placed on the desktop for each mounted image. Right-click the desktop shortcut or right-click the image file to unmount.

If you want to mount BIN/CUE files, you first need to install cdemu or complete the steps in **Thread 2**.

mountiso
```

#!/bin/bash
# Mount ISO NRG BIN/CUE

# Get filename extension and make it lower-case
EXT=`echo $1 | sed -e 's/.*\.//'`
EXT_LOW=`echo $EXT | tr 'A-Z' 'a-z'`

# Get the filename without the extension
BASE="`echo "$1" | sed 's/\.[^.]*$//'`" 

# Mount ISO
if [ $EXT_LOW == "iso" ]; then
foo=`gksudo -u root -k -m "enter your password for root terminal access" /bin/echo "got r00t?"`
sudo mkdir /media/"$BASE" &&
sudo mount -o loop,ro,nodev,noexec,nosuid "$1" /media/"$BASE" &&
## Uncomment the next line, if you prefer to have an extra link to the ISO image placed on the desktop.
#ln -s "/media/${BASE}" "/home/$USER/Desktop/${BASE}" &&
gnome-open "/media/${BASE}" 
fi

# Mount NRG
if [ $EXT_LOW == "nrg" ]; then
foo=`gksudo -u root -k -m "enter your password for root terminal access" /bin/echo "got r00t?"`
sudo mkdir /media/"$BASE" &&
sudo mount -o loop,ro,nodev,noexec,nosuid,307200 "$1" /media/"$BASE" &&
## Uncomment the next line, if you prefer to have an extra link to the NRG image placed on the desktop.
#ln -s "/media/${BASE}" "/home/$USER/Desktop/${BASE}" &&
gnome-open "/media/${BASE}" 
fi

# Mount BIN/CUE
if [ $EXT_LOW == "cue" ]; then

# Find a free node to mount
NODE=$((`cdemu -s | cut -f 8 -d " " | grep 0 -n -m 1 | cut -c 1`-2))

  if [ $NODE -lt "0" ]; then
  zenity --info --text "You can not mount any more BIN/CUE files."
  fi

  # Node needs to be between 0 and 7
  if [ $NODE -ge "0" -a $NODE -le 7 ]; then
  foo=`gksudo -u root -k -m "enter your password for root terminal access" /bin/echo "got r00t?"` 
  sudo mkdir -p "/media/${BASE}" &&
  cdemu $NODE "$1" &&
  sudo mount -t iso9660 /dev/cdemu/${NODE} "/media/${BASE}" &&
  ln -s "/media/${BASE}" "/home/$USER/Desktop/${BASE}" &&
  gnome-open "/media/${BASE}" 
  fi

# If directory is empty, then release cdemu
if [ "$(ls -A /media/${BASE})" ]; then
echo
else
cdemu -u $NODE
fi

fi

# If directory is empty, then remove empty directory
if [ "$(ls -A /media/${BASE})" ]; then
echo
else
sudo rmdir /media/"${BASE}"
fi

``` 

unmountiso
```

#!/bin/bash
# Unmount

BASE="$1"

# Get filename extension and make it lower-case
# EXT_LOW will be iso, nrg, cue or nonsense
EXT=`echo $1 | sed -e 's/.*\.//'`
EXT_LOW=`echo $EXT | tr 'A-Z' 'a-z'`

# Isolate the the basename without the extension (in case this is not the case already)
if [ $EXT_LOW == "iso" -o $EXT_LOW == "nrg" -o $EXT_LOW == "cue" -o $EXT_LOW == "volume" ]; then
BASE="`echo "$1" | sed 's/\.[^.]*$//'`"
fi

# Release /dev/cdemu according to whether BIN uses /dev/cdemu0 or /dev/cdemu/0
foo=`gksudo -u root -k -m "enter your password for root terminal access" /bin/echo "got r00t?"`
DEV="`mount | grep "$BASE" | cut -f1 -d " "`"

if [ ${DEV##/dev/cdemu/} -ge 0 -a ${DEV##/dev/cdemu/} -le 7 ]; then
cdemu -u ${DEV##/dev/cdemu/}
else
cdemu -u ${DEV##/dev/cdemu}
fi

# Unmount
foo=`gksudo -u root -k -m "enter your password for root terminal access" /bin/echo "got r00t?"`
sudo umount /media/"${BASE}"
sudo rmdir /media/"${BASE}"
sudo rm /home/$USER/Desktop/"${BASE}"

```

---

### Post by adamkane on 2006-03-25
**Mount/Unmount BIN/CUE IMG/CUE Nautilus-scripts:**

mountcue
```

See above.

``` 
unmount
```

See above.

``` [code]

---

### Post by adamkane on 2006-03-26
**Mount/Unmount NRG Nautilus-scripts:**

mountnrg
```

See above.

``` 

unmount
 ```

 See above.
 
```

---

### Post by adamkane on 2006-03-28
**Create CUE Nautilus-Script:**

If you have some BIN files with missing or corrupt CUE files, then use this script to create a new CUE file by right-clicking the BIN file.

create-cue
```

#!/bin/bash
# Create CUE for BIN

# Isolate the filename without the extension.
BASE=`echo "$1" | sed 's/\.[^.]*$//'` 

cat << EOF > "${BASE}.cue"
FILE "$1" BINARY
  TRACK 01 MODE1/2352
    INDEX 01 00:00:00
EOF

```

---

### Post by adamkane on 2006-03-28
I've put together Nautilus-Scripts to mount/unmount ISO NRG and BIN/CUE files, and a script to create CUE files.

I'll start working on some convert2iso and createiso Nautilus-Scripts, and then an install script for cdemu.

---

### Post by adamkane on 2006-04-01
I've created a cdemu install script. Let me know if it works.

---

### Post by Rikostan on 2006-04-01
I got to this part...Install ccd2iso? When it failed. Here is that part of the code. It did download okay, but it couldn't find it.

1 - Yes
2 - No
3 - Quit

1
--13:45:27--  [http://easynews.dl.sourceforge.net/sourceforge/ccd2iso/ccd2iso-0.2.tar.gz](http://easynews.dl.sourceforge.net/sourceforge/ccd2iso/ccd2iso-0.2.tar.gz)
           => `ccd2iso-0.2.tar.gz'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 179,670 (175K) [application/x-tar]

100%[====================================>] 179,670      100.74K/s

13:45:30 (100.47 KB/s) - `ccd2iso-0.2.tar.gz' saved [179670/179670]


Did the download succeed?

1 - Yes
2 - No

1
tar: ccd2iso-0.2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
cdemu-etc: line 224: cd: ccd2iso: No such file or directory
cdemu-etc: line 225: ./configure: No such file or directory
make: *** No rule to make target `clean'.  Stop.

checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

*** No known documentation files were found. The new package
*** won't include a documentation directory.

Installing with "make install"...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.






The how-to is not ready for newbs like me. You need to document the choices a little better and clean it up a bit, but it has a ton of promise and I would love to see this work.
Thanks for what you have so far.

---

### Post by adamkane on 2006-04-01
Temporary files are saved to the desktop now, and the installation files are deleted at the end.

Fixed the make clean error.

cdemu normally requires a dozen steps to install, so the install script is an improvement over what is currently available. I hope someone with better skills than I will create an even better install script.

Thanks for the help.

---

### Post by Rikostan on 2006-04-01
Now the install goes fine. I had no problems creating the scripts from post number 3 and I tested it out on an ISO and it worked great. I don't have a cue/bin image to test on right now, but I will get create one and see if I have any issues there....

Thanks for the work you put into this!

---

### Post by T313C0mun1s7 on 2006-06-08
You have put a lot of work into this. Thank you very much. I have not yet tried this, but I am sure that I will have need of it in the future as I have a lot of images of differnt types on my public drive. Kudos to you adamkane.

When you get eveything nailed down, and it can all be done in from a download I can see this being almost as important a project as Easy Ubuntu or Automatix.

Good work.

---

### Post by adamkane on 2006-06-09
All you need to do is execute the cdemu install script, and then save the mount-iso scripts to your Nautilus scripts directory, and then you are ready to go.

I made everything seem more complicated than it actually is. It's because I put a lot of work into translating the original KDE script, and it took me a long time to figure out, and to also make it work for different setups.

1. install cdemu
2. save mount-iso scripts to ~/gnome2/nautilus-scripts
3. mount an iso
4. unmount an iso

That's it.

Install kiso for conversions:
[http://www.ubuntuforums.org/showthread.php?t=150593]("http://www.ubuntuforums.org/showthread.php?t=150593")

---

### Post by keithjr on 2006-06-24
The one program I was looking forward to getting a hold of, ccd2iso, doesn't install correctly.  

I get the following error.


```
cd . && /bin/sh /home/keithjr/Desktop/ccd2iso/missing --run aclocal-1.6
aclocal: configure.in: 8: macro `AM_PROG_LIBTOOL' not found in library
WARNING: `aclocal-1.6' is needed, and you do not seem to have it handy on your
         system.  You might have modified some files without having the
         proper tools for further handling them.  Check the `README' file,
         it often tells you about the needed prerequirements for installing
         this package.  You may also peek at any GNU archive site, in case
         some other package would contain this missing `aclocal-1.6' program.
make: *** [aclocal.m4] Error 1
```


I looked this up, apparently it wants Automake 1.6, which, when I tried to install it, ran into its own dependency problems and failed ](*,) 

Really nice script... too bad ccd2iso source code is old and outdated.

---

### Post by s3ppel on 2006-06-28
I get the same error as keithjr.

Installing automake 1.9 went fine, but doesn't help.

---

### Post by keithjr on 2006-06-28
[QUOTE=s3ppel]I get the same error as keithjr.

Installing automake 1.9 went fine, but doesn't help.[/QUOTE]


Good news, apparently there is a workaround I have been enlightened about recently. 

[http://ubuntuforums.org/showthread.php?t=204687](http://ubuntuforums.org/showthread.php?t=204687)

refer to the post by christhemonkey

basically, you can compile the executable directly with gcc, without going through make and running into the automake dependency.  Silly planning on the part of the ccd2iso people, but they made a neat program so I can't complain much.

Haven't gotten a chance to try it out yet but I'll reply once I do.

---

### Post by ildfroe on 2006-06-29
Great scripts. But why do the only work with files in the home folder?
Can it be modified to also mount files from the desktop??

---

### Post by Clanman on 2006-07-06
Hi
Thanks for your great work. 

Mounting ISO works great for me
The problem I have are with BIN/CUE
It seams as something is wrong. 
When looking in the /media directory I see that the dir is created but it then gets removed. 
I guess this must have something to do with the cdemu part of your script. 
I have checked and the module cdemu is loaded. 

Please advice as I very much would like this to work as well. 

Thanks

---

### Post by nik on 2006-07-08
I'm having problems too with cue/bin files. Haven't tried iso yet. When trying to mount the cue file I get this error:
You can not mount any more BIN/CUE files.

Any idea? Great work btw :)

---

### Post by Clanman on 2006-07-11
Bump. 
If someone could be nice and help out I would be greatfull. 
Please if you need some outputs of files Ill post them 
As the script works well with ISO files Im pretty sure it has something to do with the CDEMU part. 
My system is an dualcore AMD64. And Im using the AMD64 version of ubuntu. 
I have followed the instructions as well as I could. 
I had some problem during instalation with missing librarys but I think I got them all finaly. 

PLEASE help

---

### Post by dnaxx on 2006-07-17
I have the same problem - ISO works great, bin/cue fails.

---

### Post by HAARP on 2006-07-17
Make a script.
Make it executable and start it with root rights.
Start it everytime the system boots.

```
rm /dev/cdemu*
mkdir /dev/cdemu
for drivenumber in `seq -w 0 7` ; do
        mknod /dev/cdemu/${drivenumber} b 62 ${drivenumber}
done

```

Took me quite some time to figure it out. But this works well :)

The problem is that the CDemu device-files are /dev/cdemu0-7
They should be /dev/cdemu/0-7
This script brute-forcely deletes the old device files and creates the right ones.

---

### Post by adamkane on 2006-07-24
This script was written for breezy. I haven't updated it for dapper yet.

Thanks for all the info. I'll work on an update.

---

### Post by Poul on 2006-07-27
Thanks for the tip Haarp. At the moment  I am running your script from the shell every time I boot my PC. Do you know how to make the system execute it automatically.
Adamkane - thank you for the script. Let us know when dapper version is available. Keep up the good work.
Take care.

---

### Post by HAARP on 2006-07-28
I'm using this stuff with Dapper, no problem.
I did execute-at-boot this way:

1. Edit /usr/bin/create_cdemu_devs.sh to make it look like this:
```
#!/bin/bash

rm /dev/cdemu*
mkdir /dev/cdemu
for drivenumber in `seq -w 0 7` ; do
	mknod /dev/cdemu/${drivenumber} b 62 ${drivenumber}
done
```
2. Create /etc/init.d/local
```
#!/bin/sh
echo " * Setting up CDemu devices..."
create_cdemu_devs.sh
```
3. Make it executable
4. Make it start at boot:
```
sudo ln -s /etc/init.d/local /etc/rc2.d/S20local
sudo ln -s /etc/init.d/local /etc/rc3.d/S20local
sudo ln -s /etc/init.d/local /etc/rc4.d/S20local
sudo ln -s /etc/init.d/local /etc/rc5.d/S20local
```

That's it.

The problem is not the script but rather CDemu. It creates the wrong device-files at boot. The readme tells me to create a udev rule on Debian, but this rule doesn't work. I know this is a dirty solution, but it works flawlessly.

---

### Post by ricesteam on 2006-08-05
I'm having this problem as well. Please help.


> **Clanman said:**
> Hi
Thanks for your great work. 

Mounting ISO works great for me
The problem I have are with BIN/CUE
It seams as something is wrong. 
When looking in the /media directory I see that the dir is created but it then gets removed. 
I guess this must have something to do with the cdemu part of your script. 
I have checked and the module cdemu is loaded. 

Please advice as I very much would like this to work as well. 

Thanks

---

### Post by naszi on 2006-08-19
Hi,

i had followinf problems:
First i installed cdemu, then followed the instructions. I made only one script mountiso, and with this i tried to mount bin and cue files.I was only able to mount from cue file, not directly the bin, but I guess thats the way it should work, its fine. I got an iso9660 mounted.

But when i tried to access the files, it froze my computer, competely, nothing worked anymore, only mouse.

So then i wanted to start from scratch again: figured out, that i should have choosen i686 instead of i386. (I have pentium m processor). Ok, i installed the other kernel headers, run the cdemu-etc again, installed it.
(I got an error message at the end wich i dont remember anymore. This message i also got in my first try, still i was able to mount, and i think it was not connected to the bin/cue-mounting.)

I also made a mountcue script, but still i am not sure, is it necessary to have 2-3 different scripts?

Outcome: when i run the scripts now, nothing happens.

Thats it, i hope You could give me some hints whats going on?

Thanks

---

### Post by naszi on 2006-08-19
Hi,

i had following problems:
First i installed cdemu, then followed the instructions. I made only one script mountiso, and with this i tried to mount bin and cue files.I was only able to mount from cue file, not directly the bin, but I guess thats the way it should work, its fine. I got an iso9660 mounted.

But when i tried to access the files, it froze my computer, competely, nothing worked anymore, only mouse.

So then i wanted to start from scratch again: figured out, that i should have choosen i686 instead of i386. (I have pentium m processor). Ok, i installed the other kernel headers, run the cdemu-etc again, installed it.
(I got an error message at the end wich i dont remember anymore. This message i also got in my first try, still i was able to mount, and i think it was not connected to the bin/cue-mounting.)

I also made a mountcue script, but still i am not sure, is it necessary to have 2-3 different scripts?

Outcome: when i run the scripts now, nothing happens.

Thats it, i hope You could give me some hints whats going on?

Thanks

---

### Post by Jose Catre-Vandis on 2006-09-17
All installed OK, mounts iso files fine, but not mounting nrg files (typically the ones I want to mount!). This is an audio cd it won't mount?

---

### Post by GuruX on 2007-11-06
I'm getting error with the install script for cdemu. Running Gutsy, swedish translation.

```

gustav@lillenubuntu:~/Skrivbord$ sudo sh cdemu-etc

--------------------------------------
cdemu nrg2iso ccd2iso bchunk installer
system optimizer
--------------------------------------

Select one of these download mirrors
or type quit.

You must type the name exactly.

belnet easynews heanet internap
jaist keihanna kent mesh ovh
superb surfnet switch ufpr umn

kent
[: 29: ==: unexpected operator
[: 40: ==: unexpected operator

You failed to select a mirror.

Good-bye.

gustav@lillenubuntu:~/Skrivbord$ 

```

---

