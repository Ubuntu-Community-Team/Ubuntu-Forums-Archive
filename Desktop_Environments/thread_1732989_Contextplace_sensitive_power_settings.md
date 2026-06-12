---
title: "Context/place sensitive power settings"
date: 2011-04-18
forum: Desktop Environments
---

### Post by dacovale on 2011-04-18
I want to have my setting adapt themselves depending on where I am at the moment. I use this laptop mainly at two locations, my university, where I want it to have really strict power setting (lights out after 30 seconds inactive, pw to enable screen, etc) and my home, where I want more lax settings.

I've been trying to find some script/program/applet/anything that does this, but... I would really benefit from a crash course in searching the web. I've found absolutely nothing, but I can't be the first who've had this idea.

So, does something like this exist already? Some daemon that changes the relevant settings depending on for example which network I'm logged on to?

If not, is there somewhere I can inject a script somewhere that checks what network I'm connecting to? And if so, where can I read up on the necessary commands to change the settings I want?

---

### Post by deconstrained on 2011-04-19
A feature that's been a part of GNU/Linux power managers for years (and in Windows/Mac too, for that matter) is to have separate settings for when it's connected to a power adapter and when it's running on battery power. Most of what you describe can be done using that functionality. I don't know about disabling the screen lock when on wall power, however.

---

### Post by Copper Bezel on 2011-04-19
Well, that wouldn't really solve it. He might not always be on AC at home. What he needs is separate, easily selectable power *profiles*. Ubuntu doesn't really have those.

---

### Post by dacovale on 2011-04-19
I usually have the power cord with me to the uni as well. So no, that wouldn't work, not in either direction. :)

How about my second part of the query?

Where can I find the correct commands / arguments for changing these settings from the terminal? If I knew those, I could set up a script to run when I switched location. As long as I got it all in a one-click script, I wouldn't even need it to be automatic.

---

### Post by Copper Bezel on 2011-04-19
I've made, like, 80 edits to this. It's becoming compulsive, but I made it go. = D

```
#!/bin/bash
powerprofile=`cat ~/.power-profile.txt`
	if [ "$powerprofile" = "home" ];
	then
	gconftool-2 --type integer --set /apps/gnome-power-manager/timeout/sleep_display_ac "60"; 
	gconftool-2 --type integer --set /apps/gnome-power-manager/timeout/sleep_display_battery "60";
	notify-send "Power Manager" "School Settings Enabled" -i gpm-ac-adapter &
	echo "school" > ~/.power-profile.txt
	else
	gconftool-2 --type integer --set /apps/gnome-power-manager/timeout/sleep_display_ac "600"; 
	gconftool-2 --type integer --set /apps/gnome-power-manager/timeout/sleep_display_battery "600";
	notify-send "Power Manager" "Home Settings Enabled" -i gpm-ac-adapter &
	echo "home" > ~/.power-profile.txt
	fi;
```

It's a toggle script that notifies you of the change through notify-osd, uses gconftool-2 to change the settings, and can only set values to possible settings within Gnome Power Manager (so no 15 seconds for anything.) Needs to be in the home folder as .power-profile.sh, executable, accompanied by a blank document named .power-profile.txt, non-executable. 

To add other settings modifications, look them up in gconf-editor under apps/gnome-power-manager. Notice that values in gconf-editor may be typed as integer, boolean, or string and need to be set accordingly as above, which was the last irritating little snag in making this work. = )

Edit: One last - thanks for this. I'm going to use it to turn my screen lock on and off. = )

---

### Post by dacovale on 2011-04-19
Thanks!

This works great. After going through the gconf-editor I found every setting I needed :)

---

### Post by Copper Bezel on 2011-04-19
Excellent. I'm glad it worked out! = )

---

