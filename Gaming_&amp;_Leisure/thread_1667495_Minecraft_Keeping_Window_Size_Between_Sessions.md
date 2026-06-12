---
title: "Minecraft: Keeping Window Size Between Sessions"
date: 2011-01-14
forum: Gaming &amp; Leisure
---

### Post by mattcan on 2011-01-14
Here's a small bash script I am using to keep my Minecraft window the same size between sessions. I came up with this because I wanted to start auto-recording when I played (working on a large project) so I figured there had to be a way to make the window open up the same every time. Here is the solution..

First, install a couple tools. *xwininfo* is probably installed.
```

sudo apt-get install xwininfo xdotool

```Now copy the following bash script into a text editor
```

#!/bin/bash

WINWIDTH=
WINHEIGHT=
JARPATH=
WID=0

java -Xmx1024M -Xms512M -cp $JARPATH net.minecraft.LauncherFrame &

for I in `seq 20` ; do    
   
   if [ "`xwininfo -name "Minecraft Launcher" | grep 'IsViewable'`" != '' ] ; then
      WID=`xwininfo -name "Minecraft Launcher" -int | awk '/Window id:/ {print $4}'`
      echo $WID
      break
   fi
done

if [ $WID > 0 ] ; then
    #xdotool windowmove --sync $WID 0 0
    xdotool windowsize --sync $WID $WINWIDTH $WINHEIGHT
fi

```Next change **JARPATH**, **WINWIDTH**, and **WINHEIGHT**. I think these are self explanatory. Save the script as whatever you want, I used the uncreative name *mc-opener*, and than move to the directory where it is saved, using either the terminal or file browser.

In the file browser you can right-click, hit Properties, and set the file as executable.
In the terminal..
```
chmod +x mc-opener
```Now you have a working script! Hook it up to a launcher or run it from the terminal.

**Customizing**
-Uncommenting *xdotool windowmove --sync $WID 0 0* will help you to move the window to a better position.
-Launching Minecraft by itself and than launching *xwininfo* in a terminal will help you to get details about the window. Just resize and move the window and than use *xwininfo* to get the details to dump into the script.

**Have fun and let me know if there are any problems or if you have a better way!**

**Notes**
-I also posted this at the Minecraft forums but it sank like a rock so I'm cross posting here. :) Original link: [http://www.minecraftforum.net/viewtopic.php?f=1020&t=138075](http://www.minecraftforum.net/viewtopic.php?f=1020&t=138075)
-This tool actually works for alot of programs, just change the program that is being launched and it should all play well

---

### Post by Dr_Frost on 2011-04-17
just added a small thing since my minecraft doesn't startup instantaneous

```

#!/bin/bash

WINWIDTH=1000
WINHEIGHT=600
JARPATH=/home/frost/Desktop/Linux/minecraft.jar
WID=0

java -Xmx1408M -Xms1408M -cp $JARPATH net.minecraft.LauncherFrame &

for I in `seq 3` ; do    
   sleep 1
   if [ "`xwininfo -name "Minecraft Launcher" | grep 'IsViewable'`" != '' ] ; then
      WID=`xwininfo -name "Minecraft Launcher" -int | awk '/Window id:/ {print $4}'`
      echo $WID
      break
   fi
done

if [ $WID > 0 ] ; then
    #xdotool windowmove --sync $WID 0 0
    xdotool windowsize --sync $WID $WINWIDTH $WINHEIGHT
fi

```added the sleep 1 and seq 3 = wait 1 second x 3 times to see  if minecraft has started
now it works, it didn't work before it just rand all 20 times before minecraft window had popped out

But good work on this script, i was getting tiered of resizing the window every time i started minecraft.

---

### Post by keltic dave on 2011-05-09
edit: 

works now facepalm

---

