---
title: "HOWTO: Preserve workspaces for certain windows between compiz and metacity"
date: 2009-02-15
forum: General Help
---

### Post by Twilight in Zero on 2009-02-15
Hi! Do you use compiz? Do you have windows that you absolutely have to have on a certain workspace? Do you use metacity too? Like, for playing games? Have you ever noticed that when you switch to metacity, your precious workspace settings are tossed away? This is because metacity and compiz's workspace models are incompatible with each other. And also, have you noticed that when you switch back to compiz, your windows don't move back where they're supposed to be? Personally, I find that to be a feature deficiency for the place windows plugin. But none the less, it doesn't work.

We can fix this, to an extent.

Some would say, non-compositing compiz is coming, so this won't be needed someday. But when? We're looking at months, at least. For those who live in the here and now, this will be a great help.

First, I must make some disclaimers.

-= You need to be somewhat familliar with the command line.
-= If you are the kind of user who puts windows on absolutely random workspaces as part of their workflow, and needs ALL of them to be preserved, *this script will not do that.* It will only preserve windows that are set to certain workspaces. *If your window placement follows a trend*, this may still be useful to you.
-= You will need to do a tiny bit of thinking and math. It's not hard; just multiplying and adding. You have a calculator program; use it. If you can't be arsed, this guide isn't for you either. You'll be missing out, you lazy bum.

Now that that's out of the way, let's get some prerequisites. The primary tool for this script is wmctrl. Get it with:```
sudo aptitude install wmctrl
```
You may also want to get devilspie if you want to preserve certain window rules. Get it with:```
sudo aptitude install devilspie
```However, **do not use devilspie to set your workspaces!** It's a little bit glitchy. It's much more reliable to use wmctrl to do that. I won't cover how to set window rules with devilspie; there are other guides for that.

And now, here is the magic script. Create a script called wm-switch (or whatever you want) in whichever binary directory you prefer. /home/you/bin is the best, because you don't have to use sudo. chmod +x it. Now, here is my script, personalized for my needs. You will be changing this.
```
#!/bin/bash
# Just switches between metacity and compiz.
# Easier than fusion-icon and preserves certain windows' workspaces.
ps -C "compiz.real" >& /dev/null
if [[ $? -eq 0 ]]; then
	metacity --replace &
	sleep 1  # Just to be safe
	devilspie -a &
	wmctrl -r "FullscreenTerminal" -t 3
	wmctrl -x -r "quodlibet" -t 2
else
	killall devilspie # It doesn't play nice with compiz.
	compiz --replace &
	sleep 1  # Just to be safe
	wmctrl -r "FullscreenTerminal" -e 0,3840,-1,-1,-1
	wmctrl -x -r "quodlibet" -e 0,2560,-1,-1,-1,-1
fi
exit 0
```

You want to keep most of that the same. Take out the devilspie lines if you won't be using it. My two windows are a maximized Quod Libet that goes on workspace 3, and a maximized gnome-terminal that goes on workspace 4.

Here's how to make your commands for metacity. It explains the options for wmctrl that you will need. This is the easy part. This will also apply to compiz below; remember it.

wmctrl
-x  // Use the window class instead of window title for -r. This is a little more foolproof. You probably use the window class to specify window placement in compiz; use CCSM to find out what your window classes are.
-r "string"  // Text that will be found in the window to be moved's title. If -x is specified, the window class is used instead. Case-insensitive.
-t #  // Workspace number, starting from zero. So workspace 3 would be 2 here. Also, if you want to make the window sticky, or across all workspaces, you *can* put -1 here, but that's managed in compiz's window rules plugin, so it's better to use devilspie for that for consistency.
-e 0,x,y,width,height  // Maybe you want to move the window somewhere or resize it after switching its workspace. So then you'd use this. If you don't want to change a certain value, put -1. If you don't want to mess with the window's position on the workspace, leave it out. The first part of the -e switch is "gravity" according to wmctrl's manpages. I don't know what it's for, so I don't mess with it.

And here's now to make your commands for compiz. This is where it gets tricky. Compiz's workspaces are made of just one giant virtual desktop, and the workspaces are viewports onto certain areas of that desktop. This means that the -t switch for wmctrl is not going to work; there's only one desktop! So if your screen was 1024x768, and you have 4 workspaces right next to each other, that virtual desktop size would be 4096x768. This is most likely if you have the desktop cube. The viewports for each workspace are specified by the top left corner. So workspace 1 on that desktop would be at 0,0, workspace 2 at 1024,0, workspace 3 at 2048,0, and workspace 4 at 3072,0. If you have your workspaces arranged with 2 on top, and 2 on bottom, then your virtual desktop would be 2048x1536, and your workspaces would be at 0,0, 1024,0, 0,768, and 1024,768. My screen resolution is 1280x800, so I put Quod Libet at 2560,0, and gnome-terminal at 3840,0. Since it's all on one big desktop, we use the -e switch to move it.

If your windows are maximized, you need only figure out where your desired viewport is, and use the -e switch to move it there. Thus, my maximized Quod Libet and gnome-terminal. If they aren't, compiz won't remember where on each workspace they are. You need to decide on a good place to put them. Its location would be (viewport x) + (window x), (viewport y) + (window y). Here's an example, let's say you wanted gedit at 100, 100 on viewport 3 of a desktop cube, and your screen resolution is 1024x768.

