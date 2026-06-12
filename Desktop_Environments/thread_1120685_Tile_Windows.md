---
title: "Tile Windows?"
date: 2009-04-09
forum: Desktop Environments
---

### Post by mxboy15u on 2009-04-09
Is there a function like windows has to automatically tile windows horizontally and vertically?

---

### Post by Bramkaandorp on 2009-06-27
I will bump, and add the question if any other arranging of windows is possible.

Thanks.

---

### Post by zhocchao on 2009-06-27
in compiz there's a tiling plugin, but you have to install an extra package (don't know the name). Without compiz tiling can be done with a bash script (any arrangement you like), or by using a tiling window manager.

---

### Post by Bramkaandorp on 2009-06-28
I am really interested in that bash script. I have no knowledge of scripting, but if there is a script which gives me keyboard shortcuts without using compiz (I use sketchup a lot, so compiz is out of the question), that would be fine.

Any up to date info would be appreciated, since I use Jaunty.

Thanks,

Bram

---

### Post by zhocchao on 2009-06-28
for this script wmctrl should be installed. It ignores minimized windows (can be changed) and gives alternative layouts for 2-5 windows on second trigger. You have to create a .temptilefile in your home and make it executable. It can be empty (or type -1 as text to be sure). The active window is always the biggest left. m , n should be changed depending on theme.

---

### Post by danshumaker on 2009-07-17
It seems that is a very common request.
[URL="http://ubuntuforums.org/showthread.php?t=469585&page=4"]
Older thread[/URL]

In that older thread, that is closed now (otherwise I would comment there), some guy ForLong tried to force his opinion as fact on all of us and say that tiling windows is not that common.

A guy named bazzer argued the contrary belief.  I TOTALLY agree with bazzer.  I'm a developer and artist and I love tiling and use it all the time in windows and in ubuntu heron and other releases.  I wish and pray that something like that becomes available for the mac as well.

Now that I've upgraded to Jaunty, I have to go search through about six different threads, compile the "tile" hack, combine it with compiz hotkeys, maybe install ion3, maybe try IceWM or some other wm,, etc.   Eventually I just get really pissed that it's not standard.

