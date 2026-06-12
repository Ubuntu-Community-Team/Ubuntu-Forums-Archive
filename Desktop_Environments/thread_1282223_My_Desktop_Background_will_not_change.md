---
title: "My Desktop Background will not change"
date: 2009-10-04
forum: Desktop Environments
---

### Post by HomoGleek on 2009-10-04
Hi. 

My desktop background no longer changes :confused: Ive tried all the ways I know too change it with no luck.

Yesterday I used this script for a random wallpaper

```

#! /bin/bash
cd ~/Pictures/desktop
#the rest of a line of text starting with the "#" symbol is a "comment," meaning that it isn't part of the code
#it's just there so you can leave remarks in the code so people can understand your code better
set -- *  #tell whatever the next command is, that we should use the list of all files as the data to process
length=$#  #get the length of whatever we're working with (in this case, the list of all files in the current directory)
random_num=$(( $RANDOM % ($length + 1) ))   #Generate a random number between 0 and [number of files in the current directory]
FILE_NAME=${!random_num}   #whatever the random number is, get that file. So if the random number was 5, get the 5th file
FILE_NAME=$PWD"/"$FILE_NAME   #add the current directory's name to the beginning of the filename 
#($PWD gets substituted for the name of the current directory.) Don't forget to add the slash too!
#now instead of, say, mountains.jpg, it is /home/whatever_your_username_is/Pictures/desktops/mountains.jpg
#the gconf command will need the full path name in order to work.
gconftool-2 -t string -s /desktop/gnome/background/picture_filename $FILE_NAME
sleep 60 #pause for 240 seconds
cd - #go back to the directory we were previously in, which in this case will be where the script is.
#that way the script can run itself
/bin/bash $0    # $0 gets substituted for the filename of the currently-running script, 
#so in this case it after the 240 seconds, this program would run itself again from the beginning.

```

But I don't want a random wallpaper (this hasn't been used since yesterday, I didn't run on boot up today)

---

### Post by underyourskin on 2009-10-04
Start your configuration editor (gconf). Expand the 'desktop' tree, then 'gnome' and click on 'background'. In the right window you shoud see an option 'Draw Background'. Make sure the box is checked. if not do so. Restart your window manager or Log out and in again.

---

### Post by HomoGleek on 2009-10-04
> **underyourskin said:**
> Start your configuration editor (gconf). Expand the 'desktop' tree, then 'gnome' and click on 'background'. In the right window you shoud see an option 'Draw Background'. Make sure the box is checked. if not do so. Restart your window manager or Log out and in again.
Thanks, but it seemed too sort itself out when I restarted. Strange.

---

