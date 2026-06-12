---
title: "[SOLVED] Context menu script question"
date: 2007-12-22
forum: Desktop Environments
---

### Post by quandary on 2007-12-22
Hi!

I want to be able to mount cd-images from the context menu.

From what I understand, I have to place a script in: "/root/.gnome2/nautilus-scripts/"
I called it: "Mount ISO Image"

Then i create a mount folder:
mkdir /media/iso

"Mount ISO Image" 's content is:
```

#!/bin/sh
mount ~/Desktop/wikipedia.iso /media/iso -o loop;
exit;

```

then i do: chmod +x "Mount ISO Image"

and now i can mount this image by right-clicking on a file on the desktop, selecting scripts and click on mount iso image.

Now my question:
When i select my script from the context menu, how can i get the filename (and path) of the selected icon/file in the script?
I suppose nautilus passes the name and path as some arguments? Or Not?

Additionally, is it possible to make a seperate context menu entry (=not in scripts) like the extract here for b2z files, which also shows up only if the file is of a specified type?

---

### Post by PeterJS on 2007-12-22
Take a look at zenity.

```

#!/bin/bash
mount `zenity --title "Select ISO" --file-selection` /media/iso -o loop;
exit;

```

---

### Post by quandary on 2007-12-22
Oh, zenity remembers me of the VB dialog boxes ,-)

Thanks so far. That works.

But is there no direct way, getting the filename directly, without having to select it again?

---

### Post by PeterJS on 2007-12-22
You could save the the last used file in a predictable location, and then reload it at the start of the script. It's getting better but still not right, see the commented section in the middle.

```

#!/bin/bash

LOCATION_FILE="$HOME/.last_iso"

if [ -f "$LOCATION_FILE" ]
then
LASTLOC=`cat $LOCATION_FILE`
LASTDIR=`dirname $LASTLOC`
LASTFILE=`basename $LASTLOC`
#Debug messages, remove as you see fit.
#echo $LASTDIR
#echo $LASTFILE
cd $LASTDIR
#The commented out line seems like it should work based on the man pages, but just generates an error :(
#FILENAME=`zenity --title "Select ISO" --filename "$LASTFILE" --file-selection`
FILENAME=`zenity --title "Select ISO" --file-selection`
else
FILENAME=`zenity --title "Select ISO" --file-selection`
fi

zenity --info --title "Debug" --text "$FILENAME"

echo $FILENAME > "$LOCATION_FILE"

```

---

### Post by dandandan on 2007-12-23
> **quandary said:**
> 

Additionally, is it possible to make a seperate context menu entry (=not in scripts) like the extract here for b2z files, which also shows up only if the file is of a specified type?

sudo apt-.get install nautilus-actions
then run nautilus-actions-config and make your own nautilus action which is then directly shown in the context menu, you can specify mime-types there for example, on which selection the action shows.

---

### Post by quandary on 2007-12-25
Thanks for the last tip.
OK i got it like i wanted it now.
I've attached the script and the nautilus-actions-config for ISO-CD in the zip file.

nautilus-actions-config action-parameter is %M
The script must look like this:
```

#!/bin/bash

filename=""
ArgumentIndex=0
for ARG in $*
do

	if [ "$ArgumentIndex" = "0" ]
		then
			filename="$ARG"
		else
			filename="$filename $ARG"
	fi
	       
	ArgumentIndex=$(($ArgumentIndex+1))
done

mount "$filename" /media/iso -o loop
exit;

```

Still one tiny question left:
When i go to nautilus-actions-config, open to the tab "conditions" and there select:
- for filetypes: *
- for Mimetypes: application/x-iso

then the context menu for my ISO image disappears from nautilus.

I therefore have to set:
- for filetypes: *.iso
- for Mimetypes: */*

and the context menu for my ISO image appears.

Why that? Is my ISO image not an ISO image, or is "application/x-iso" the wrong mime for ISO CD images?

---

### Post by quandary on 2007-12-25
OK, problem solved myself.

There exists no mime for ISO itselfs.

Instead you have to take the general CD image mime, which anyway is better in my case, because that way i can mount any cd-image.

MIME-type is:
"application/x-cd-image"

I found it by searching the folder
/usr/share/mime

for a name containing "CD".


which returns amongst others:
/usr/share/mime/application/x-cd-image.xml

---

### Post by smekis on 2008-07-08
That's what I needed, tnx!

But I have two follow up questions:

1. What do I put in fstab to make me not have to be root to mount (or umount) an iso to /media/iso ?

2. Is there a way to make the name of the mounted "drive" the name of the imaged disc? I just get "iso" in my places when i mount a disc.

---

