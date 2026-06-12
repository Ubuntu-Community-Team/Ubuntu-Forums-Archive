---
title: "Nvidia video reset"
date: 2013-01-28
forum: Desktop Environments
---

### Post by francoeurdavid on 2013-01-28
I'm trying to write a quick script here that will switch the current xorg.conf by the configuration file of the set up I want. It will go from, my computer only, to my TV only and then both at the same time.

Everything is looking good so far except for one thing, how do I get to load the new config and then apply it without restarting the X server.

I want to do just like the "Apply" button in the nvidia-settings page that does a video "reset" and then show up with the new settings.

Currently my script make a backup, ask for the wanted setup and the copy the configuration of the chosen setup over the current.

I've also read that nvidia-xconfig --xconfig=CONFIG_FILE is doing a good job at this, but it is not applying the change right away.

I've also heard of xrandr, but I don't understand how to make it work as I want it!

Thanks, David

---

### Post by francoeurdavid on 2013-01-29
After I found that it was xrandr, and not xandr, I was able to see how to make it work :

Here is what my script look like :

```

#! /bin/bash
clear

echo "Ensure the HDMI is plugged."

echo "1 - Computer display only."
echo "2 - Computer and TV display."
echo "3 - TV only."

read choice
if [ $choice -eq 1 ]
then
	# computer only
	xrandr --output LVDS-0 --mode 1280x800 --output HDMI-0 --off	
elif [ $choice -eq 2 ]
then
	# both
	xrandr --output LVDS-0 --mode 1280x800 --output HDMI-0 --mode 1280x720
elif [ $choice -eq 3 ]
then
	# tv only
	 xrandr --output LVDS-0 --off --output HDMI-0 --mode 1280x720
else
	echo "Wrong option."
	exit 1
fi


```


And here's the raw output of xrandr as my HDMI is plugged in : 

```

Screen 0: minimum 8 x 8, current 1280 x 800, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
TV-0 disconnected (normal left inverted right x axis y axis)
LVDS-0 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       63.2*+
HDMI-0 connected (normal left inverted right x axis y axis)
   1920x1080      60.0 +   59.9     24.0     30.0     30.0  
   1440x480       30.0  
   1280x720       60.0     59.9  
   720x480        59.9     30.0  
   640x480        59.9  

```

Feel free to use the code for whatever.

---

