---
title: "tilt screen horizontal"
date: 2011-02-11
forum: Desktop Environments
---

### Post by stdcinout on 2011-02-11
hi guys 
i was wondering if we can tilt our desktop environment to horizontal position.. what i meant is tilt 90 degree so that i can books with my head on the bed... 

do i have to configure xorg ? or any shortcut / software to do this? 
thanks

---

### Post by Copper Bezel on 2011-02-11
Yep, there's a shortcut through a program called xrandr for rapidly changing screen size or orientation, and it's apparently pretty widely used for using netbooks to read in bed; I do so quite a bit myself, and once you get it all together with a couple of other tweaks, it's so gloriously smooth it's hard to believe it's not an intended feature of the machine. 

Xrandr is command-line based, but that means that you can create keystroke commands or launchers for the commands and such. You can run the command

xrandr -o left

And you're there. Replace "left" with "normal" to switch back.

You can set these to a toggle script, as described [here]("http://blog.gammal.org/2006/06/screen-rotation-using-xrandr.html"), a text file you can execute from a single command that stores the current state in another text file so that it knows how to switch back. Then you can run it from a panel launcher or screen edge binding in Compiz; click once for portrait, then again to revert to landscape.

Now, this is where it gets cool. Do you have a Synaptics touchpad? If so, you can set up a tweaked driver and a script that will reorient the trackpad, too, so that it's oriented with the screen. [Aapo Rantalainen]("https://launchpad.net/%7Eaapo-rantalainen/+archive/ppa-aaporantalainen") has a tweak to the Synaptics trackpad driver to rotate all input to match the screen, specifically designed for netbooks in bed although it has some other uses, as well. It's quick and painless to install, and then you can just add

synclient Orientation=1

for portrait and

synclient Orientation=0

for landscape to that same toggle script. The whole process of the switchover is nigh-instantaneous and ridiculously convenient.

Edit: Or, duh, I could just give you the modified script I'm using in the first place. I'm like 99% certain that xrandr is installed by default, but double-check, then install the patch if you have a Synaptics touchpad. Make this an executable hidden text file in your home directory:

> #!/bin/bash
rotate=`cat ~/.screen-orientation`
echo $rotate
    if [ "$rotate" = "normal" ];
    then
    rotate="left"
    wacom="CCW"
    synaptics="1"
    else
        if [ "$rotate" = "left" ];
        then
            rotate="normal";
            wacom="NONE";
            synaptics="0"
        fi
    fi
echo "rotate = "$rotate
echo "wacom = "$wacom
xrandr -o "$rotate";
xsetwacom set "12" Rotate "$wacom";
xsetwacom set "13" Rotate "$wacom";
xsetwacom set "11" Rotate "$wacom";
synclient orientation="$synaptics"
echo $rotate > ~/.screen-orientation;

Then make a second text file simply called .screen-orientation with just the word 

> normal

and don't flag this second one as executable. Set the other one to a launcher. Enjoy. = )

---

