---
title: "configuring icewm"
date: 2008-03-12
forum: Desktop Environments
---

### Post by shifty2 on 2008-03-12
Just trying to get icewm running properly and have a couple of questions:
I have seen that in order to get the gtk themes applied you should add "gnome-settings-daemon" to your start-up file. however, when trying to run "gnome-settings-daemon" i get this error:
```

** (gnome-settings-daemon:11188): WARNING **: Couldn't connect to session bus: Failed to connect to socket /tmp/dbus-ye8pToclwK: Connection refused

** (gnome-settings-daemon:11188): WARNING **: Could not get a connection to the bus

```

Also,
How do I set Icewm to use a proxy? or will loading the gnome settings demon solve that problem?

Cheers for any help

---

### Post by mocoloco on 2008-03-12
If you want to run it without Gnome you don't need gnome-settings-daemon.  There are a couple of hidden files that will do the trick for you, .gtkrc-2.0 and .gtkrc.mine.  To get you started download a little app called gtk-chtheme.  When you run it and choose a theme it will set up your .gtkrc-2.0 and you can take a look at it to see it's syntax.  The .gtkrc.mine is where you tell it what icon theme to use, so for example mine looks like this ```
gtk-icon-theme-name="Tango"
```

---

### Post by jseiser on 2008-03-12
instead of wasting yo ur resources on gnome, here is how i do it.

themes go into ~/.themes

**gtk2 themes**

 install gtk-chtheme, run program, select gtk2 theme.

**gtk1 themes**

install gtk-theme-switch package and launch with command "switch"

**for fonts**

f you want to change the type and size of your fonts, add the following to ~/.gtkrc.mine:

style "user-font"
{
font_name = "[font-name] [size]"
}
widget_class "*" style "user-font"
gtk-font-name = "[font-name] [size]"

where [font-name] [size] is the desired font and point size. For example:

style "user-font"
{
font_name = "DejaVu Sans 8"
}
widget_class "*" style "user-font"
gtk-font-name = "DejaVu Sans 8"

Both font_name and gtk-font-name fields are required for backwards compatibility. 


**for icons**

Extract the desired icon theme to /usr/share/icons (system-wide access) or ~/.icons (local user access).

Add the following to ~/.gtkrc.mine:

gtk-icon-theme-name = "[name-of-icon-theme]"

where [name-of-icon-theme] is the name of the icon theme directory. For example:

gtk-icon-theme-name = "Tango"
[B]
Mouse cursor themes[/B]

Extract the desired Xcursor theme to either /usr/share/icons (system-wide access) or ~/.icons (local user access).

Add this to ~/.Xdefaults:

Xcursor.theme:   [name-of-cursor-theme]

where [name-of-cursor-theme] is the name of the cursor theme directory. For example:

Xcursor.theme:	Vanilla-DMZ-AA



sry mocoloco got in b4 me :)

---

### Post by shifty2 on 2008-03-12
Yep I had just noticed that after doing a bit more googling - now its all nicely themed.

Hmm I think I'm going to have issues using epiphany as my browser, since it displays the same error as above, any other good lightweight browsers?

---

### Post by shifty2 on 2008-03-12
Just one more question:
How do I change my keyboard layout? At the moment it is stuck on us and I want it to be "gb". I have tried reconfiguring xorg but to no avail. 

Using midori as my browser, working well and everything is running very quickly :-) cheers for the help so far

---

