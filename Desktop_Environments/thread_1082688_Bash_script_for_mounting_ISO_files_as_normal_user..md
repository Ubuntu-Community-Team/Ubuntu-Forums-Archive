---
title: "Bash script for mounting ISO files as normal user."
date: 2009-02-28
forum: Desktop Environments
---

### Post by etrash2000 on 2009-02-28
Hi, 

I would like to submit a script for preview and testing. 

It is a simple script for mounting and unmounting an ISO image. I have seen other script in this forum but most of them seem to require root privilege at mount time as they are using sudo/gksudo. This script requires root privilege only at installation time. The installation instructions are in the code as comments.

The script features following:

[LIST]
[*]Mount / Unmount from shell.
[*]Mount / Unmount from file-managers via Action scripts (Nautilus and Thunar has been tested successfully).
[*]Unmount from desktop / Diskmounter.
[/LIST]


Please let me know what you think about it.

With regards,
Erdal Suvar
Germany.
 




```


#!/bin/bash

##################################################
# Copywrite Dr Erdal Suvar, Frankfurt Oder, Germany, February 25th, 2009.   #
# Licence: GPLv3                                                                                                #
##################################################

# NAME:
# MountISO

# DESCRIPTION:
# This script allows a normal user to mount and unmount an ISO image into the filesystem without the need for root privilage. 

# USAGE:
# Mounting: MountISO imagefile.iso 
# Unmounting: MountISO imagefile.iso 

# INSTALLATION
# Step 1:
# Make sure that this script is executable (i.e. chmod a+x MountISO). 
# 
# Step 2:
# A root privilaged user must enable this script by modifying the "fstab" file in order for this script to work. 
# The required modification is to add the following lines (without the first comment sign "#") in your /etc/fstab file
#
#      # The MountISO script is assuming maximum 3 simultaneously mounted ISO files.
#      # You can easily extend this by adding corresponding lines in the fstab file.
#
#      # These are needed for for mounting
# 	/tmp/ISO1 /media/ISO1 iso9660 ro,loop=/dev/loop1,users,noauto 0 0
# 	/tmp/ISO2 /media/ISO2 iso9660 ro,loop=/dev/loop2,users,noauto 0 0
# 	/tmp/ISO3 /media/ISO3 iso9660 ro,loop=/dev/loop3,users,noauto 0 0
#      # ... 
#
#      # These are needed for unmounting
# 	/dev/loop1      /media/ISO1 iso9660 ro,loop=/dev/loop1,users,noauto 0 0
# 	/dev/loop2      /media/ISO2 iso9660 ro,loop=/dev/loop2,users,noauto 0 0
# 	/dev/loop3      /media/ISO2 iso9660 ro,loop=/dev/loop3,users,noauto 0 0
#      # ...
#
# Step 3:
# You also need to create (i.e. sudo mkdir) the following mounting points /media/ISO1, /media/ISO2 and so forth.


# NOTES FOR FILEMANAGERS.
# If you intend to call this script from a filemanager than make sure that you configure your filemanager to supply the FULLPATH of the iso file. 
# If you have problem, remove the comment from the debugging section to see if you are supplying the fullpath. 
# The correct parameter for Thunar Actions is %f .
# The correct parameter for Nautilus Actions is %M.
#
# You can use this script with relative path if you call it directly from shell. 

# NOTES.
# This script uses "zenity" to display messages to the user but these are not critical and can be removed or changed to "echo". 

# REVISION
# 2009-02-24: First version.  Based on ISOMount which required root account.



	# Configure Section
		FULLNAME="${1}"
		if [ "${FULLNAME:0:1}" != "/" ]; then				# Convert to absolute path if this script is called directly from the shell.
			FULLNAME="$PWD/${FULLNAME}"
		fi
		FILE="${FULLNAME##*/}"							# get base name, i.e. everything after last '/' (can also use `basename "$FULLNAME"`)
		FILE_EXT="${FILE##*.}"							# get extension, i.e. everything after last '.'	
		FILE_EXTC=`echo ${FILE_EXT} | tr a-z A-Z`			# Change to upper case letters.
		FILE_NAME="${FILE%.${FILE_EXT##*.}}"
		FILE_PATH="${FULLNAME%/$FILE}"					# get directory name, i.e. everything before last '/' (can also use dirname=`dirname "$FULLNAME"`)

		# for debugging
		MSG=""
		MSG="$MSG\nFULL=$FULLNAME\n"
		MSG="$MSG\nFile=$FILE"
		MSG="$MSG\nFilename=$FILE_NAME"
		MSG="$MSG\nFile ext=$FILE_EXTC"
		MSG="$MSG\nFile path=$FILE_PATH"
		#zenity --info --text="$MSG"

		# Checking file extension is ISO
		if [ ${FILE_EXTC} != "ISO" ]; then
			MSG=""
			MSG="$MSG\n Filetype \"${FILE_EXT}\" can not be mounted with this script."
			MSG="$MSG\n Only ISO images are supported.\n"
			MSG="$MSG\n You can try to convert your image to ISO with one of the"
			MSG="$MSG\n following applications nrg2iso, ccd2iso, mdf2iso or use cdemu."
			zenity --error --title "Wrong filetype" --text "${MSG}"; 
			exit 1;		 
		fi

		# Check if file is already mounted, unmount it in that case.
		# zenity --info --text="We will first try to Umount it."
		for n in {1..3}
		do
			MNT_PNT="/media/ISO${n}"
			MNT_LNK="/tmp/ISO${n}"
			MNT_IMG=`exec readlink ${MNT_LNK}`
			MNTED=`exec mount | grep "on ${MNT_PNT} type" `
			# zenity --info --text="Unmouting\nMNT_PNT: ${MNT_PNT}\nMNT_LNK: ${MNT_LNK}\nMNT_IMG: ${MNT_IMG}\nFILE: ${FULLNAME}\nMNTED: ${MNTED}"
			# Check if link is poiting to our file and mounted.
			if  [ "${MNT_IMG}" ==  "${FULLNAME}" ] && [ -n "${MNTED}" ]; then
				# Try to unmount it.
				if  (/bin/umount "${MNT_PNT}" && /bin/rm "${MNT_LNK}" ); then
					# zenity --info --title "Image unmounted succesfully" --text="The following image was unmounted: \n$FULLNAME\n"
					exit 0
				else
					zenity --error --title "Error unmounting image" --text="The following image could not be unmounted or deleted: \n${MNT_IMG}."
					exit 1
				fi
			fi
		done
		
		# The ISO image do not seem to be mounted. 
		# zenity --info --text="We will try to mount it."
		for n in {1..3}
		do 
			MNT_PNT="/media/ISO${n}"
			MNT_LNK="/tmp/ISO${n}"
			MNTED=`exec mount | grep "on ${MNT_PNT} type" `			
			# zenity --info --text="Mounting\nMNT_PNT: ${MNT_PNT}\nMNT_LNK: ${MNT_LNK}\nFILE: ${FULLNAME}\nMNTED: ${MNTED}"
			if  [  -z  "${MNTED}" ] && [ -e "${FULLNAME}" ]; then
				ln -s -f "${FULLNAME}" "${MNT_LNK}"
				/bin/mount "${MNT_PNT}"
				MSG=""
				MSG="$MSG\n The following image was mounted: \n$FULLNAME\n"
				MSG="$MSG\n The mountpoint is:\n $MNT_PNT"
				# zenity --info --title "Image mounted succesfully" --text="${MSG}"
				exit 0
			fi
		done
	
		# If you reach this point then you failed to mount for some reason. 
		zenity --error --title "Error mounting image" --text="The following ISO could not be mounted: \n${FULLNAME}\n Maybe you are trying to mount too many ISO files."
		exit 1

```

