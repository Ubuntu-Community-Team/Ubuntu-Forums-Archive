---
title: "Terminal on Right Click"
date: 2005-10-26
forum: Desktop Environments
---

### Post by breen92uk on 2005-10-26
I have recently upgraded to Breezy from Hoary, and am generally pleased with the improvements. There is one thing that really annoys me though - the fact that the 'Terminal' launcher has been removed from the right click menu. Is there anyway this can be re-enabled?

---

### Post by Biker on 2005-10-26
Put this script in ~/.gnome2/nautilus-scripts and don't forget to make it executable (chmod 755) and give the script the name "Xterm here". Of course you can call the gnome-terminal too in the last line.


#!/bin/sh
# Original by two other scripts merged together
# Modified by Eugenia Loli and Kon, Oct 2004
# This script either opens in the current directory, 
# or in the selected directory
# Doesn't work with the ~/Desktop or the ~/.Trash folders (Nautilus' limitation).

base="`echo $NAUTILUS_SCRIPT_CURRENT_URI | cut -d'/' -f3- | sed 's/%20/ /g'`"

if [ -z "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" ]; then
     dir="$base"
else 
     while [ ! -z "$1" -a ! -d "$base/$1" ]; do shift; done
     dir="$base/$1"
fi

if [ "$NAUTILUS_SCRIPT_CURRENT_URI" == "x-nautilus-desktop:///" ]; then
dir="Desktop"
fi

if [ "$NAUTILUS_SCRIPT_CURRENT_URI" == "trash:" ]; then
dir="$HOME/.Trash"
fi

if [ "$NAUTILUS_SCRIPT_CURRENT_URI" == "file:///" ]; then
dir="/"
fi

FIRST_URI="`echo -n $NAUTILUS_SCRIPT_SELECTED_URIS`"

if [ "$FIRST_URI" == "x-nautilus-desktop:///home" ]; then
dir="$HOME"
fi

if [ "$FIRST_URI" != "" ]; then
dir="`echo $FIRST_URI | cut -c8-`"
fi

if [ "$FIRST_URI" == "x-nautilus-desktop:///computer" ]; then
dir="/"
fi 

# uncomment this if you want to use the Gnome Terminal instead of XTerm
#gnome-terminal --working-directory="$dir"

cd $dir
#exec xterm -bg black -fg green -cr red -sl 3000 -g 100x76+1+1 -T `pwd`
exec aterm +sb --title `pwd`

---

### Post by breen92uk on 2005-10-26
It doesn't seem to work: a sub-menu appears with 'Xterm here' in it, but that does nothing.

---

### Post by Dr. Nick on 2005-10-26
Just install the package "nautilus-open-terminal" and it will put a launcher on the right click menu

---

### Post by Leigh on 2005-10-26
Dr. Nick is right, but you may need to enable the extra repositories before trying his  suggestion, otherwise you'll get the "*Couldn't find package nautilus-open-terminal.*" error message. Also, you'll have to log off and log in again to see "Open Terminal" in the right-click menu.

---

### Post by breen92uk on 2005-10-26
[QUOTE=Dr. Nick]Just install the package "nautilus-open-terminal" and it will put a launcher on the right click menu[/QUOTE]
That works - cheers.

---

### Post by Dr. Nick on 2005-10-26
[QUOTE=breen92uk]That works - cheers.[/QUOTE]

Cool
[QUOTE=leigh]

Dr. Nick is right, but you may need to enable the extra repositories before trying his suggestion, otherwise you'll get the "Couldn't find package nautilus-open-terminal." error message. Also, you'll have to log off and log in again to see "Open Terminal" in the right-click menu.[/QUOTE]

Thanks for catching that, Its been awhile since Ive installed fresh so I forget sometimes about having to enable the extra repos.

---

### Post by Leigh on 2005-10-26
[QUOTE=Dr. Nick]Thanks for catching that, Its been awhile since Ive installed fresh so I forget sometimes about having to enable the extra repos.[/QUOTE]

The only reason I know is because I got out with it.  Thank goodness for these forums!

---

### Post by Biker on 2005-10-27
[QUOTE=breen92uk]It doesn't seem to work: a sub-menu appears with 'Xterm here' in it, but that does nothing.[/QUOTE]

Do you have made the file 'Xterm here" executable?

sudo chmod 755 ~/.gnome2/nautilus-scripts/Xterm\ Here

---

### Post by GTvulse on 2005-10-27
If you look at the last two lines, you'll notice that it execs aterm, a terminal emulator that is not installed by default (it is in Universe). The commented line does load xterm and works out-of-the-box, but you may want to customize it to your own personal tastes. Read the xterm manual: Menu System/Help, select Manual Pages/Applications/xterm. You can bookmark it to come back to is easier in the future.

EDIT. Forgot to thank Biker for the script... :-)

---

