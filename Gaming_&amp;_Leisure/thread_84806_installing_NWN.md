---
title: "installing NWN"
date: 2005-11-01
forum: Gaming &amp; Leisure
---

### Post by TuxicGuy on 2005-11-01
Hi folks,
          I downloaded the nwn-install.sh script from icarus.org, mentioned in one of the threads in this forum. Having specified the install as CD - and cdrom device as /media/cdrom - when asked to insert CD 2 - i do so and gnome automounts it (I informed the script NOT to mount CD's as this is done automatically) - however the script does not recognize the fact that the CD is already mounted and keeps asked for me to insert the disk. Could someone help me out with this? Thanks in advance.

PS: I've posted prior questions in this forum about quake2 and would like to say a big 'Thank you' for all the people who had responded - It is a pleasure to be part of such a helpful community and i hope that i can contribute towards it.

---

### Post by Jacky_J on 2005-11-01
The way I installed NWN is by following the instructions on

    [http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html)

You basically download the client files so you don't even need your CD, just the CD-key that came with the game. That is, of course you're willing to download 1.12 GB.  Another tip is that you need to get the patch to run the game, as i had tried to run just the CD-version and it didn't work.

I try to stay away from third-party install scripts for games because they're usually outdated and don't work for everyone.

---

### Post by TuxicGuy on 2005-11-01
Jacky,
         The reason i used the script is that it gets the game resources right off the CD's - I certainly don't want to download 1.12 GB worth of files that could be fetched from the CD itself. But you do have a point - the script mentions that  it is to be used for the platinum edition of the game and i'm trying to use it for normal NWN , SoU and HoTU (purchased separately). This boils down to a problem of not being able to see the cdrom drive. I've attached the script that i'm using. i hope that helps.

Regards,

TuxicGuy


#!/bin/sh
# Neverwinter Nights installer
# Version: 1.3
# Written by Morgan Galpin
# Additional changes by Steve Ellis
# date: November 1, 2004
# updated by Steve Ellis: July 08, 2005
#            (untested please let me know if it works or not)
# email: [email]icarus.lnx@gmail.com[/email]
# original file name: install-nwn.sh
#---------------------------------------------------------------------
# This script installs Neverwinter Nights Platinum from the CDs.
# It also applies the current hotu patch, which can be obtained from
# the Bioware website. The orginal game plus both expansion packs
# are installed since that seems to be the point of buying the
# Platinum version.
# 
# Instructions:
# 
# Make sure you meet the few requirements below, set the 
# configuration parameters, then at a shell prompt, type:
#     ./install-nwn.sh
# Enter the CDs when asked to do so, and soon you will be enjoying
# Neverwinter Nights Platinum!
# 
# Note:
# The files installed from the Platinum CDs and the files from the 
# current hotu patch match those in Eyrdan's valid installation 
# guide md5sums for common and both expansion packs (1 and 5), 
# except for ./fixinstall. The one included with the Platinum CDs 
# may be older, but they only differ by a few characters. It 
# certainly won't break your install.
#--------------------------------------------------------------------
# Additional Notes by Steve Ellis:
# I replaced most of the static options with variables to better
# support various Linux distributions and enhancing the script
# so no manual editing of the script is required.
# The patch to be installed currently needs to be located in the
# installers home directory.
# Slight update to use convert to make the nwn.ico a nwn.xpm for
# used as a menu item
# Slight update to default to the 1.66 patch
# Currently this is mostly aimed at the English version, maybe
# in the future multi-language support will be added
#
# Special Thanks:
# Thanks to pineapple <pineapplecoward@yahoo.com> for suppliing the
# needed information for the DVD install
#---------------------------------------------------------------------
# Requirements:
#
# unshield: You must have this installed since some of the required
#     files are in installshield .cab files. Type 'unshield -h'
#     at your shell prompt to see if you have it installed.
#     If you don't, you can get it from:
#     [http://synce.sourceforge.net/synce/unshield.php](http://synce.sourceforge.net/synce/unshield.php)
#     It's free and it does the job with less patch downloading.
# English_linuxclient166_xp2.tar.gz: The latest linux Hordes
#     of the Underdark patch. Some of the files from the install
#     CDs are not extracted since they would only be overwritten
#     by the latest patch, so you need this. You can get it from:
#     [http://nwn.bioware.com/support/patch.html](http://nwn.bioware.com/support/patch.html)
# Client files: The DVD version requires the Client files as the DVD
#     does not include the needed Linux files to run. This is only
#     needed if you have the DVD, the Linux client files are included
#     in the CD disks on Disk 3.
# The game cds: You need the cds. This script installs most of the
#     files for the game from the cds.
#---------------------------------------------------------------------
# Configuration parameters:
# No trailing slashes (/) for directories.
# The cdrom drive mount point where each of the cds will be
# mounted one at a time.
#OPT_CDROM=/mnt/cdrom
# The destination directory where all the files will be extracted.
# You must have write access to this directory.
#OPT_INSTALL_DIR=/home/nwn
# The current linux client from bioware's website (currently v1.29)
OPT_CLIENT=~/nwclient129.tar.gz
# The patch to apply after the install is done. Some of the
# required files are only found in the patch.
#OPT_PATCH=./linuxhotuclientupdate1xxto165eng.tar.gz
# Whether or not to use the mount command. Some systems automatically
# mount a cdrom drive when a cd is inserted. If your system does this,
# then this should be set to 0. If you have to manually mount cds
# with the mount command, set this to 1. You might have to run the 
# script as root to use the mount command.
#OPT_USE_MOUNT_COMMAND=0
# The username and group to make the owner of all the files.
# If this is other than your own, then the script will have to
# be run as root. If you've opted to OPT_USE_MOUNT_COMMAND, then
# likely you *are* running the script as root and you will want
# to set these options to the user and group that you will play
# the game as.
# OPT_USERNAME=gautam
OPT_USERNAME=`whoami`
#OPT_GROUPNAME=root
#OPT_GROUPNAME=users
# Whether to install from 4 cds or from the dvd.
#OPT_CD_OR_DVD=CD

# End of configuration. Run the script!
#---------------------------------------------------------------------
# Prompt the user and wait for Enter to be pressed. Any input
# is ignored.
# Paramters:
#   $1: The text to use for a prompt.
give_prompt() {
  echo -e "\033[31m$1Press Enter to continue.\033[0m"
  read $ENTER
  return 0
}

# Get user inputed variables
get_input_vars(){
  echo -e "\033[32mTesting for unshield\033[0m"
  unshield_test=`whereis unshield|awk -F:  '{ print $2 }'`
   if [ -z "$unshield_test" ];
    then
     echo -e "\033[31munshield not found!\033[0m"
     echo -e "unshield can be downloaded from http://synce.sourceforge.net/synce/unshield.php"
     echo -e "Try again after installing"
     exit 0
    else
     echo -e "\033[33munshield found, using $unshield_test\033[0m"
   fi

  echo -n "Will the install be using the CD version or DVD version? (CD/dvd): "
  read ready
    if [ -z "$ready" ];
    then
     OPT_CD_OR_DVD=CD
    else
     case $ready in
       cd|CD|cD|Cd)
	 OPT_CD_OR_DVD=CD
	 ;;
       dvd|DVD|dVd|DvD|Dvd|dVD|DVd|dvD)
         OPT_CD_OR_DVD=DVD
	 ;;
       *)
         echo -e "\033[32mPlease use a cd/dvd variant\033[0m"
	 exit 0
	 ;;
     esac
    fi
  echo -e "\033[33mInstall will use the $OPT_CD_OR_DVD version to install\033[0m"

    if [ $OPT_CD_OR_DVD = DVD ]; then
      CLIENT_TEST=`ls $OPT_CLIENT`
            if [ -z $CLIENT_TEST ];
              then
              echo -e "\033[31mClient file not found! Please check that the patch is in your home directory.\033[0m"
