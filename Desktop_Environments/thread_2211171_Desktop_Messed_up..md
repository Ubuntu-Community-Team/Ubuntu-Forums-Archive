---
title: "Desktop Messed up."
date: 2014-03-14
forum: Desktop Environments
---

### Post by william27 on 2014-03-14
I have somehow messed up my desktop theme.
[IMG]http://i.imgur.com/DszmMSn.png[/IMG]
Now, The default Xubuntu theme would be nice!
I've tried removing the xfce4 folder and relogging, but with no avil.

---

### Post by ajgreeny on 2014-03-14
I don't really understand what it is you're complaining about.  What version of Xubuntu are you using.  Your Desktop background image appears to be one of the defaults available, but you can change that or add any other image you want by right clicking on the desktop and navigating to the picture you would like to use.

If you don't like the Icon label backgrounds showing in grey, as they are in your screenshot, copy the txt I have attached into a file in your home and rename the file .gtkrc-2.0 (note the . at the start of the filename)

You can also change other settings by going to the main menu (top left in your pic) and Settings-Manager ->Appearance, and choose a different theme, and then to Window-Manager and play around as much as you want to get it looking how you want.
```
# This file should be placed in your xubuntu home folder
# and name ".gtkrc-2.0"
#
gtk-menu-popup-delay=0
gtk-menu-popdown-delay = 0
gtk-menu-bar-popup-delay = 0
gtk-enable-animations = 0
gtk-timeout-expand = 10
#---------------------------------------------------------------
# Section "icon background colors"
#---------------------------------------------------------------
# The following two lines *should* be left uncommented
# if we want the XFCE desktop icon backgrounds to use
# alpha blending (e.g. invisible or some % thereof)
#
style "xfdesktop-icon-view" {
XfdesktopIconView::label-alpha = 0
XfdesktopIconView::selected-label-alpha = 0
XfdesktopIconView::active-label-alpha = 0
#
#---------------------------------------------------------------
# Section "icon font colors"
#---------------------------------------------------------------
#
# The next three lines deal with the color of the desktop icon's
# text. You can comment them out if you want you use gtk theme
# colors. Below yields white un-selected normal, green selected,
# and blue when going to another window
#
# I chose three different colors so that you can see the level
# of customization we can do.
#
fg[NORMAL] = "#ffffff"        #this is white
fg[SELECTED] = "#00ff00"      # this is green
fg[ACTIVE] = "#ff0000"        # this is red
#
## my blue fonts to use with nuvola theme & royal blue WM
# environment. a soft shark underbelly blue color if you will.
#fg[NORMAL] = "#528AC6"
#fg[SELECTED] = "#528AC6"
#fg[ACTIVE] = "#528AC6"
#
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"


```

---