---

### Post by qrwe on 2009-02-28
Nice!
Though:
> ioctl: LOOP_SET_FD: Invalid argument
...and there's a soft link at the Desktop after running this.

---

### Post by etrash2000 on 2009-02-28
Hi,

I also get the "ioctl" error but I also get this when I mount an ISO manually so I am not sure what it means. Maybe someone else know what it means and know to correct it.

The "softlink" is wanted as the mount point is in /media and not in /mnt. You can change this in the script but then the ISO will not show up as a device in the file manager. In my case I get an device icon of a CD to indicate the mounted ISO. You can use this device icon (the softlink) to unmount the ISO directly. 

The desktop link is labeled as ISOX (X=1,2,3,...) and it corresponds to the mount point. I do not know how to change this label without changing the mountpoint (which needs to be fixed in fstab).

---

### Post by qrwe on 2009-02-28
> **etrash2000 said:**
> 
The "softlink" is wanted as the mount point is in /media and not in /mnt. 
Yeah, read that in the script. It's just that the soft links is created even if the mount itself doesn't work.
Hope that 'ioctl' thing can be explained and fixed as I'm trying to install a game under wine which spans over multiple CD:s. When I have to change CD (in this case: iso) to continue, an unmount command isn't possible as it's locked by wine. The only thing I can think  of now is if someone can make it possible to mount iso:s without su permission.

---

### Post by etrash2000 on 2009-03-01
Hi,

I have looked into the "ioctl" error but with no luck. It seems to be connected with how loop devices work. For example, you can run the following in bash to see this.

```

# Implicit usage of /dev/loop0
# No error message 
sudo mount image.iso /media/ISO -o loop
sudo umount /media/ISO 

# Explicit usage of /dev/loop0
# Results in error message
sudo mount image.iso /media/ISO -o loop=/dev/loop0
sudo umount /media/ISO 

```

The first option is not possible to use in this scrip as I would lose the possibility to umount an image. 

In any case, this error message do not seem to cause to much problems (at least for me) as I am able to mount and unmount as I want from the file-manager. 


PS. Have you tried to make a single ISO file (look into mkisofs) of all your images. This might help with your problem with wine.


PSS. This is not connected with your problems but I made I small update of the script. It will now look if a loop-device is already in use before trying to use it. See the attachment if you are interested.

---

### Post by qrwe on 2009-03-03
Yep, this happened to me when simply unmounting iso files which was mounted into those directories. Suppose this is the major bug now.
BTW, I really hope hope the Ubuntu developers will make a way to mount iso files without root permission, built-in. That will solve all these goofy problems and will be well recieved for non-CD laptop (EeePC) owners like myself.

---