echo -en "\033[33mDo you wish to try to download the client? (y/n): \033[0m"
            read client
            case $client in
             y|Y|yes|Yes|YES)
               wget [http://nwdownloads.bioware.com/neverwinternights/linux/129/nwclient129.tar.gz](http://nwdownloads.bioware.com/neverwinternights/linux/129/nwclient129.tar.gz)
             ;;
             n|N|no|No|NO)
              echo -e "\033[32mFailing on the client install, the game will not run without the client files\033[0m"
              echo -e "\033[31mYou can download the client from www.bioware.comhttp://nwn.bioware.com/downloads/linuxclient.html"
          exit 0
             ;;
             *)
              echo -e "\033[32mPlease use a yes/no variant\033[0m"
             ;;
            esac
            else
          echo -e "\033[33mThe client to be installed is $OPT_CLIENT\033[0m"
            fi
    fi




  echo -n "Enter the cdrom path (/mnt/cdrom): "
  read ready
    if [ -z "$ready" ];
    then
     OPT_CDROM=/mnt/cdrom
    else
     OPT_CDROM=$ready
    fi
  CD_TEST=`grep $OPT_CDROM /etc/fstab|wc -l`
    if [ "$CD_TEST" -lt 1 ];
    then
     echo -e "\033[31mINVALID DEVICE! Please check the device and try again\033[0m"
     exit 0
    else
     echo -e "\033[33mcdrom drive is set for $OPT_CDROM\033[0m"
    fi

  echo -n "Enter the install directory (/usr/local/games/nwn): "
  read ready
    if [ -z "$ready" ];
    then
     OPT_INSTALL_DIR=/usr/local/games/nwn
    else
     OPT_INSTALL_DIR=$ready
    fi
  echo -e "\033[33mNeverwinter Nights will install to $OPT_INSTALL_DIR\033[0m"


