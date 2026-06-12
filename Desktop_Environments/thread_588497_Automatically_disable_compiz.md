---
title: "Automatically disable compiz"
date: 2007-10-23
forum: Desktop Environments
---

### Post by Amt0571 on 2007-10-23
Hello,

I have found that Blender has some problems when running with Compiz enabled. I have been looking with no luck for a way to automatically disable compiz when running Blender and reenable it when exiting.

It doesn't bother me a lot to disable it manually, but it would be a lot better if it could be done automatically. Is it possible to make "application profiles" for compiz?

Thanks

---

### Post by ecschiel on 2007-10-31
I have the same problem a couple of days ago and I decided to write a simple script to do the job. Here it is:
```

#!/bin/bash
#           runner
#
#  Sun Oct 28 07:17:37 2007
#  Copyright  2007  Enrique Schiel
#  <ecschiel@yahoo.com.ar>

# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
# 
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU Library General Public License for more details.
# 
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor Boston, MA 02110-1301,  USA

CHANGE=0

if ps -e | grep compiz; then
    CHANGE=1
fi

if [ $CHANGE == 1 ]; then
    printf "Disabling advanced desktop efects...\n"
    /usr/bin/metacity --replace &
fi

printf "Running the game...\n"
$@ &
wait $!

if [ $CHANGE == 1 ]; then
    printf "The game is finished. Restoring advanced desktop efects...\n"
    /usr/bin/compiz --replace &
fi

```

Save this script to something called "runner" or anything that suits you and give permission for execution

```
 chmod 755 runner 
```

And then you only have to type in the console

```
runner <program to run + args>
```

and the script do the job in the case it's necessary. You can add it in the menus to, just made a right click in the menu and edit the menu, the same that in the command line, you need to apped it just in the applications that use 3D, The others generally don't have trouble with compiz. Be aware that it only works with GNOME (Metacity), and not KDE or others. If you have doubts just PM me

---

### Post by rogerdean on 2007-11-12
that's just brilliant. thank you very much. it's perfect for my google earth problems
cheers
roger

---

### Post by Amt0571 on 2007-11-13
Thank you very much. This is perfect :)

---

### Post by Triptoph on 2007-11-14
Exactly what I was looking for!  Well, actually I was looking for commands to disable/enable compiz from the command line so I could write a script, so this is much better :o) 

Thanks!


Now, I am having a bit of trouble with the script, and I'm not sure how to fix it as I'm very new to the linux world (Vista convert!)

The script fails when you have an argument with spaces in it, e.g.:

runner wine /home/tony/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe

The escaped spaces are removed before being passed to the script like this:

wine  /home/tony/.wine/drive_c/Program Files/World of Warcraft/WoW.exe

and hence wine fails, complaining that it cannot find "/home/tony/.wine/drive_c/Program".  Using quotation marks instead of escaping the individual spaces also doesn't work.  

Any ideas on how to improve the script to allow spaces?

Also, I'm curious as to what $@ does as opposed to $* ?

Thanks for the help :)

---

### Post by Triptoph on 2007-11-14
Found a solution, though not very elegant.

Adding the following to the script (just after the comments) will take care of the problem:

```
IFS=$'\t\n'
```

Also, I changed the line ```
$@ &
``` to ```
$* &
``` though I'm not sure if that made any difference at all :)

If you intend to extend the script you should be aware that this may result in some strange errors as it causes bash to recognize only tabs and newlines and not spaces as separators between parameters as I understand it (might be wrong, still very much a linux noob!).

---

### Post by Triptoph on 2007-11-14
Unfortunately the commands with metacity and compiz have a couple of bad side-effects for me:

I run a dual-head setup with an nvidia 8800 GTS card, in TwinView mode.  Without the script, when wow is in windowed/maximized mode, it uses one of my two screens, which is the behaviour I need.  With the script, it will span both monitors.  I can configure the game to work around this by changing the viewport in game, but the second side-effect is a show-stopper:

After running the script, opening some windows doesn't work, for example opening my home folder (nautilus?), or pressing the red icon to bring up the shutdown options.

I'm using ubuntu i386 gutsy 7.10 on the following hardware:
intel Q6600 quad core cpu
4GB RAM (only 3 of which are in use i believe using i386 version - 64 would not install despite a few days of attempts)
Asus P5K Deluxe motherboard, P35 chipset
Nvidia 8800 GTS 320MB video card
ubuntu-packaged nvidia drivers
on-board sound
creative x-fi sitting uselessly in the case.

---

### Post by appye on 2007-12-07
> **Triptoph said:**
> Found a solution, though not very elegant..

You could just create a script and launch it directly like this:

```
/usr/bin/metacity --replace &
wine "/home/appye/.wine/drive_c/Program Files/Paint_Shop_Pro_704/PSP.EXE"
/usr/bin/compiz --replace &
```

Create a launcher pointing directly to the script.  This might be better than changing bash defaults (if that is what that does, bash noob here as well).

I don't have WOW or any Windows games, but this PSP example works for me.  I don't know if that would fix the other problems you describe though.

ecschiel, I do applaud you for your script.  You obviously know more about bash than I do.  Much easier than making individual scripts for everything.  Now I can just change the launcher, at least for most things it seems.  Most any 3D app is not a good mix with compiz right now.

---

### Post by circlemaster on 2008-04-20
This is a cool solution, however I have the problem that whenever it switches between metacity/compiz all my windows on all desktops gets crammed into the first desktop, so for me it gets totally useless since I make use of having windows on different desktops. I don't really have the energy to move each window to its correct place every time after I play a game :)
Maybe it's a bug?

---

### Post by gfern on 2008-06-04
I'm using Ubuntu Hardy Heron. Newbie here. I did what you said, saved the script as "runner" and applied chmod 755 to it. But when I try to run "runner googleearth + args" on the console it replies "bash: runner: command not found". What am I doing wrong? Thanks!

---

### Post by gfern on 2008-06-04
Ok, I figured on my own how to get it going, moved it to /bin and it all worked fine. Well, almost. 

I'm getting an error message at the end of the script every time I close Google Earth. Here's the log: 

Disabling advanced desktop efects...
Running the game...
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x1200007 specified for 0x1200005 (Initializi).
The game is finished. Restoring advanced desktop efects...
Checking for Xgl: gui@gui-laptop:~$ not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1400x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


See that message at the end about an unsupported value??? What is it?  What should I do about it? I'm REALLY new at Ubuntu and Linux. Got it running for the first time ever last Thursday, so bare with me... ; )

---

