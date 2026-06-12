---
title: "Scripts"
date: 2005-09-11
forum: Desktop Environments
---

### Post by cbudden on 2005-09-11
Could someone please give a full HowTo on how i would go about installing nautilus scripts.  I have a image resize script, put it in the ~/.gnome2/nautilus-scripts folder but it does not appear in my right click menu.  Thanks for you help.

---

### Post by mlomker on 2005-09-11
Is the script executable?  [Starter Guide](http://ubuntuguide.org/#openfilesasrootviarightclick)

---

### Post by cbudden on 2005-09-11
Im not sure how i should change the command in the guide.  The script is called NIS and the contents is below. 


#!/bin/sh
# Author : Mathieu Vilaplana <mathieu@creationgif.com>
# Date : 09/03/2005
#depends: imagemagick, zenity
# thanks to coffe
#version 0.3
#	- check mime type

#test if a file has been selected
if [ $# -eq 0 ]; then
	zenity --error --title="error" --text="You must select at least 1 file to process"
	exit 1
fi

#show the select size dialog		
title="Choose which sizes to scale to"
imgsize=`zenity --title "$title"  --list --separator=" " --column="size" "160x120" "320x240" "640x480" "800x600" "800x600" "1024x768" | sed 's/ max//g' `

#if $? != 0, user click on cancel button, so exit
if [ "$?" != 0 ] ; then
	exit
fi

#user must select a target size
if [ ! "$imgsize" ]; then
	zenity --error --title="error" --text="select a target size"
	exit
fi

#transform 640x480 en 640x640 for convert to respect proportions
val1=`echo "$imgsize" | awk -F'x' '{ print $1  }'`
imgsize="${val1}x${val1}"


#Select only images
mime=`file -bi $*`
nb_images=`echo "$mime" | grep image  | wc -l`

let "nbfiles = $nb_images"
#compteur=0;
(while [ $# -gt 0 ]; do
	picture=$1
	mime=`file -bi $picture`
	isimage=`echo "$mime" | grep image  | wc -l`
	if [ $isimage -eq 0 ]; then
		zenity --error --title="error" --text="$picture is not an image"
	else	
		echo "# Processing image $picture ..."
		convert -quality 80 -resize $imgsize "$picture" "$imgsize-$picture"
		let "compteur += 1"
		let "progress = compteur*100/nbfiles"
		echo $progress
	fi
	shift
done
) |
        zenity --progress --auto-close --title="Scaling images"  --text="Processing images ..."  --percentage=0

---

### Post by cbudden on 2005-09-11
Ok got it now thanks.  chmod +x NIS  Thanks for your help

---