# Setup/get patch
  echo -n "Enter the current patch version that is located in the users home directory (166): "
  read ready
    if [ -z "$ready" ];
    then
     OPT_PATCHNUM=166
    else
     OPT_PATCHNUM=$ready
    fi
 if [ $OPT_PATCHNUM -eq 166 ]; then
  OPT_PATCH=~/English_linuxclient166_xp2.tar.gz
 else
  OPT_PATCH=~/linuxhotuclientupdate1xxto$OPT_PATCHNUM.tar.gz
 fi
    PATCH_TEST=`ls $OPT_PATCH`
    if [ -z $PATCH_TEST ];
    then
     echo -e "\033[31mPatch Not Found! Please check that the patch is in your home directory\033[0m"
     echo -en "\033[33mDo you wish to try to download this patch? (y/n): \033[0m"
     read patch
     case $patch in
      y|Y|yes|Yes|YES)
       PATCH_VER=`echo $OPT_PATCHNUM|cut -c1-3`
       PATCH_LAN=`echo $OPT_PATCHNUM|cut -c4-6`
       echo "-$PATCH_VER-"
         case $PATCH_VER in
	164)
       wget http://nwdownloads.bioware.com/neverwinternights/linux/164/linuxhotuclientupdate1xxto$OPT_PATCHNUM.tar.gz
       ;;
        165)
       wget http://content.bioware.com/neverwinternights/linux/165/linuxhotuclientupdate1xxto165$PATCH_LAN.tar.gz
      ;;
        166)
       wget [http://content.bioware.com/neverwinternights/linux/166/English_linuxclient166_xp2.tar.gz](http://content.bioware.com/neverwinternights/linux/166/English_linuxclient166_xp2.tar.gz)
      ;;
        *)
       echo -e "\033[32mPatch not needed for versions older then 1.64\033[0m"
      ;;
        esac
	;;
      n|N|no|No|NO)
       echo -e "\033[32mSkipping patch, there WILL be errors at the end of the install\033[0m"
      ;;
      *)
       echo -e "\033[32mPlease use a yes/no variant\033[0m"
      ;;
    esac
    else
     echo -e "\033[33mThe patch to be installed is $OPT_PATCH\033[0m"
    fi

  echo -n "Do you wish for the script to mount the CD (Y/n): "
  read ready
    if [ -z "$ready" ];
     then
      OPT_USE_MOUNT_COMMAND=1
     else
     case $ready in
       y|Y|yes|Yes|YES)
	 OPT_USE_MOUNT_COMMAND=1
	 ;;
       n|N|no|No|NO)
         OPT_USE_MOUNT_COMMAND=0
	 ;;
       *)
         echo -e "\033[32mPlease use a yes/no variant\033[0m"
	 exit 0
	 ;;
     esac
     fi
  echo -e "\033[33mThe CD setting for mounting is $OPT_USE_MOUNT_COMMAND\033[0m"

  echo ""

  echo -e "\033[33mThe game will be installed as user '$OPT_USERNAME'\033[0m"
  

  echo -n "What Group should the game be installed as (users): "
  read ready
    if [ -z "$ready" ];
    then
     OPT_GROUPNAME=users
    else
     OPT_GROUPNAME=$ready
    fi
   GROUP_TEST=`awk -F: '{ print $1 }' /etc/group|grep $OPT_GROUPNAME`
    if [ -z "$GROUP_TEST" ];
    then
      echo -e "\033[31mInvalid Group name\033[0m"
      exit 0
    else
      echo -e "\033[33mThe group is set to $OPT_GROUPNAME\033[0m"
    fi
}
# Get all desired zip files from a disk:
# Parameters:
#   $1: The disk number, ie. 1, 2, 3, or 4.
#   $@: The list of files to get, eg. "disk4" "xp1" "xp1_data"
get_zips_on_disk() {
  disk_num="$1"
  shift
  give_prompt "Please insert Neverwinter Nights disk \033[32m$disk_num\033[0m \033[31min\033[0m \033[33m$OPT_CDROM\033[0m\n"
  if [ $OPT_USE_MOUNT_COMMAND -eq 1 ]; then
    mount $OPT_CDROM
  fi
  for file in $@
  do
    filename="$OPT_CDROM/$file.zip"
    while [ ! -r "$filename" ]; do
      give_prompt "Cannot read \"$filename\".\033[0m\nPlease check that disk \033[32m$disk_num\033[0m is in \033[33m$OPT_CDROM\033[0m\n"
    done
    unzip -o "$filename"
  done
  
  return 0
  }
  get_zips_on_dvd(){
  give_prompt "Please insert Neverwinter Nights Platinum \033[32mDVD\033[0m \033[31min\033[0m \033[33m$OPT_CDROM\033[0m\n"
  if [ $OPT_USE_MOUNT_COMMAND -eq 1 ]; then
    mount $OPT_CDROM
  fi
    for file in $@
      do
        filename="$OPT_CDROM/$file.bzf"
      while [ ! -r "$filename" ]; do
       give_prompt "Cannot read \"$filename\".\033[0m\nPlease check that disk \033[32m$disk_num\033[0m is in \033[33m$OPT_CDROM\033[0m\n"
      done
    unzip -o "$filename"
    done

    return 0
}
# Unmount the cd only if that's what the user wants.
do_umount()
{
  if [ $OPT_USE_MOUNT_COMMAND -eq 1 ]; then
    eject $OPT_CDROM
  fi
  return 0
}

