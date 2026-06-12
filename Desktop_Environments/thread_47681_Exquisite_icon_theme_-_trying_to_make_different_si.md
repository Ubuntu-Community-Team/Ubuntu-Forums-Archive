---
title: "Exquisite icon theme - trying to make different sizes"
date: 2005-07-09
forum: Desktop Environments
---

### Post by lakcaj on 2005-07-09
Hi.


I really like the exquisite icon theme for gnome, which can be found here:
[http://www.gnome-look.org/content/show.php?content=16006](http://www.gnome-look.org/content/show.php?content=16006)

Well, I tweaked the buildset script and made a new index.theme file so that all the different sized icons could be created from this theme.  

Well, all you have to do is download the tarball from gnome.org, extract it, and then copy the buildset and new index.theme file into the created directory.  Then, run buildset and it will create a new tarball that can be extracted in /usr/share/icons.

BUILDSET
```

#!/bin/bash

# (C) Nick Bargnesi nbargnesi at den-4.com
# This script is distributed under the GPL.  See the file GPL.
# If you make any improvements, feel free to email me any changes. nbargnesi at den-4.com


# PACKAGENAME is the final tarred, compressed, iconset.
PACKAGENAME="Exquisite"
REQUIRED_SIZES="32x32 22x22 16x16"

SIZES="128x128 96x96 72x72 64x64 56x56 48x48 $REQUIRED_SIZES"
DIRS="apps devices emblems filesystems mimetypes"

CONVERT_PATH=
TAR_PATH=
COMPRESSOR=
function checkCompressor() {
	echo -ne "Checking for bzip2... "
	FOUND=`which bzip2`
	if [ "$FOUND" != "" ]; then
		echo -ne "found $FOUND\n"
		COMPRESSOR=$FOUND
		return
	else
		echo -ne " no.\n"
		echo -ne "Checking for gzip... "
		FOUND=`which gzip`
		if [ "$FOUND" != "" ]; then
			echo -ne "found $FOUND\n"
			COMPRESSOR=$FOUND
			return
		else
			echo -ne " no.\n"
			echo -ne "\nNo compressor found (bzip2 | gzip).\n"
			exit 1
		fi
	fi
}
function checkNeeded() {
	echo -ne "Checking for tar... "
	FOUND=`which tar`
	if [ "$FOUND" != "" ]; then
		echo -ne " found $FOUND\n"
		TAR_PATH=$FOUND
		echo -ne "Checking for convert... "
		FOUND=`which convert`
		if [ "$FOUND" != "" ]; then
			echo -ne " found $FOUND\n"
			CONVERT_PATH=$FOUND
			return
		else
			echo -ne " no.\n"
			echo -ne "\nNo convert found in path.\n"
			exit 1
		fi
	else
		echo -ne " no.\n"
		echo -ne "\nNo tar found in path.\n"
		exit 1
	fi
}
function printFound() {
	echo -ne "\nDependencies met - this script is using:\n"
	echo -ne "\t\t$COMPRESSOR as compressor\n"
	echo -ne "\t\t$TAR_PATH as tar path\n"
	echo -ne "\t\t$CONVERT_PATH as convert path\n"
}

echo -ne "This script builds an installable GNOME iconset using bash and convert.\n"
echo -ne "Change what you want, add additional sizes, whatever... :)\n"
echo

checkCompressor
checkNeeded
printFound

echo
echo -ne "Converting all icons!\n"
echo

#Loop directory creation according to SIZES specified at startup
for size in $SIZES
do
	mkdir -p $size/apps $size/devices $size/emblems $size/mimetypes $size/filesystems
done

# Mmmm... loops...
for dir in $DIRS
do
	cd 128x128/$dir
	for icon in *
	do
		# Loop the specified sizes
		for size in $SIZES
		do
			convert "$icon" -resize $size ../../$size/$dir/"$icon"
		done
	done
	# Move from 128x128/$directory to toplevel
	cd ../../
done

# Move to top directory

mkdir $PACKAGENAME
cp index.theme $PACKAGENAME
cp buildset $PACKAGENAME

for size in $SIZES
do
	mv $size $PACKAGENAME
done

echo -ne "\nDone with conversions.\n"
echo -ne "Tarring and compressing.\n"
if test -f $COMPRESSOR
	then
		tar cf $PACKAGENAME.tar $PACKAGENAME && $COMPRESSOR $PACKAGENAME.tar
		echo -ne "\nThe $PACKAGENAME icon set has been built.\n"
		echo && ls -sh $PACKAGENAME.tar* && echo
fi
echo -ne "Removing all temporary directories...\n"
rm -fr $PACKAGENAME

echo -ne "\nAll done. ;)\n"

```

index.theme
```

[Icon Theme]
Name=Exquisite
Inherits=gnome
Directories=\
128x128/apps,128x128/devices,128x128/emblems,128x128/filesystems,128x128/mimetypes,\
96x96/apps,96x96/devices,96x96/emblems,96x96/filesystems,96x96/mimetypes,\
72x72/apps,72x72/devices,72x72/emblems,72x72/filesystems,72x72/mimetypes,\
64x64/apps,64x64/devices,64x64/emblems,64x64/filesystems,64x64/mimetypes,\
56x56/apps,56x56/devices,56x56/emblems,56x56/filesystems,56x56/mimetypes,\
48x48/apps,48x48/devices,48x48/emblems,48x48/filesystems,48x48/mimetypes,\
32x32/apps,32x32/devices,32x32/emblems,32x32/filesystems,32x32/mimetypes,\
22x22/apps,22x22/devices,22x22/emblems,22x22/filesystems,22x22/mimetypes,\
16x16/apps,16x16/devices,16x16/emblems,16x16/filesystems,16x16/mimetypes

[128x128/apps]
Size=128
Context=Applications
Type=Fixed

[128x128/devices]
Size=128
Context=Devices
Type=Fixed

[128x128/emblems]
Size=128
Context=Emblems
Type=Fixed

[128x128/filesystems]
Size=128
Context=FileSystems
Type=Fixed

[128x128/mimetypes]
Size=128
Context=MimeTypes
Type=Fixed

[96x96/apps]
Size=96
Context=Applications
Type=Fixed

[96x96/devices]
Size=96
Context=Devices
Type=Fixed

[96x96/emblems]
Size=96
Context=Emblems
Type=Fixed

[96x96/filesystems]
Size=96
Context=FileSystems
Type=Fixed

[96x96/mimetypes]
Size=96
Context=MimeTypes
Type=Fixed

[72x72/apps]
Size=72
Context=Applications
Type=Fixed

[72x72/devices]
Size=72
Context=Devices
Type=Fixed

[72x72/emblems]
Size=72
Context=Emblems
Type=Fixed

[72x72/filesystems]
Size=72
Context=Filesystems
Type=Fixed

[72x72/mimetypes]
Size=72
Context=Mimetypes
Type=Fixed

[64x64/apps]
Size=64
Context=Applications
Type=Fixed

[64x64/devices]
Size=64
Context=Devices
Type=Fixed

[64x64/emblems]
Size=64
Context=Emblems
Type=Fixed

[64x64/filesystems]
Size=64
Context=Filesystems
Type=Fixed

[64x64/mimetypes]
Size=64
Context=Mimetypes
Type=Fixed

[56x56/apps]
Size=56
Context=Applications
Type=Fixed

[56x56/devices]
Size=56
Context=Devices
Type=Fixed

[56x56/emblems]
Size=56
Context=Emblems
Type=Fixed

[56x56/filesystems]
Size=56
Context=Filesystems
Type=Fixed

[56x56/mimetypes]
Size=56
Context=Mimetypes
Type=Fixed

[48x48/apps]
Size=48
Context=Applications
Type=Fixed

[48x48/devices]
Size=48
Context=Devices
Type=Fixed

[48x48/emblems]
Size=48
Context=Emblems
Type=Fixed

[48x48/filesystems]
Size=48
Context=Filesystems
Type=Fixed

[48x48/mimetypes]
Size=48
Context=Mimetypes
Type=Fixed

[32x32/apps]
Size=32
Context=Applications
Type=Fixed

[32x32/devices]
Size=32
Context=Devices
Type=Fixed

[32x32/emblems]
Size=32
Context=Emblems
Type=Fixed

[32x32/filesystems]
Size=32
Context=Filesystems
Type=Fixed

[32x32/mimetypes]
Size=32
Context=Mimetypes
Type=Fixed

[22x22/apps]
Size=22
Context=Applications
Type=Fixed

[22x22/devices]
Size=22
Context=Devices
Type=Fixed

[22x22/emblems]
Size=22
Context=Emblems
Type=Fixed

[22x22/filesystems]
Size=22
Context=Filesystems
Type=Fixed

[22x22/mimetypes]
Size=22
Context=Mimetypes
Type=Fixed

[16x16/apps]
Size=16
Context=Applications
Type=Fixed

[16x16/devices]
Size=16
Context=Devices
Type=Fixed

[16x16/emblems]
Size=16
Context=Emblems
Type=Fixed

[16x16/filesystems]
Size=16
Context=Filesystems
Type=Fixed

[16x16/mimetypes]
Size=16
Context=Mimetypes
Type=Fixed

```

Thanks in advance for any suggestions.

---

