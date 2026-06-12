---
title: "Random background script help"
date: 2009-09-10
forum: Desktop Environments
---

### Post by Spongeloaf on 2009-09-10
I found a simple and helpful script online (I'm sorry, but i forget who wrote it. You know you're awesome.) to randomly choose a background at login. This is all well and good, except for when I run two screens, at which point the background image gets stretched across both monitors. The backgrounds all vary in size, so setting them to tiled doesn't work. I found one really _[COLOR=Blue][awesome]("http://www.gnome-look.org/content/show.php/Trinity?content=81727")[/COLOR]_ image I'd like to use that spans both screens, but I'm lazy, and I dont like having to manually set it each time I boot dual screen. 

So, does anyone have the courage/fortitude/awesomeness to give me pointers in modifying the script? (posted at bottom) I simply want to add a few llines like this:

```

if 

second monitor = enabled

then 

set background trinity.jpg

else

carry out the script as normal
```I have only limited understanding of shell script, and if anyone knows how to get the status of the second monitor from X server, that would be very helpful. I'm running 9.04, desktop edition.

Here is the script:
```

#!/bin/bash
WALLPAPERS=/home/spongeloaf/Desktop/Stuff/desktopbgs

# find the identity of the current wallpaper...
# get the name...
THISONE=`gconftool-2 -g /desktop/gnome/background/picture_filename`

# Chop off the path
THISONE=${THISONE##*/}

# locate the filename by index in this directory
THISONE=`ls -1 $WALLPAPERS | grep -n $THISONE`

# make the grep string into a valid number
THISONE=0${THISONE%%:*}

# get a directory list
ALIST=( `ls -1 $WALLPAPERS` )

# get the number of lines in that list
RANGE=${#ALIST[@]}

# programmers trick to make a 'while' loop that runs at least once...
lastnum=1
number=1

while [[ "$lastnum" -eq "$number" ]]; do
# Now randomize until we have a new number that is not the same as the old one...
    let lastnum=$THISONE
    let "number = $RANDOM + $lastnum"
    let "number = $number % $RANGE"
done

# Set wallpaper to selection indexed by new "number"
gconftool-2 -t string -s /desktop/gnome/background/picture_filename $WALLPAPERS/${ALIST[$number]}
```Thanks.

---