metacity's wmctrl command: wmctrl -x -r "gedit" -t 2 -e 0,100,100,-1,-1
compiz's wmctrl command: wmctrl -x -r "gedit" -e 0,2148,100,-1,-1

So, got all that figured out? Let's make a custom version of the script. We'll put the gedit from above, and a maximized Firefox on workspace 4. We'll assume a screen resolution of 1024x768, and our workspaces will be arranged for the desktop cube. Also, we won't use devilspie. Here's the custom script:
```
#!/bin/bash
# Just switches between metacity and compiz.
# Easier than fusion-icon and preserves certain windows' workspaces.
ps -C "compiz.real" >& /dev/null
if [[ $? -eq 0 ]]; then
	metacity --replace &
	sleep 1  # Just to be safe
	wmctrl -x -r "gedit" -t 2 -e 0,100,100,-1,-1
	wmctrl -x -r "firefox" -t 3
else
	compiz --replace &
	sleep 1  # Just to be safe
	wmctrl -x -r "gedit" -e 0,2148,-1,-1,-1
	wmctrl -x -r "firefox" -e 0,3072,-1,-1,-1,-1
fi
exit 0
```

That's not too hard, is it? Now, you can use this script whenever you need to switch window managers. Like, for example, a nifty launcher on your panel, or a game launcher script.
```
#!/bin/bash
# Temporarily disables compiz to play a game.
ps -C "compiz.real" >& /dev/null
if [[ $? -eq 0 ]]; then
	wm-switch
	sleep 1  # I like using sleep to make sure
	$@
	sleep 1  # that things don't mess up
	wm-switch
else $@
fi
exit 0
```

If there's anything I can do to make this howto better, please let me know! Have fun! :D


Also, are there any skilled bash scripters interested in making this... perfect? It's possible to make a script that will preserve the workspace options for ALL windows. I've been thinking about the details, but I don't yet have the scripting skills to implement it. If you're interested, PM me.

---

### Post by mrchan on 2009-05-08
I have written a script which should preserve all window positions when changing to/fro compiz and metacity. I had been searching for a solution to using compiz and xrandr for rotation; rotating while compiz is in use will stall the redrawing of the screen. My work around was to rotate the screen, then run comipz --replace again to get the redrawing of the screen to be normal again, however, window positions were messed.

```

#!/bin/bash

CURR_WORKSPACE=`wmctrl -d | grep "*" | cut -d' ' -f 1`
CURR_WM=`wmctrl -m | grep "Name" | cut -d' ' -f 2`

SCREEN_WIDTH=`wmctrl -d | grep "*" | cut -d' ' -f 12 | sed 's/x.*//'`
VIEW_PORT=`wmctrl -d | grep "*" | cut -d' ' -f 8 | sed 's/,.*//'`
WINDOW_POSITIONS=`wmctrl -lG | awk 'OFS=" " {print $1,$2,$3,$4 ","}'`

case $CURR_WM in
Metacity)
    compiz --replace &
    sleep 1
    echo -n $WINDOW_POSITIONS | tr ',' '\n' | grep -v " \-1 " |
    while read line
    do
    `
        echo $line $CURR_WORKSPACE $SCREEN_WIDTH |
            awk '{print "wmctrl -i -r " $1 " -e 0," ($3 + ($2*$6)) - 10 "," $4 - 48 ",-1,-1"}'
    `
    done
    sleep 1
    wmctrl -o $[CURR_WORKSPACE*SCREEN_WIDTH],0
;;

compiz)
    metacity --replace &
    sleep 1

    echo -n $WINDOW_POSITIONS | tr ',' '\n' | grep -v " \-1 " |
    while read line
    do
    `
        echo $line $CURR_WORKSPACE $SCREEN_WIDTH $VIEW_PORT |
        awk '{print "wmctrl -i -r " $1 " -t " int(($3 + (2*$7))/(2*$6))}'
    `
    `
        echo $line $CURR_WORKSPACE $SCREEN_WIDTH $VIEW_PORT |
            awk '{print "wmctrl -i -r " $1 " -e 0," (($3 + $7*2)/2)%$6 - 5 "," $4/2 - 24 ",-1,-1"}'
    `
    #`
    #   echo $line $CURR_WORKSPACE $SCREEN_WIDTH $VIEW_PORT |
    #   awk '{print "wmctrl -i -r " $1 " -t " int(($3 + (2*$7))/(2*$6))}'
    #`
    done
    wmctrl -s $[VIEW_PORT/SCREEN_WIDTH]
;;

esac

```
Code's bit messy, but logic should be right.

---

### Post by themonkeymoo on 2010-08-01
First, many apologies for the thread necromancy.

Second, I've written a launcher script for World of Warcraft in linux available [here.]("https://sourceforge.net/projects/wowlaunchersh/")

I would like to include a slight modification to mrchan's script above in wowlauncher.sh, but it is missing any release/copyright information. My script is released under [the gpl.]("http://www.gnu.org/licenses/gpl.html") Is this acceptable to you, mrchan?

---

