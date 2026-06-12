---
title: "systemtray: blank space / icons not showing"
date: 2011-05-24
forum: Desktop Environments
---

### Post by Spektakel on 2011-05-24
As can be seen in the title of this post, I'm not quite sure what's going on exactly, but my systemtray icons in Lubuntu 11.04 are not shown the way they should. There's blank space between them, the equivalent of 2 or 3 icons, and the blank space is 'created' while starting up, as though they are programs. See the attached screenshot to get an idea what I'm talking about.

I'm really happy with Lubuntu, this is at the moment the only thing that's bugging me. It used to be 2 empty spaces in the systemtray, now it's 3. Any help would be appreciated, but please note I'm a simple end-user without much knowledge of Linux.

Thanks!

---

### Post by SteveDee on 2011-05-24
> **Spektakel said:**
> ... systemtray icons in Lubuntu 11.04 are not shown the way they should. There's blank space between them, the equivalent of 2 or 3 icons...

Is there really something there or is it just "space"?
If you left click in this blank area does anything happen?

I suggest you experiment with Panel Preferences to investigate this. Right click on the panel and select Panel settings.

Under Panel Applets you can move the applets up & down the list to change the order in the panel. Does the blank area move with the tray?

Also play with the Geometry settings, especially the alignment settings.

---

### Post by Spektakel on 2011-05-24
> **SteveDee said:**
> If you left click in this blank area does anything happen?

I suggest you experiment with Panel Preferences to investigate this.

It's just blank space, however it seems to be linked to programs trying to use that space, because the space will sometimes expand. For example, when I run "HP device manager", the blank space expands, but can't be clicked.

Experimenting with the Panel Preferences and geometry settings didn't help, the blank space moves with the system tray (see attachment).

Any suggestions? Thanks!

---

### Post by SteveDee on 2011-05-25
Please post your "panels" file. 
The path is probably something like this:-
```

/home/spektakel/.config/lxpanel/LXDE/panels

```

As .config is a hidden file you need to enable "show hidden files"

---

### Post by kerry_s on 2011-05-25
did you try changing the icon theme?
It could be because those icons in the space is not in your theme.

---

### Post by Spektakel on 2011-05-26
> **SteveDee said:**
> Please post your "panels" file.

Panel file says:
```
# lxpanel <profile> config file. Manually editing is not recommended.
# Use preference dialog in lxpanel to adjust config when you can.

Global {
    edge=bottom
    allign=left
    margin=0
    widthtype=percent
    width=100
    height=24
    transparent=1
    tintcolor=#ffffff
    alpha=119
    autohide=0
    heightwhenhidden=2
    setdocktype=1
    setpartialstrut=1
    usefontcolor=1
    fontcolor=#000000
    background=0
    backgroundfile=/usr/share/lxpanel/images/lubuntu-background.png
    iconsize=22
}

Plugin {
    type = menu
    Config {
        image=/usr/share/lubuntu/images/lubuntu-logo.png
        system {
        }
        separator {
        }
        item {
            command=run
        }
        separator {
        }
        item {
            image=gnome-logout
            command=logout
        }
    }
}

Plugin {
    type = launchbar
    Config {
        Button {
            id=/usr/share/applications/firefox.desktop
        }
        Button {
            id=/usr/share/applications/anki.desktop
        }
        Button {
            id=/usr/share/applications/leafpad.desktop
        }
        Button {
            id=/usr/share/applications/audacious2.desktop
        }
        Button {
            id=pcmanfm.desktop
        }
    }
}

Plugin {
    type = space
    Config {
        Size=4
    }
}

Plugin {
    type = wincmd
    Config {
        image=window-manager
        Button1=iconify
        Button2=shade
        Toggle=0
    }
}

Plugin {
    type = space
    Config {
        Size=4
    }
}

Plugin {
    type = space
    Config {
        Size=4
    }
}

Plugin {
    type = taskbar
    expand=1
    Config {
        tooltips=1
        IconsOnly=0
        ShowAllDesks=0
        UseMouseWheel=1
        UseUrgencyHint=1
        FlatButton=0
        MaxTaskWidth=200
        spacing=0
        GroupedTasks=1
    }
}

Plugin {
    type = tray
}

Plugin {
    type = volumealsa
}

Plugin {
    type = dclock
    Config {
        ClockFmt=%R
        TooltipFmt=%A %x
        BoldFont=0
        IconOnly=0
    }
}

Plugin {
    type = launchbar
    Config {
        Button {
            id=lubuntu-logout.desktop
        }
    }
}
```

Changing the icon theme did nothing to solve the problem.

---

### Post by kerry_s on 2011-05-26
can you do a pic of your panel applets?

like this.

---

### Post by Spektakel on 2011-05-26
> **kerry_s said:**
> can you do a pic of your panel applets?