# Same as get_zips_on_disk(), but unmounts the cdrom afterwards.
get_zips_on_disk_umount() {
  get_zips_on_disk $@
  do_umount
  return 0
}
# Conditionally create a directory.
# Parameters:
#   $1: The name of the directory to create.
make_dir() {
  if [ -d "$1" ]; then
    if [ ! -w "$1" ]; then
      echo "You do not have write permission for $1!" 1>&2
      return 1
    else
      return 0
    fi
  else
    if ( mkdir "$1"); then
      return 0
    else
      echo "Unable to create $1!" 1>&2
      return 1
    fi
  fi
}
# Create a directory and enter it.
# Parameters:
#   $1: The name of the directory to create and enter.
make_and_enter() {
  if ( make_dir "$1" ); then
    cd "$1"
    return 0
  else
    return 1
  fi
}
# Get variables from user input
get_input_vars

# Make the destination directory:
make_and_enter "$OPT_INSTALL_DIR" || exit 1
# Unpack all the needed zip files.
if [ $OPT_CD_OR_DVD = CD ]; then
get_zips_on_disk_umount 2 "disk2"
get_zips_on_disk_umount 3 "disk3" "language_data" "Data_Linux"
get_zips_on_disk_umount 4 "disk4" "xp1" "xp1_data"
get_zips_on_disk 1 "Data_Shared" "Language_data"
 else
 get_zips_on_dvd "Data_Shared" "Language_data" "Language_update"
fi
# Get some files from the cab files.
make_and_enter unshielded_files
unshield x $OPT_CDROM/data1.hdr
make_dir ../nwm/
mv -f NWN_Platinum/nwm/* ../nwm/
make_dir ../docs/
mv -f NWN_Platinum/docs/* ../docs/
make_dir ../modules/
mv -f NWN_Platinum/modules/* ../modules/
cd ..
rm -rf unshielded_files
cp $OPT_CDROM/nwn.ico $OPT_INSTALL_DIR/nwn.ico
do_umount
# Install linux binaries if DVD version is selected (currently v1.29)
if [ $OPT_CD_OR_DVD = DVD ]; then
echo Extracting $OPT_CLIENT
tar -xvzf $OPT_CLIENT
fi
# Apply the current patch.
rm -rf override # Not needed, but for good measure.
echo Extracting $OPT_PATCH ...
tar -xvzf $OPT_PATCH
# Fix any files that need fixin'.
# Should not be needed with the 1.66 patch
mv ./texturepacks/xp2_gui.erf ./texturepacks/XP2_GUI.erf
chown -R $OPT_USERNAME:$OPT_GROUPNAME *
./fixinstall
# Give final instructions.
echo "Add \"cd $OPT_INSTALL_DIR\" to \"$OPT_INSTALL_DIR/nwn\" to be able to run Neverwinter Nights from anywhere. You may also want to add a symbolic link to it from a bin directory, or somewhere else in your PATH."
echo "Enjoy!"
echo -e "\033[32mTesting for ImageMagick convert\033[0m"
  convert_test=`whereis convert|awk -F:  '{ print $2 }'`
   if [ -z "$convert_test" ];
    then
     echo -e "\033[31mconvert not found!\033[0m"
     echo -e "convert is a part of the Image Magick tools, used here to make the nwn.iso a Linux friendly nwn.xps"
     echo -e "Skipping image conversion"
    else
     echo -e "\033[33mMaking nwn.xpm\033[0m"
	convert nwn.ico nwn.xpm
   fi
exit 0

---

