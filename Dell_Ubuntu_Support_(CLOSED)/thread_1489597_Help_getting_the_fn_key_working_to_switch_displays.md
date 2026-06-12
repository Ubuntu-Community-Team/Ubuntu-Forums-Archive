---
title: "Help getting the fn key working to switch displays"
date: 2010-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Rackstar on 2010-05-21
Hi,

The title says it all! I need help getting the fn key working to swith displays. On my Dell Studio 1558 this is FN-F1. And the shortcut name is Mod4 - P .

I have an ATI HD5470.

Any ideas?

---

### Post by Rackstar on 2010-05-21
Hi,

I made a workaround for this problem, with some help of the thread [http://ubuntuforums.org/showthread.php?t=965861&highlight=crt+lcd](http://ubuntuforums.org/showthread.php?t=965861&highlight=crt+lcd) by johnylwo. (Thanks!)

[B]1) First create the script. Mine is located at /home/ruben/Scripts/toggleDisplay.sh.
[/B]

```
#!/bin/bash
# Script to toggle display configuration on Dell Studio 1558
# author: Ruben Verhack

config="/tmp/display.conf"
current=`cat $config`

# Check if config exists
if [ ! -a $config ]
then
	# Empty file executes default
	touch $config;
fi

# Check if CRT2 is connected
if xrandr -q | grep "CRT2 connected"
then
	# Toggle between states
	case "$current" in
	  '')
		# default
        	xrandr --output LVDS --auto --output CRT2 --left-of LVDS --output CRT2 --auto
		echo "dual" > $config
		;;
	  'dual')
		# was dual, now external only
        	xrandr --output LVDS --off --output CRT2 --auto
		echo "external" > $config
		;;
	  'external')
		# was external, now laptop only
        	xrandr --output LVDS --auto --output CRT2 --off
		echo "laptop" > $config
		;;
	  'laptop')
		# was laptop, now both
        	xrandr --output LVDS --auto --output CRT2 --left-of LVDS --output CRT2 --auto
		echo "dual" > $config
		;;
	esac
else
	xrandr --output LVDS --auto
fi
```

Note that my displays are named LVDS and CRT2. I think LVDS is default for laptop displays, though CRT2 can differ. It is possible to check what the names are for your displays by executing "xrandr -q".

**2) Edit your gnome shortcuts using the tool: Preferences -> Shortcuts**

See screenshot for this.

Hope this helps someone!

Posted a little longer version on my BLOG: [http://ninetynine.be/blog/2010/05/quick-workaround-for-missing-switch-display-key-or-lcdcrt-key-on-ubuntu/](http://ninetynine.be/blog/2010/05/quick-workaround-for-missing-switch-display-key-or-lcdcrt-key-on-ubuntu/)

---