See attachment. As you can see, the blank space retains any "picture" (in this case, the white of the right-click panel menu) that has hovered over it.

---

### Post by kerry_s on 2011-05-26
try changing your monitor refresh rate.

---

### Post by SteveDee on 2011-05-26
The panel file s OK (I added it to one of my computers).

I think kerry_s is on the right track re: icons: It looks like space is being allocated for icons that either don't exist or cannot be displayed.

What non-standard applications have you installed since installing Lubuntu?

---

### Post by kerry_s on 2011-05-26
> **SteveDee said:**
> The panel file s OK (I added it to one of my computers).

I think kerry_s is on the right track re: icons: It looks like space is being allocated for icons that either don't exist or cannot be displayed.

What non-standard applications have you installed since installing Lubuntu?

he says it's from menus, so i'm thinking artifacting. i get artifacting if my refresh is 75, which it defaults to, i have to change it to 60.

---

### Post by StrikerMan780 on 2011-10-14
I am having the same problems in a Lubuntu session in a standard Ubuntu 11.10 install.

---

### Post by Spektakel on 2011-10-14
Ok, here is how I fixed this issue. For me the problem seemed to be that I was running Ubuntu alongside Lubuntu. When I removed all Ubuntu elements, the problem was fixed: [http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

Be aware that this also removes programs you don't want to be removed, so it's quite a bit of a hassle to get everything back in order.

---

### Post by exanime on 2011-10-30
I have the same issue but only started in 11.10... in any case I have noticed the blank spaces seem to get created as the computer resumes from stand-by... 99% of the time I suspend via pm-suspend as opposed to letting the power manager do it on idle time.

I have found no way to eliminate the white space without logging out and back in.

---

### Post by exanime on 2011-11-02
Running the following script will clean the spaces.... it may be useful if you do not want to log out and back in... it is faster too


#!/bin/bash

killall lxpanel
find ~/.cache/menus -name '*' -type f -print0 | xargs -0 rm
lxpanel -p Lubuntu &

Tested on lubuntu 11.10

---

### Post by edison23 on 2011-11-04
hi, i had the exactly same problem and the script helped.. thanks a lot ;)

---

### Post by loganrah on 2011-11-05
I'm having exactly the same problem in lubuntu 11.10 
The script above seems to work but I'm new to lubuntu and only know how to run it through a terminal so as soon as i close the terminal the lxpanel disappears. How should i run the script so that i don't have to keep the terminal open? and is there a way to have it run automatically at start up and/or when waking from sleep?

---

### Post by hoppipolla on 2011-11-13
> **exanime said:**
> Running the following script will clean the spaces.... it may be useful if you do not want to log out and back in... it is faster too


#!/bin/bash

killall lxpanel
find ~/.cache/menus -name '*' -type f -print0 | xargs -0 rm
lxpanel -p Lubuntu &

Tested on lubuntu 11.10

hm, that worked but as soon as I logged out and logged back in the problem came back, I'm assuming because that command only removed things in the cache.

So... what ARE these rogue entries and how can we remove them permanently? o.O

---

### Post by swatson on 2011-12-03
Giving this a gentle bump - as still seeing the issue in 11.10. Does anyone know if it has been raised as a bug in Launchpad?

Cheers,

Simon

---

### Post by erchinoald on 2011-12-08
Also have this in Lubuntu 11.10 on a Samsung NC10 - waking from suspend adds empty spaces between my volume and wireless tray icons, which only disappear following reboot. Any permanent fixes?

EDIT: apologies for bump, just found this thread which is more specific to this issue: [http://ubuntuforums.org/showthread.php?t=1869357](http://ubuntuforums.org/showthread.php?t=1869357)

---

### Post by ogilvierothchild on 2012-02-15
Here is my work-around
[http://ubuntuforums.org/showthread.php?p=11690707#post11690707](http://ubuntuforums.org/showthread.php?p=11690707#post11690707)

---

### Post by cashmank on 2012-05-01
> **ogilvierothchild said:**
> Here is my work-around
[http://ubuntuforums.org/showthread.php?p=11690707#post11690707](http://ubuntuforums.org/showthread.php?p=11690707#post11690707)

I'm not seeing the "lxpanel reset" program in menu at all. Any idea what went wrong?

---

### Post by ethanay on 2013-04-12
I had this problem with Lubuntu 12.04:  no system tray icons were visible (specifically the Network Manager nm-applet icon).   I tried all sorts of suggestions.  Finally, I discovered that changing the panel position to the top caused the system tray icons to reappear.  Changing the panel back to the bottom caused them to disappear.  Increasing the panel thickness past 48 caused the icon to start reappearing.   It's position when the panel was at the bottom was messed up.

My final solution was to change the monitor's resolution from its default down to 1280x800, and the system tray icons reappeared.  I changed the resolution back to default, and the icons stayed visible!

---

