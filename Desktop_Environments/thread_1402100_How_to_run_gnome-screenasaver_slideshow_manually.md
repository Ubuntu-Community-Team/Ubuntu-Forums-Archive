---
title: "How to run gnome-screenasaver slideshow manually"
date: 2010-02-08
forum: Desktop Environments
---

### Post by raghu1111 on 2010-02-08
What I am trying to achieve:

I have selected photo slide show as the screensaver and normally it activates after 5min of inactivity and 'power saving' turns off monitor after 15min.

Occasionally I would like to run the same slideshow for one hour without interruption by the gnome-screen saver. (Ideally in a script so that it could be launched with one click).

One way to do this would be :```

#!/bin/bash
#disable screen saver temporarily
gnome-scrensaver-command -i &
PID=`jobs -p`

#find the right args for gnome-screensaver slideshow
/usr/lib/gnome-screensaver/gnome-sreensaver/slideshow

# or run some other slideshow

sleep 3600
kill $PID

```

Two questions with the above approach :
1. How can we start "/usr/lib/gnome-screensaver/gnome-sreensaver/slideshow" same way that gnome-screensaver would? 
2. will 'gnome-screensaver-command -i' command also prevent power management from turning off the monitor?

---

### Post by raghu1111 on 2010-02-23
The following script does pretty much exactly what I need.

It requires 'xte' and 'xprintidle'. It uses glslideshow for slideshow. Search this forum for how to configure photo directory for it. This is a much better slideshow than the default in gnome-screensaver. The script does the following :
[LIST]
[*] disable gnome-screen-saver and store the pid.
[*] obtain "window-id" for the desktop background using xwininfo.
[*] move cursor to right bottom corner (so that it does not appear over the photos.
[*] wait for 30 minutes before stopping the slideshow.
[*] there is no easy way for the user to kill the slideshow. So watch for any user activity during this time.
[/LIST]
```

#!/bin/bash

#disable screen saver while running slideshow
gnome-screensaver-command -r "slideshow" -i &
PID=`jobs -p`

#get the window id
WID=`xwininfo -name x-nautilus-desktop | grep 'Window id:' | awk '{print $4}'`

#move the mouse to bottom right corner
WIDTH=`xwininfo -id $WID | grep Width: | awk '{print $2}'`
HEIGHT=`xwininfo -id $WID | grep Height: | awk '{print $2}'`
xte 'mousemove $WIDTH $HEIGHT'

/usr/lib/xscreensaver/glslideshow -fade 5 -pan 12 -duration 12 -window-id $WID &
SLIDESHOW=`jobs -p`

ENDTIME=`expr \`date +%s\` + 1800`
sleep 2

#wait for any input on the screen to end the slideshow

while [ `date +%s` -lt $ENDTIME ] && [ `xprintidle` -gt 1000 ]; do
    sleep 0.2
done

kill $SLIDESHOW
kill $PID

```

---

