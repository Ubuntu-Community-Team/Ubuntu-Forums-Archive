---
title: "Help with Bash Scripting. Script to shred files."
date: 2009-04-05
forum: General Help
---

### Post by miau1010 on 2009-04-05
I'm a begginer at bash scripting but manage to do simple scripts. The problem is, things for what there is a simple solution are still beyond me.

With my script I want to have GUI windows (for which I use zenity) for the interactive parts. This way, you confirm you want to shred the file, the script gives the shred command, and then checks if the files exist and informs in a GUI box if it was successful or not. I later put this on the context menu of nautilus with Nautilus Actions Configurator.

Here is the script:

```

#!/bin/bash
#################################################
#						#
#	Shred Script v0.1.3 Alpha.		#
#	 Shred (3 pass) version			#
#						#
#################################################

ans=$(zenity --title "Confirmation" --entry --text "Shred the file(s)? Type 'y' to confirm." --window-icon=warning); #Confirmation turned into a variable.

if [ "$ans" = "y" ] ; then
 shred -fuz -n 2 "$@" #Shred command. Two passes plus a zeroing pass.
else
 zenity --info --title="Error" --text="Incorrect confirmation. Files NOT shreded." --window-icon=warning #Confirmation failure message.
 rm ./0 #Removing strange 0 file that appears in home folder for no reason.
 exit 1
fi

#Checking if files are really gone. In construction.

while [ ! "pgrep shred" > "0" ] ; do #Checks if shred process exists every second.
sleep 1
done

sleep 1 #Waits a second so as to give time for the filesystem to recognize the deletion of the files (?).

while [ ! -e "$1" ] ; do
  if [ ! -e "$2" ] ; then
    zenity --info --title="Sucess" --text="All files shreded (High probability guess)." #Success message.
    rm ./0
    exit 0
  fi
shift
done

zenity --info --title="Error" --text="Unknown error: Not all files shreded." --window-icon=warning #Failure message.
rm ./0
exit 2

```

And the problems I have are:
-I need to delete the backup files that end with ~ for the files being shredded. Doing shred (options) $@~ only shreds the backup file of the last file being shreded, if it's more than one.

-A better way to check if the files don't exist after the shredding. My current way is convoluted and won't work if the first two files are gone but the other remain. (That's why I put that it's only a high probability guess).


Any help with either (or both) problems would be greatly appreciated. And getting it to work properly would be great for any other users concerned about deleting securely their files from the convenience of the context menu ;)

---

### Post by miau1010 on 2009-04-06
Bump. Come on, some of you must know about bash scripting.

---

