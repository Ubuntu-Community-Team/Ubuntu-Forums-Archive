---
title: "Command line geek question"
date: 2008-12-20
forum: General Help
---

### Post by IKhider on 2008-12-20
Greetings Ubuntu Users, 

Is there a way to convert raw image files in a folder to jpeg files? There are loads of pictures I took with a Canon camera that saves them as .crw which gimp has trouble with. I want to convert them to jpeg so I can work with them easier. 

Anyone know?

-i-

---

### Post by p_quarles on 2008-12-20
The "convert" command (part of the imagemagick utility suite) can do this, so long as both formats are supported. Camera raw isn't specifically mentioned in the man page, but may be supported. 

The syntax is easy:
```
convert image.gif image.jpg
```

---

### Post by unutbu on 2008-12-20
If imagemagick does not support your type of raw format, then do this:

Install imagemagick and dcraw:
```

sudo apt-get install imagemagick
sudo apt-get install dcraw
```
The command to convert img_2539.cr2 to img_2539.jpg would be:

```
dcraw -Tc img_2539.cr2 | convert tiff:- img_2539.jpg 
```

The dcraw command outputs a tiff file. The 'convert' app converts the tiff data to jpg.

---

### Post by sarang on 2008-12-20
You need to have the dcraw, cjpeg and exiftool programs installed:

```

sudo apt-get install libimage-exiftool-perl libjpeg-progs dcraw

```

Then create the directory ~/bin and create a file named crw2jpeg-script.bash in it and make it executable.
```

mkdir ~/bin
cd ~/bin
touch crw2jpeg-script.bash
chmod +x crw2jpeg-script.bash

```

Then open the file in a text editor and paste the following contents in it:

**Edit: This version of the script will get confused by special characters etc. A better version is posted in this thread as post # 6. Please use that version. All other usage details remain the same.**
```

#!/bin/bash
DCRAW="dcraw -w -c "


while [ $# -ge 1 ]
do

targetdir=$1

for rawfile in $targetdir/*.[cC][rR][wW]

do
    	
    OJPEG=$(echo $rawfile| perl -pe 's/\.crw$//i' | tr 'A-Z' 'a-z')'.jpeg'
    echo "${DCRAW} $rawfile | cjpeg > ${OJPEG}"
    ${DCRAW} -q 3 $rawfile | cjpeg -quality 100 > ${OJPEG} || echo " *PROBLEM*"
    # transfer EXIF data from the original raw file
    exiftool -overwrite_original -TagsFromFile "$rawfile" "${OJPEG}" >/dev/null
    # preserve timestamps as much as possible
    # touch -r "$rawfile" "${OJPEG}"
    dcraw -z "${OJPEG}"

    # UNCOMMENT to delete raw files:
    # rm -f $rawfile

done
    shift
    
done

```

This script uses raw files to create equivalent high quality jpegs with same exif data. It can also delete the original raw files if you uncomment the relevant line in it.

[FONT="Courier New"]bash ~/bin/crw2jpeg-script dir1 dir2 dir3[/FONT] should create jpeg files for raw files in dir1, dir2 and dir3.

---

### Post by IKhider on 2008-12-20
Hello Repliers, 

First thanks to p_quarles and Unutbu--I have figured out how to convert .CRW files to .TIFF files. Then I converted them to .JPEG's 

I was wondering if there was a way to skip the TIFF files and go straight to jpeg. 

To facilitate the ease of plugin use I installed the Ubuntu studio graphic suite. 

Now Sarang's response is intriguing, it seems to skip the TIFF process. I am just worried about re-installing things I might already have. Let me give Sarang's proccess a try and then I will get back to ye. 

Thanks!

-I-

---

### Post by sarang on 2008-12-20
I want to post a better version of my script. Unlike the previous one, this version won't be confused by special characters like spaces in file and directory names:

```

#!/bin/bash
DCRAW="dcraw -w -c "


while [ $# -ge 1 ]
do

targetdir="$1"

for rawfile in "$targetdir"/*.[cC][rR][wW]

do
    	
    OJPEG=$(echo "$rawfile"| perl -pe 's/\.crw$//i' | tr 'A-Z' 'a-z')'.jpeg'
    echo "${DCRAW} "$rawfile" | cjpeg > ${OJPEG}"
    ${DCRAW} -q 3 "$rawfile" | cjpeg -quality 100 > "${OJPEG}" || echo " *PROBLEM*"
    # transfer EXIF data from the original raw file
    exiftool -overwrite_original -TagsFromFile "$rawfile" "${OJPEG}" >/dev/null
    # preserve timestamps as much as possible
    # touch -r "$rawfile" "${OJPEG}"
    dcraw -z "${OJPEG}"

    # UNCOMMENT to delete raw files:
    # rm -f "$rawfile"

done
    shift
    
done

```

---

### Post by sarang on 2008-12-23
Just learnt about the packages gimp-dcraw and gimp-ufraw. Don't know hw good the plugins are though.

Edit:
I also found [RawTherapee]("http://www.rawtherapee.com/") and [RawStudio]("http://rawstudio.org/").

---

