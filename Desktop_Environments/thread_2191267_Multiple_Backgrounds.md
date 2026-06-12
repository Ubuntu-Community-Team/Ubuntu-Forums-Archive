---
title: "Multiple Backgrounds"
date: 2013-12-01
forum: Desktop Environments
---

### Post by itannerjh on 2013-12-01
Hey everyone! I'm relatively new on Xubuntu, and I am experimenting on different layouts for my monitor, namely vertical, and horizontal. I have found that I like using both for different things. When I am watching movies, or videos, I like horizontal, but when I am typing a paper for school, I like to use vertical, because it gives me a better view of the page. Is there any way to make it so that whenever I switch layouts, the wallpaper will change?

Thanks a ton

---

### Post by Toz on 2013-12-02
Hello and welcome to the forums.

This isn't possible using the configuration options within Xfce, but you can use a script to accomplish this. Here is one:
```
#!/bin/bash

#defaults
VERTICAL=90				#0=normal, 90=left, 180=inverted, 270=right
HORIZONTAL=0				#0=normal, 90=left, 180=inverted, 270=right
OUTPUT=LVDS1				#from xrandr -q | grep " connected"
VERTICAL_WALL="/home/toz/Pictures/View.jpg"
HORIZONTAL_WALL="/home/toz/Pictures/Galaxy.jpg"

###  DON'T CHANGE ANYTHING BELOW  #######################################

case $VERTICAL in 
	0) XVERTICAL=normal;;
	90) XVERTICAL=left;;
	180) XVERTICAL=inverted;;
	270) XVERTICAL=right;;
	*) XVERTICAL=null;;
esac
case $HORIZONTAL in 
	0) XHORIZONTAL=normal;;
	90) XHORIZONTAL=left;;
	180) XHORIZONTAL=inverted;;
	270) XHORIZONTAL=right;;
	*) XHORIZONTAL=null;;
esac

#get the current rotation
CURRENT=$(xfconf-query -c displays -p /Default/$OUTPUT/Rotation)

if [ "$CURRENT" -eq "$HORIZONTAL" ];
then
	xrandr --output $OUTPUT --rotation $XVERTICAL
	xfconf-query -c xfce4-desktop -p /backdrop/screen0/monitor0/image-path --create -t string -s "$VERTICAL_WALL"
else
	xrandr --output $OUTPUT --rotation $XHORIZONTAL
	xfconf-query -c xfce4-desktop -p /backdrop/screen0/monitor0/image-path --create -t string -s "$HORIZONTAL_WALL"
fi
```

To use:
[LIST=1]
[*]Copy and paste this into a new file called "rotater" in your home directory.
[*]Change the options in the "#defaults" section to suit:
- **VERTICAL** rotation value - one of the 4 following values: 0=normal, 90=left, 180=inverted, 270=right
- **HORIZONTAL** rotation value - one of the 4 following values: 0=normal, 90=left, 180=inverted, 270=right
- **OUTPUT** - the screen being output to - can be obtained by running the following command: **xrandr -q | grep " connected"**
- **VERTICAL_WALL** - the path and name to the wallpaper you want to use when the screen is in vertical orientation
- **HORIZONTAL_WALL** - the path and name to the wallpaper you want to use when the screen is in horizontal orientation
[*]Save the file.
[*]Make the file executable. From a command line:
```
chmod +x ~/rotater
```
[*] Test it from the command line by running the following command in a terminal window:
```
~/rotater
```
...since it is a toggle script (it will toggle between the two orientations and change the wallpaper), running the script repeatedly should toggle between the two orientations.
[*]And since this is a toggle script it will work best if attached to a keyboard shortcut. Go to Settings Manager -> Keyboard -> Application Shortcuts and create a new shortcut (for the command, make sure you enter the full path to the command - "/home/USER/rotater" - where USER is your username). 
[*]
[/LIST]

---

