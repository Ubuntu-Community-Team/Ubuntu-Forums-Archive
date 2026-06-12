---
title: "Best way to mount an image from inside Nautilus?"
date: 2009-11-11
forum: Desktop Environments
---

### Post by last1 on 2009-11-11
I've read about Nautilus-mount-image, but the developer says it's no longer being developed because you can do it with gvfs. I have no idea what that means or how you do that, but I do know that doing it the manual way that I usually do it is tedious, seems to me there should be a more automated method for doing it from within the file manager itself, so any suggestions?

---

### Post by Keith Hedger on 2009-11-11
put this:```
#!/bin/bash

DIRNAME=$(echo $NAUTILUS_SCRIPT_CURRENT_URI | cut -d'/' -f3- | sed 's/%20/ /g')
FILENAME=$1
if [ ! -f "$DIRNAME/$FILENAME" ];then
	zenity --error --text="$DIRNAME/$FILENAME\nIs Not A File"
	exit 0
fi

foo=$(gksudo -u root -k -m "Enter Your Admin Password" /bin/echo "got r00t?")
sudo mkdir "/media/$FILENAME"
sudo mount -o loop "$DIRNAME/$FILENAME" "/media/$FILENAME"

```
in a file in ~/.gnome2/nautilus-scripts call it somthing like "Mount iso" make it executable then just right click on an iso and select Scripts->Mount iso and roberts your mothers brother!

---

### Post by Zoot7 on 2009-11-11
Gmount-Iso is another nifty way of doing it.
```
sudo apt-get install gmountiso
```

It's basically a front end for the command line way:
```
sudo mount -t iso9660 -o loop <image> <mount point>
```

---

### Post by last1 on 2009-11-11
Thanks, the script is working great.

---

### Post by durand on 2009-11-11
Strange, I have a right click option in my nautilus. I can't be any help to you though cos I have no idea how it got there :S

---

### Post by nowhere@cox.net on 2009-11-11
You can check this page out too for a more "complete" treatment of the issue...

[Community Documentation: Manage Disc Images]("https://help.ubuntu.com/community/ManageDiscImages")

---

### Post by keypox on 2009-11-12
> **Keith Hedger said:**
> put this:```
#!/bin/bash

DIRNAME=$(echo $NAUTILUS_SCRIPT_CURRENT_URI | cut -d'/' -f3- | sed 's/%20/ /g')
FILENAME=$1
if [ ! -f "$DIRNAME/$FILENAME" ];then
	zenity --error --text="$DIRNAME/$FILENAME\nIs Not A File"
	exit 0
fi

foo=$(gksudo -u root -k -m "Enter Your Admin Password" /bin/echo "got r00t?")
sudo mkdir "/media/$FILENAME"
sudo mount -o loop "$DIRNAME/$FILENAME" "/media/$FILENAME"

```
in a file in ~/.gnome2/nautilus-scripts call it somthing like "Mount iso" make it executable then just right click on an iso and select Scripts->Mount iso and roberts your mothers brother!

Thats pretty sweet thanks man.  Only problem, how to unmount?  It wont from nautilus because not root.

---

### Post by Zoot7 on 2009-11-12
From within Nautilus, my bad.

> **keypox said:**
> Thats pretty sweet thanks man.  Only problem, how to unmount?  It wont from nautilus because not root.

Here's the one I'm using:

```
#!/bin/bash
# unmount

gksudo -k /bin/echo "got r00t?"

BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS`

sudo umount "/media/$BASENAME"

sudo rmdir "/media/$BASENAME"

zenity --info --text "Successfully unmounted /media/$BASENAME"

exit 0
```
Assuming it's mounted in a folder in /media just right click on that folder and use this script.

---

### Post by Keith Hedger on 2009-11-12
Same again but call this script:```
#!/bin/bash

FULLPATH=$(echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | sed 's/\n//g' )
foo=$(gksudo -u root -k -m "Enter Your Admin Password" /bin/echo "got r00t?")
sudo umount "$FULLPATH"
sudo rmdir "$FULLPATH"
``` "Eject Disk"
Right click on the mounted disk ( on the desktop ) select Scripts -> Eject Disk and off it will go!
P.S. I aint too happy about this script it's a bit of a klutz but seems to work!

---

### Post by stinkeye on 2009-11-12
In karmic there is a right click option "Open with Archive Mounter".

---

### Post by Keith Hedger on 2009-11-12
> **stinkeye said:**
> In karmic there is a right click option "Open with Archive Mounter".

Archive mounter is also in Jaunty but is hidden in one of the menus (other) I dragged it to the desktop and use it to mount archives I didn't know it would mount iso too, well spotted!

---

### Post by stinkeye on 2009-11-12
> **Keith Hedger said:**
> Archive mounter is also in Jaunty but is hidden in one of the menus (other) I dragged it to the desktop and use it to mount archives I didn't know it would mount iso too, well spotted!
Thanks, Can't take to much credit though.I'm just a linux noob who likes to listen Linux podcasts.
Picked this up on this weeks Going Linux podcast.

---

