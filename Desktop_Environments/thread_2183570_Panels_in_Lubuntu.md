---
title: "Panels in Lubuntu"
date: 2013-10-25
forum: Desktop Environments
---

### Post by SoftLAN on 2013-10-25
I upgrade to Lubuntu 13.10 recently and it went great but something happened to my screen and system tray. 

As for the system tray, it is not there anymore. It is gone. No clock, no calendar.
And second, text seem to go outside of screen. I haven't changed any of the screen settings recently.

I tried to update a config file, ~/.config/lxpanel/<Profile>/panels and pasted this text:

```
# lxpanel <profile> config file. Manually editing is not recommended.
# Use preference dialog in lxpanel to adjust config when you can.

# Global section: defines appearance and behavior of this panel.
Global {
    edge=bottom    # The edge this panel attaches to
    allign=left    # alignment: left/center/right
    margin=0       # margin: margin to the edge of the whole screen
    widthtype=percent   # percent/pixel
    width=100      # width of the panel: The unit used here is according to widthtype.
    height=26      # height of the panel
    transparent=0  # use (pseudo-)transparent background: on=1, off=0
    tintcolor=#000000  # color blended with the backgroud when transparency is used.
    alpha=0    # alpha value used to blend tintcolor with background.
    setdocktype=1   # ask the window manager to treat the panel as a dock.
    setpartialstrut=1  # ask the window manager to reserve the space for the panel and not to cover it with maximized windows
    usefontcolor=1   # use customize colors for the text instead of that defined in system theme.
    fontcolor=#ffffff   # color of text on the panel (Currently this is only supported by clock applet)
    background=1    # use customize image to draw the background of the panel. (cannot be used with transparent)
    backgroundfile=/usr/share/lxpanel/images/background.png  # The image file used.
}


# Configuration of various applets
# Basic syntax:
# Plugin {
#   type=<plugin type>
#   expand=0    (optional, mainly used in "taskbar" and "space" applets.
#                expand=1 will stretch the applet to fill all available spaces)
#   Config {
#     ...
#   }
# }


Plugin {
    type = space
    Config {
        Size=2
    }
}

Plugin {
    type = menu
    Config {
        # image must be set
        image=/usr/share/lxpanel/images/my-computer.png
        # name is optional
        # it may be set to the name of a *.directory file in /usr/share/desktop-directories to get a localised label
        # eg. name=lxde-menu-applications.directory
        name=Label
        # tint may be set to an X11 colour name or a hex value,
        # see http://library.gnome.org/devel/gdk/unstable/gdk-Colormaps-and-Colors.html#gdk-color-parse
        # The default is blue; black disables tinting.
        tint=red
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
            id=pcmanfm.desktop
        }
        Button {
            id=gnome-terminal.desktop
        }
        Button {
            id=firefox.desktop
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
        Button1=iconify
        Button2=shade
    }
}

Plugin {
    type = space
    Config {
        Size=4
    }
}

Plugin {
    type = pager
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
        AcceptSkipPager=1
        ShowIconified=1
        ShowMapped=1
        ShowAllDesks=0
        UseMouseWheel=1
        UseUrgencyHint=1
        FlatButton=0
        MaxTaskWidth=150
        spacing=1
    }
}

Plugin {
    type = netstat
}

Plugin {
    type = cpu
}

Plugin {
    type = tray
}

Plugin {
    type = dclock
    Config {
        ClockFmt=%R
        TooltipFmt=%A %x
        BoldFont=0
    }
}

```
but no success. I read this page, [http://wiki.lxde.org/en/LXPanel](http://wiki.lxde.org/en/LXPanel)

Help please!

Thanks.

---

### Post by Dennis N on 2013-10-25
This should reset the panel to original state:

```
lxpanelctl restart
```

---

### Post by SoftLAN on 2013-10-25
Thanks, but I tried that before and I tried that again just now. Didn't work. Any other suggestions?

---

### Post by SoftLAN on 2013-10-26
Is it better to just reinstall Lubuntu? I'd rather not do that.

---

### Post by LuvLinuxOS on 2013-10-26
Have you tried copying ~/.config/lxpanel/*.* from the live cd to your ~/.config/lxpanel/?  I lost my entire display and I did something similar to avoid reinstall.  I copied /etc/X11 from the live cd to my hdd corrected all of my display errors.  you will have to do something like the following
1. boot from the live cd
2. mount your hdd
3. open LXTerminal
4. sudo su
5. delete the contents of ~/.config/lxpanel/ -- "rm -rf ~/.config/lxpanel/ on your hdd so it will be in /media/your hdd UID/home/yourlogin/.config/lxpanel
6. copy the contents of the live cd ~/.config/lxpanel/ to your hdd home directory
7. reboot it should not hurt anything and it is worth a try.

[> ~LuvLinuxOS~]("http://luvlinuxos.blogspot.com")

---

### Post by SoftLAN on 2013-10-29
LuvLinuxOS

Thanks for your suggestion. I decided to reinstall the whole thing. It's not such a big problem since I mainly use Chromium and the terminal

---

### Post by walterorlin on 2013-10-29
A note for others if you can configure the panel using the gui through right clicking on it.

---

