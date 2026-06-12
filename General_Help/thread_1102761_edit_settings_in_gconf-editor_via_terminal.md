---
title: "edit settings in gconf-editor via terminal?"
date: 2009-03-22
forum: General Help
---

### Post by spacesearcher on 2009-03-22
I would like to be able to edit specific settings in the gconf-editor via the terminal I can open to a specific folder but I can't figure out a way to edit these values. is it possible to edit the values through terminal?

---

### Post by Nxion on 2009-03-22
That depends, what is it you are wanting to edit exactly?

---

### Post by sdennie on 2009-03-22
You should be able to use gconftool-2.  Here are some examples that involve compiz:

```

gconftool-2 --type float --set /apps/compiz/plugins/expo/allscreens/options/zoom_time 1.3

gconftool-2 --type bool --set /apps/compiz/plugins/wall/allscreens/options/show_switcher 0

gconftool-2 --type int --set /apps/compiz/plugins/animation/screen0/options/time_step 15

```

---

### Post by spacesearcher on 2009-03-22
thank you! I can get it working in my terminal to do things like turn on and off cube gears in compiz and things like that. But would you know how to do it from a script that runs as root? Like I am taking using what i know from this [http://ubuntuforums.org/showpost.php?p=5031046&postcount=3](http://ubuntuforums.org/showpost.php?p=5031046&postcount=3)
so that any time I am on battery certain things get turned off and when I am on AC certain things get turned back on. There is this bug report: [https://bugs.launchpad.net/gconf/+bug/290647](https://bugs.launchpad.net/gconf/+bug/290647) that describes what seems to be the same problem. There is a workaround listed there but it isn't working and idk why my script looks like this: 

```
#!/bin/bash
if on_ac_power; then

  # on AC so don't do any head parking

  hdparm -B 254 /dev/sda # you might need 255 or a different value

ON_USER=$(cat /etc/passwd | grep :1000: | cut -d ':' -f 1)
export DBUS_SESSION=$(grep -v "^#" /home/$ON_USER/.dbus/session-bus/`cat /var/lib/dbus/machine-id`-0)

   gconftool-2 --type=list --list-type=string -s  /apps/compiz/general/allscreens/options/active_plugins [core,neg,extrawm,resize,svg,vpswitch,water,firepaint,imgjpeg,workarounds,mousepoll,session,video,png,regex,dbus,place,text,decoration,resizeinfo,shift,animation,thumbnail,wobbly,obs,animationaddon,fade,cube,showmouse,rotate,scale,move,3d,cubeaddon,expo,scalefilter,scaleaddon,ezoom,switcher,gears]

sudo -u $ON_USER $DBUS_SESSION gconftool-2 --type=list --list-type=string -s  /apps/compiz/general/allscreens/options/active_plugins [core,neg,extrawm,resize,svg,vpswitch,water,firepaint,imgjpeg,workarounds,mousepoll,session,video,png,regex,dbus,place,text,decoration,resizeinfo,shift,animation,thumbnail,wobbly,obs,animationaddon,fade,cube,showmouse,rotate,scale,move,3d,cubeaddon,expo,scalefilter,scaleaddon,ezoom,switcher,gears]




else
  # either on battery or power status could not be determined
  # so quickly park the head to protect the disk
  
ON_USER=$(cat /etc/passwd | grep :1000: | cut -d ':' -f 1)
export DBUS_SESSION=$(grep -v "^#" /home/$ON_USER/.dbus/session-bus/`cat /var/lib/dbus/machine-id`-0)



  hdparm -B 128 /dev/sda

  gconftool-2 --type=list --list-type=string -s  /apps/compiz/general/allscreens/options/active_plugins [core,neg,extrawm,resize,svg,vpswitch,water,firepaint,imgjpeg,workarounds,mousepoll,session,video,png,regex,dbus,place,text,decoration,resizeinfo,shift,animation,thumbnail,wobbly,obs,animationaddon,fade,cube,showmouse,rotate,scale,move,3d,cubeaddon,expo,scalefilter,scaleaddon,ezoom,switcher]

sudo -u $ON_USER $DBUS_SESSION gconftool-2 --type=list --list-type=string -s  /apps/compiz/general/allscreens/options/active_plugins [core,neg,extrawm,resize,svg,vpswitch,water,firepaint,imgjpeg,workarounds,mousepoll,session,video,png,regex,dbus,place,text,decoration,resizeinfo,shift,animation,thumbnail,wobbly,obs,animationaddon,fade,cube,showmouse,rotate,scale,move,3d,cubeaddon,expo,scalefilter,scaleaddon,ezoom,switcher]



fi
```

---

### Post by sdennie on 2009-03-22
Interestingly enough, I actually copy/pasted from my scripts that do exactly what you are asking for but edited out the "su" parts for clarity.  Here is what you need in your case:

```

XUSER=your_username

DISPLAY=:0.0 su ${XUSER} -c "gconftool-2 --type boolean --set /apps/compiz/general/screen0/options/sync_to_vblank 0"

DISPLAY=:0.0 su ${XUSER} -c "gconftool-2 --type float --set /apps/compiz/plugins/wall/allscreens/options/slide_duration 0.1"

DISPLAY=:0.0 su ${XUSER} -c 'gconftool-2 --type float --set /apps/compiz/plugins/expo/allscreens/options/zoom_time 1.3'

DISPLAY=:0.0 su ${XUSER} -c "gconftool-2 --type bool --set /apps/compiz/plugins/wall/allscreens/options/show_switcher 0"

```

You might get a few ideas from this thread as well: [ HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773")

---

### Post by spacesearcher on 2009-03-22
So i changed my script to this and re installed it. it still doesn't work and it also doesn't work if I run a terminal session by doing sudo gnome-terminal and then running thee command. the gears aren't turning on or off however my hard drive advanced power setting does change. What am I doing wrong with my script?

```
#!/bin/bash

XUSER=joe

if on_ac_power; then



  # on AC so don't do any head parking

  hdparm -B 254 /dev/sda # you might need 255 or a different value

  DISPLAY=:0.0 su ${XUSER} -c "gconftool-2 --type=list --list-type=string -s  /apps/compiz/general/allscreens/options/active_plugins [core,neg,extrawm,resize,svg,vpswitch,water,firepaint,imgjpeg,workarounds,mousepoll,session,video,png,regex,dbus,place,text,decoration,resizeinfo,shift,animation,thumbnail,wobbly,obs,animationaddon,fade,cube,showmouse,rotate,scale,move,3d,cubeaddon,expo,scalefilter,scaleaddon,ezoom,switcher,gears]"


else
  # either on battery or power status could not be determined
  # so quickly park the head to protect the disk


  hdparm -B 128 /dev/sda

 DISPLAY=:0.0 su ${XUSER} -c "gconftool-2 --type=list --list-type=string -s  /apps/compiz/general/allscreens/options/active_plugins [core,neg,extrawm,resize,svg,vpswitch,water,firepaint,imgjpeg,workarounds,mousepoll,session,video,png,regex,dbus,place,text,decoration,resizeinfo,shift,animation,thumbnail,wobbly,obs,animationaddon,fade,cube,showmouse,rotate,scale,move,3d,cubeaddon,expo,scalefilter,scaleaddon,ezoom,switcher]"



fi
```

---

### Post by spacesearcher on 2009-03-22
I forgot to also mention that I am using intrepid which has gnome version 2.24

---

### Post by spacesearcher on 2009-03-23
So after awhilewith the most recent script I posted installed to:

 /etc/acpi/ac.d/99-hdd-ugly-fix.sh
 /etc/acpi/start.d/99-hdd-ugly-fix.sh 
/etc/acpi/resume.d/99-hdd-ugly-fix.sh 
/etc/acpi/battery.d/99-hdd-ugly-fix.sh 


 I have discovered that the script works correctly on start up but not when switching between battery and ac or when resuming from suspend. I still don't know how to fix it. it changes my hard drive advanced power management correctly for startup ac and battery but not resuming from suspend.

---