Heres some other links of people trying to find and do tiling:
[LIST]
[*][brainstorm//brainstorm.ubuntu.com/idea/428/]("http://brainstorm.ubuntu.com/idea/428/")
[*][http://ubuntuguide.org/wiki/Ubuntu:Edgy/TipsAndTricks#How_to_tile_windows_in_gnome]("http://ubuntuguide.org/wiki/Ubuntu:Edgy/TipsAndTricks#How_to_tile_windows_in_gnome")
[*][http://tombuntu.com/index.php/2009/03/17/introduction-to-the-xmonad-tiling-window-manager/]("http://tombuntu.com/index.php/2009/03/17/introduction-to-the-xmonad-tiling-window-manager/")
[*][http://ubuntuforums.org/showthread.php?t=470160&highlight=tile+windows]("http://ubuntuforums.org/showthread.php?t=470160&highlight=tile+windows")
[*][http://brainstorm.ubuntu.com/idea/5466/]("http://brainstorm.ubuntu.com/idea/5466/")
[*][http://brainstorm.ubuntu.com/idea/9286/]("http://brainstorm.ubuntu.com/idea/9286/")
[*][http://brainstorm.ubuntu.com/idea/1940/]("http://brainstorm.ubuntu.com/idea/1940/")

[/LIST]

I can't beleive after seeing this list of links and posts and votes that someone would actually think that tiling windows is still not wanted!!!!

This forlong character seems to think wobbly windows is more important.  What a waste of time and effort.

---

### Post by aallison05 on 2009-08-03
I totally agree dan.  It may not be necessary for the smaller laptops or older machines with small screens out there, but my 23" monitor screams for some tiling action on a regular basis.

---

### Post by ceti331 on 2009-08-21
> **aallison05 said:**
> I totally agree dan.  It may not be necessary for the smaller laptops or older machines with small screens out there, but my 23" monitor screams for some tiling action on a regular basis.

i guess what usually happens is people on desktop machines have multiple monitors, and simply work with 2 maximized apps. Tiling seems much more necasery on a single screen  (especially laptop)


I agree tiling should be a default hotkey. windows 7 solution of WIN+Left/Right to maximize to left/right halves of the screen is a reasonable solution

---

### Post by stinkeye on 2009-08-24
On my jaunty machine I have a tile plugin in compiz (0.8.2) which I think came in the *compiz-fusion-plugins-unsupported* package from the universe repos.

---

### Post by macogw on 2009-08-24
I use the tiling window manager Xmonad.  Other tiling WMs include Ion2 and RatPoison and twm and dwm.

---

### Post by danshumaker on 2009-08-24
Ok, so I just spent a few months trying out Xmonad.  I was very exicted about it.  Played around with several of the different configuration files.  Got things working the way I wanted (except for memorized sessions).  Combined it with gnome and all was well, except after an hour or so it would lock up.  So after a week of lock-ups I'm going to try and get the compiz program to work .... AGAIN.  

What prompted me to abort from compiz in the first place is when I click on the "Tile Window" button to enable it, it stays checked for about 4 seconds and then is mysteriously unchecked right before my eyes.  It must be checking with the gnome system to see if it is supported or something and then "decides" that it's not.

The doubly strange thing is I checked the compiz setting while using the Xmonad window manager and this same compiz tile window option was checked and remained checked.   

The sad thing is that the same compiz tile window option use to work in Hardy Heron (or whatever the version was before Jaunty).

Anybody else feeling the pain?

I just tried this and it didn't help:  [http://dokuwiki.osuosl.org/development/tiling_windows_with_compiz](http://dokuwiki.osuosl.org/development/tiling_windows_with_compiz)

---

### Post by stinkeye on 2009-08-25
> **danshumaker said:**
> Ok, so I just spent a few months trying out Xmonad.  I was very exicted about it.  Played around with several of the different configuration files.  Got things working the way I wanted (except for memorized sessions).  Combined it with gnome and all was well, except after an hour or so it would lock up.  So after a week of lock-ups I'm going to try and get the compiz program to work .... AGAIN.  

What prompted me to abort from compiz in the first place is when I click on the "Tile Window" button to enable it, it stays checked for about 4 seconds and then is mysteriously unchecked right before my eyes.  It must be checking with the gnome system to see if it is supported or something and then "decides" that it's not.

The doubly strange thing is I checked the compiz setting while using the Xmonad window manager and this same compiz tile window option was checked and remained checked.  
 

The sad thing is that the same compiz tile window option use to work in Hardy Heron (or whatever the version was before Jaunty).

Anybody else feeling the pain?

I just tried this and it didn't help:  [http://dokuwiki.osuosl.org/development/tiling_windows_with_compiz](http://dokuwiki.osuosl.org/development/tiling_windows_with_compiz)

That how to was taken from a forum post 
[[COLOR="DarkRed"]_Compiling additional Compiz Fusion plugins from GIT_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=774561")
A later posting says "in 9.04 Jaunty Jackelope, you want to grab the unsupported plugins from here rather than git"
[[COLOR="DarkRed"]_later post_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=7138244&postcount=13")

I've had the problem before of not being able to tick the tiling box but at the moment works fine with no compiling.
I have this third party repo enabled
```
deb http://ppa.launchpad.net/compiz/ppa/ubuntu jaunty main
```
and the universe repo ticked and just downloaded
```
compiz-fusion-plugins-unsupported
```
through synaptic

[[COLOR="DarkRed"]_plugins in unsupported package_[/COLOR]]("http://wiki.compiz-fusion.org/PluginsUnsupported")

Hope that helps.

---

### Post by PhoHammer on 2009-09-28
> **stinkeye said:**
> 

I've had the problem before of not being able to tick the tiling box

I'm having this problem even after installing the plugins...

I really want to try tiling, but it seems like I always end up with a tangled up Ubuntu mess when I switch the DE or WM, so I am hesitant to try a tiling WM.

---

### Post by stinkeye on 2009-09-29
> **PhoHammer said:**
> I'm having this problem even after installing the plugins...

I really want to try tiling, but it seems like I always end up with a tangled up Ubuntu mess when I switch the DE or WM, so I am hesitant to try a tiling WM.
You may want to have a look at this applet for the gnome panel:
[[COLOR="DarkRed"]_xtile_[/COLOR]]("http://open.vitaminap.it/en/x_tile.htm")
It's under early development and is a bit cumbersome but should get better.

---

### Post by Frankenpunk on 2009-09-29
I use compiz-fusion. There is a "maximumize" option that covers all my tiling needs. Install compiz, type "ccsm" into a terminal window, and find the "maximumize" option, play with the settings to get what you want.

---

### Post by zlatkart on 2009-10-11
for those without Compiz could try this:
[http://ubuntuforums.org/showthread.php?t=1288385](http://ubuntuforums.org/showthread.php?t=1288385)

---

### Post by sdmarshall73 on 2009-10-25
Hey found an ideal solution to this. Try out X-tile.   [http://open.vitaminap.it/en/x_tile.htm](http://open.vitaminap.it/en/x_tile.htm)

Didn't need anything else. Easy to install..easy to use.

---

### Post by jonnan on 2009-11-01
Given that I haven't found a version of tile that works on a 64 bit pc, x-tile is definitely an improvement, but if anyone has that bash script for wmctrl that was mentioned, that might be more customizable and more universal.

But it's *sooo* much nicer than not having tiling - many thanks.

Jonnan

---

### Post by ArielEnter on 2009-11-04
> **stinkeye said:**
> On my jaunty machine I have a tile plugin in compiz (0.8.2) which I think came in the *compiz-fusion-plugins-unsupported* package from the universe repos.

Jajaja, The first time I tried I didn't find the option in the compizConfig Settings Manager. It's on the window Manager category, just in case that somebody is as absentminded as I am, or maybe it's not there until you reboot. I just can't believe it, I been looking for a way to do it for days and the solution was so simple. Jajaja, how funny.

I was using whaw instead, I would recommend it if you can't use compiz. Just read carefully the manual to understand how to use it from the terminal.

---

### Post by stinkeye on 2009-11-05
Whoopee!
I just installed the tile plugin in a fresh install of karmic.
All I did was enable the development repo for compiz in ubuntu tweak > third party sources.
Refreshed the sources and then went into synaptic and searched for
compiz-fusion-plugins-unsupported and installed it.
The version is 0.83+git20090911-1ubuntu1
Opened up CCSM , crossed my fingers and ticked the tile box and the tick remained.
I then went back to ubuntu tweak and unticked the development repo for compiz because now its running I don't want something stuffing it up.
Made my day.
:p:D:):tongue:O:):biggrin:

---

### Post by prvteprts on 2009-11-07
> **stinkeye said:**
> Whoopee!
I just installed the tile plugin in a fresh install of karmic.
All I did was enable the development repo for compiz in ubuntu tweak > third party sources.
Refreshed the sources and then went into synaptic and searched for
compiz-fusion-plugins-unsupported and installed it.
The version is 0.83+git20090911-1ubuntu1
Opened up CCSM , crossed my fingers and ticked the tile box and the tick remained.
I then went back to ubuntu tweak and unticked the development repo for compiz because now its running I don't want something stuffing it up.
Made my day.
:p:D:):tongue:O:):biggrin:

Thank you for this! It worked on my machine. I had the same problem: the Tile and Snow (perhaps even all the unsupported-plugins) checkboxes don't remain ticked. I thought it was initially because of the conflict with the Docky theme of Gnome-Do. Which by the way, leads me to another solution for Tiling.

Gnome-Do has a plugin which enables you to perform the Tiling and Cascading of windows. Just check in Gnome-Do's Preferences if the Window Manager plugin is ticked. It allows you to control windows for each workspace. Please ignore this if it has already been posted.

If you have this plugin installed, you probably wouldn't need the "unsupported" fusion plugins, though it doesn't allow you to tile vertically (which I need to do sometimes).

---

### Post by stinkeye on 2009-11-07
> **prvteprts said:**
> Thank you for this! It worked on my machine. I had the same problem: the Tile and Snow (perhaps even all the unsupported-plugins) checkboxes don't remain ticked. I thought it was initially because of the conflict with the Docky theme of Gnome-Do. Which by the way, leads me to another solution for Tiling.

Gnome-Do has a plugin which enables you to perform the Tiling and Cascading of windows. Just check in Gnome-Do's Preferences if the Window Manager plugin is ticked. It allows you to control windows for each workspace. Please ignore this if it has already been posted.

If you have this plugin installed, you probably wouldn't need the "unsupported" fusion plugins, though it doesn't allow you to tile vertically (which I need to do sometimes).
No problem.Thanks for the tip on gnome-do.Didn't know about that tiling option.Good to know as a backup window tiler when compiz stuffs up.

---

### Post by oktapod on 2009-11-14
Thank you prvteprts. I had installed Gnome Do but didn't now this. Now I can edit my spreadsheet tables without need of windows 7.

---

### Post by haan on 2009-12-04
**Tiling in Kubuntu and/or Ubuntu**

Execute the following script to generate the commands for Kubuntu (KDE) and/or Ubuntu (GNOME) for your resolution (without annoying overlapping windows). grid.sh:

```

#!/bin/bash

echo ""
echo "Ubuntu (GNOME) contains a nice utility Compiz Grid:"
echo "Tile, position and resize your windows to fit an imaginary grid."
echo "The functionality is based on Winsplit Revolution for Microsoft Windows."
echo "For more info, demos etc. see: http://winsplit-revolution.com"
echo ""
echo "This script can be used to define wmctrl commands for Kubuntu (KDE)"
echo "for your monitor resolution. These commands can be attached to"
echo "Key Bindings (keyboard shortcuts), so you have the same functionality"
echo "under KDE without the need to install a Tiling Window Manager like"
echo "xmonad, awesome or ion3."
echo ""
echo "The commands can also be used to emulate Windows 7 Aero Snap"
echo "without annoying overlapping windows."
echo "For more info about this subject see youtube or for example" 
echo "http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html"
echo ""
echo "NOTES:" 
echo "- This scipt uses xwininfo (part of x11-utils package) and wmctrl."
echo "  For (K)ubuntu:"
echo "  sudo apt-get install x11-utils wmctrl"
echo "- This script is tested with:"
echo "  Ubuntu 9.10 (resolution 1920x1200)"
echo "  Kubuntu 9.10 (resolution 1920x1200)"
echo "  Kubuntu 8.10 (resolution 1600x1200)"

# define maximum size of usable screen
wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz
sleep 1

WIDTH=$((`xwininfo -id $WINDOWID | grep 'Width:' | cut -f 2 -d ':'`))
HEIGHT=$((`xwininfo -id $WINDOWID | grep 'Height:' | cut -f 2 -d ':'`))
BORDERY=$((`xwininfo -id $WINDOWID | grep 'Corners:' | cut -f 11 -d ' ' | cut -f 2 -d '-'`))
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;
sleep 1
wmctrl -r :ACTIVE: -e 0,0,0,$WIDTH,$HEIGHT
sleep 1

BORDER=$((`xwininfo -id $WINDOWID | grep 'Absolute upper-left X:' | cut -f 2 -d ':'`))
BOTTOM=$((`xwininfo -id $WINDOWID | grep 'Corners:' | cut -f 11 -d ' ' | cut -f 2 -d '-'`))
BORDERY=$(($BORDERY-(`xwininfo -id $WINDOWID | grep 'Corners:' | cut -f 11 -d ' ' | cut -f 2 -d '-'`)))
TOP=$((`xwininfo -id $WINDOWID | grep 'Relative upper-left Y:' | cut -f 2 -d ':'`))

if [ $TOP -eq 0 ]
then #KDE
    echo ""
    echo "----------------------"
    echo "Assuming KDE, Correct?"
    echo "----------------------"
    WIDTH=$(((`xwininfo -id $WINDOWID | grep 'Width:' | cut -f 2 -d ':'`)-2*$BORDER))
    HEIGHT=$(((`xwininfo -id $WINDOWID | grep 'Height:' | cut -f 2 -d ':'`)-2*$BORDERY))
    TITLE=$((`xwininfo -id $WINDOWID | grep 'Absolute upper-left Y:' | cut -f 2 -d ':'`))

    echo ""
    echo "Below are the wmctrl commands for KDE (Kubuntu)."
    echo ""
    echo "The Key Bindings (keyboard shortcuts) can be set in the following way:"
    echo "sudo apt-get install xbindkeys xbindkeys-config"
    echo "xbindkeys --defaults > ~/.xbindkeysrc"
    echo "echo \"xbindkeys\" > ~/.kde/Autostart/startxbindkeys.sh"
    echo "chmod u+x ~/.kde/Autostart/startxbindkeys.sh"
    echo "~/.kde/Autostart/startxbindkeys.sh"
    echo "xbindkeys-config"
    echo "finally add the commands below"
    echo ""
    echo "Centre       Control+Alt+KP_Begin:"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,0,$WIDTH,$HEIGHT"
    echo ""
    echo "Left         Control+Alt+KP_Left:"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,0,$(($WIDTH/2-$BORDER)),$HEIGHT"
    echo ""
    echo "Right        Control+Alt+KP_Right:"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$(($WIDTH/2+($BORDER))),0,$(($WIDTH/2-$BORDER)),$HEIGHT"
    echo ""
    echo "Top          Control+Alt+KP_Up:"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,0,$WIDTH,$(($HEIGHT/2-($TITLE/2+$BORDERY)))"
    echo ""
    echo "Bottom       Control+Alt+KP_Down:"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,$(($TITLE+$BORDERY+$TOP+($HEIGHT/2-($TITLE/2+$BORDERY)))),$WIDTH,$(($HEIGHT/2-($TITLE/2+$BORDERY)))"
    echo ""
    echo "Top Left     Control+Alt+KP_Home:"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,0,$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDERY)))"
    echo ""
    echo "Top Right    Control+Alt+KP_Prior:"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$(($WIDTH/2+($BORDER))),0,$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDERY)))"
    echo ""
    echo "Bottom Left  Control+Alt+KP_End:"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,$(($TITLE+$BORDERY+$TOP+($HEIGHT/2-($TITLE/2+$BORDERY)))),$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDERY)))"
    echo ""
    echo "Bottum Right Control+Alt+KP_Next:"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$(($WIDTH/2+($BORDER))),$(($TITLE+$BORDERY+$TOP+($HEIGHT/2-($TITLE/2+$BORDERY)))),$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDERY)))"
else #GNOME
    echo ""
    echo "------------------------"
    echo "Assuming GNOME, Correct?"
    echo "------------------------"
    WIDTH=$((`xwininfo -id $WINDOWID | grep 'Width:' | cut -f 2 -d ':'`))
    HEIGHT=$((`xwininfo -id $WINDOWID | grep 'Height:' | cut -f 2 -d ':'`))

    wmctrl -r :ACTIVE: -e 0,0,$TOP,$WIDTH,$(($HEIGHT-2*$BOTTOM))
    sleep 1
    TITLE=$(((`xwininfo -id $WINDOWID | grep 'Absolute upper-left Y:' | cut -f 2 -d ':'`)-$TOP-$BORDER))
    TOP=$(($TOP-$TITLE))
    
    echo ""
    echo "Below are the wmctrl commands for GNOME (Ubuntu)."
    echo "The Key Bindings (keyboard shortcuts)"
    echo "or Edge Bindings (like Aero Snap) can be set under:"
    echo "System -> Prefences -> CompizConfig Settings Manager ->"
    echo "Commands -> Commands/Key Bindings/Edge Bindings"
    echo ""
    echo "Centre       <Control><Alt>KP_5:"
    #echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$BORDER,$(($TITLE+$TOP)),$WIDTH,$HEIGHT"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,0,$WIDTH,$HEIGHT"
    echo ""
    echo "Left         <Control><Alt>KP_4:"
    #echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$BORDER,$(($TITLE+$TOP)),$(($WIDTH/2-$BORDER)),$HEIGHT"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,0,$(($WIDTH/2-$BORDER)),$HEIGHT"
    echo ""
    echo "Right        <Control><Alt>KP_6:"
    #echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$(($WIDTH/2+(2*$BORDER))),$(($TITLE+$TOP)),$(($WIDTH/2-$BORDER)),$HEIGHT"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$(($WIDTH/2+(2*$BORDER))),0,$(($WIDTH/2-$BORDER)),$HEIGHT"
    echo ""
    echo "Top          <Control><Alt>KP_8:"
    #echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$BORDER,$(($TITLE+$TOP)),$WIDTH,$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,0,$WIDTH,$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo ""
    echo "Bottom       <Control><Alt>KP_2:"
    #echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$BORDER,$(((2*($TITLE+$BORDER))+$TOP+($HEIGHT/2-($TITLE/2+$BORDER)))),$WIDTH,$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,$(((2*($TITLE+$BORDER))+$TOP+($HEIGHT/2-($TITLE/2+$BORDER)))),$WIDTH,$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo ""
    echo "Top Left     <Control><Alt>KP_7:"
    #echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$BORDER,$(($TITLE+$TOP)),$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,0,$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo ""
    echo "Top Right    <Control><Alt>KP_9:"
    #echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$(($WIDTH/2+(2*$BORDER))),$(($TITLE+$TOP)),$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$(($WIDTH/2+(2*$BORDER))),0,$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo ""
    echo "Bottom Left  <Control><Alt>KP_1:"
    #echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$BORDER,$(((2*($TITLE+$BORDER))+$TOP+($HEIGHT/2-($TITLE/2+$BORDER)))),$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,$(((2*($TITLE+$BORDER))+$TOP+($HEIGHT/2-($TITLE/2+$BORDER)))),$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo ""
    echo "Bottum Right <Control><Alt>KP_3:"
    #echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$(($WIDTH/2+(2*$BORDER))),$(((2*($TITLE+$BORDER))+$TOP+($HEIGHT/2-($TITLE/2+$BORDER)))),$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo "wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,$(($WIDTH/2+(2*$BORDER))),$(((2*($TITLE+$BORDER))+$TOP+($HEIGHT/2-($TITLE/2+$BORDER)))),$(($WIDTH/2-$BORDER)),$(($HEIGHT/2-($TITLE/2+$BORDER)))"
    echo ""
    echo "TIP: For GNOME (Ubuntu) Key Bindings use Compiz Grid instead. Go to:"
    echo "     System -> Prefences -> CompizConfig Settings Manager ->"
    echo "     Window Management -> Grid"
fi

wmctrl -r :ACTIVE: -e 0,0,0,$WIDTH,$HEIGHT

echo ""
echo "Current used values:"
echo "border: $BORDER pixels"
if [ $TOP -eq 0 ]
then #KDE
    echo "bordery: $BORDERY pixels"
fi
echo "width:  $WIDTH pixels"
echo "height: $HEIGHT pixels"
echo "bottom: $BOTTOM pixels"
echo "top:    $TOP pixels"
echo "title:  $TITLE pixels"

```

---

### Post by Wulfrunner on 2010-01-21
I have found that this feature is already present in a default install of 9.10. You will need to install CompizConfig Settings Manager. Go to Window Management, and enable the Grid plugin. You can then scale individual windows to various corners or sides of your screen. For example, the equivalent of Windows7 SUPER+left is CTRL+ALT+NUM4 (numpad left arrow). Of course this can be changed to a combination you prefer.

---

### Post by AntonioTheGreat on 2010-02-15
Thanx Wulfrunner, it is a perfect solution! :D

---

### Post by skarychinezeguie on 2010-02-18
wulfrunner you the man. now i can have my rotating sphere, 3 space desktop and just use SHIFT+U,D,L, or R to snap the windows to the top, bottom, left or right. just like windows Aero snap, but better. some windows aren't TOTALLY resizeable though, like the compiz config window. it won't fit to half the screen, but that is not the fault of the grid plugin. you could probably change the window rules to compensate for such windows though.

thanks again

---

### Post by blur xc on 2010-02-18
I addition to the grid plugin (I love that plugin) try maximumize.  It "maximizes" the active window to fill the available space on your desktop.  It's quite handy...


BM

---

### Post by DanCar on 2010-05-18
Is installing CompizConfig Settings Manager still the best option for 10.04?

Thanks,
Daniel

---

### Post by stinkeye on 2010-05-29
There is a script to install experimental plugins for Ubuntu 9.04 - 10.04, compiz version 0.8.x. 

It can install:
anaglyph
atlantis
cubemodel
dialog
elements
extra_animations
fakeargb
fireflies
freewins
ghost
icons
mswitch
photowheel
putplus
screensaver
simple_animations
smartput
snow
snowglobe
stackswitch
stars
static
swap
tile
toggle_decoration
wizard
workspacenames


The script allows you choose which ones to install or install them all.
A lot of them are just fluff.
I find the tile and workspace names useful.
[**_[COLOR="DarkRed"]http://forum.compiz.org/viewtopic.php?f=114&t=12012[/COLOR]_**]("http://forum.compiz.org/viewtopic.php?f=114&t=12012")

---

### Post by UberStudent on 2010-05-29
Try x-tile [http://open.vitaminap.it/en/x_tile.htm](http://open.vitaminap.it/en/x_tile.htm)

No compositing necessary.  Comes default on UberStudent. :cool:

---

