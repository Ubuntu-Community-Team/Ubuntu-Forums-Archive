---
title: "Compiz on 14.04"
date: 2015-03-06
forum: Desktop Environments
---

### Post by egeezer on 2015-03-06
In Compiz there used to be an option under Wallpapers to use different wallpapers for each of the workspaces on the Cube.  The current Compiz version describes that same option (in the left panel of Utility > Wallpaper), but it seems to refer now to time-cycling rather than workspaces.  Is that part of the general decline in the number of supported features since Sam Spillsbury left as main developer, or is there something I missed in the installation and setup?
 

 I was delighted to find the Xfce offers the option of different wallpapers per workspace in the new 4.12 release, but that's a different window manager.  Now if they had just included The Cube...!

---

### Post by deadflowr on 2015-03-06
It works the exact same on 14.04 as it does on 12.04.
.
You add a wallpaper and that becomes wallpaper for workspace #1.
Add a second one and it becomes the wallpaper for workspace #2.
And so forth.
If you set the cycle option(which is default to off), then whichever wallpapers are set will toggle through each workspace.

So if you set four workspaces each with a different wallpaper, and then turn on cycle,
when the cycle starts, wallpaper for workspace #1 moves to the end (workspace #4) and wallpaper for workspace #2 moves into workspace #1. and so forth.

> or is there something I missed in the installation and setup?
maybe.

---

### Post by egeezer on 2015-03-06
Thank you, deadflowr!  You not only solved it, you did it with the fastest answer I've ever gotten to a fresh thread!

It worked, of course, just the way you said it would.  The word "cycle" was what had stopped me from even messing with it.  Cycling in spaces instead of time never occurred to me.  

Again, my thanks.

---

### Post by CantankRus on 2015-03-06
Hi egeezer,
you may also be interested in this script I use. It uses the wallpaper plugin of compiz.
It allows you to randomly choose **images from a directory** to use as wallpaper for compiz cube.
With a little bit of bash scripting knowledge can easily be used to run in a loop and run at timed interval or just put in startups as is to change at each login.
The script keeps desktop1 as the image set in Appearance and changes the other 3 desktops.
Can also be edited to change all 4 desktops.

_wallchanger-compiz-cube.sh_
```
#!/bin/bash
#set -x 
##############################################################################
## Enable the compiz wallpaper plugin and manually set 4 wallpapers in ccsm ##
## before running this script                                               ##
##############################################################################

directory="/home/glen/Pictures/wallpaper"   # set your wallpaper directory

find "$directory" -type f -iname '*.jpg' -or -iname '*.jpeg' -or -iname '*.png' | shuf -n 4 > ~/.4walls    # searches recursively

## use this to set a permanent image on desk1 to whatever you have selected in Appearances
## or to use with xplanetfx which alternates between ~/.xplanetFX/output/xplanetFX1.png and ~/.xplanetFX/output/xplanetFX2.png
desk1="$(dconf read /org/gnome/desktop/background/picture-uri | cut -c 9- | tr -d "'")"  # comment for random image
#desk1="$(awk 'NR==1' ~/.4walls)"  # uncomment for random image

desk2="$(awk 'NR==2' ~/.4walls)"
desk3="$(awk 'NR==3' ~/.4walls)"
desk4="$(awk 'NR==4' ~/.4walls)"

## sets the 4 desktop images in the compiz wallpaper plugin
dconf write /org/compiz/profiles/unity/plugins/wallpaper/bg-image "['$desk1', '$desk2', '$desk3', '$desk4']"
```
Edit to use your images directory and make executable.
I use this script because I use xplanetfx to draw the earth and moon over my wallpaper so need desk1 to remain the same image.

---

