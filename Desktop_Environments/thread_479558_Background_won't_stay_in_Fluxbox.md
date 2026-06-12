---
title: "Background won't stay in Fluxbox"
date: 2007-06-20
forum: Desktop Environments
---

### Post by Gadren on 2007-06-20
I'm using Fluxbox, and I'm having a problem.  When I start it up, the background I want appears, then, right as the toolbar appears, the background is replaced with a light blue background color (different from the default GDM color).  Running "fbsetbg -l" fixes it, but I want it to happen on startup.  Here is my startup file:

```

# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# You can set your favourite wallpaper here if you don't want
# to do it from your style.
#
#fbsetbg -f /home/gadren/pictures/wallpapers/SPACE_by_FalseBeauty.jpg &
#
# This sets a black background

#/usr/bin/fbsetroot -solid black

# This shows the fluxbox-splash-screen
# fbsetbg -C /usr/share/fluxbox/splash.jpg

# Other examples. Check man xset for details.
#
# Turn off beeps:
# xset -b
#
# Increase the keyboard repeat-rate:
# xset r rate 195 35
#
# Your own fonts-dir:
# xset +fp "/home/gadren/.fonts"
#
# Your favourite mouse cursor:
# xsetroot -cursor_name right_ptr
#
# Change your keymap:
# xmodmap "/home/gadren/.Xmodmap"



# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &

# GADREN'S ADDITIONS
tilda &
fbsetbg -l 
gnome-volume-manager &
xscreensaver -nosplash &

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec /usr/bin/fluxbox
# or if you want to keep a log:
# exec /usr/bin/fluxbox -log "/home/gadren/.fluxbox/log"

```

Tilda loads, but fbsetbg works only for a while.

---

### Post by Happy_Man on 2007-06-20
Maybe you should uncomment out that line up there, which has a file path.

---

### Post by RedSquirrel on 2007-06-20
> **Gadren said:**
> I'm using Fluxbox, and I'm having a problem.  When I start it up, the background I want appears, then, right as the toolbar appears, the background is replaced with a light blue background color (different from the default GDM color).  Running "fbsetbg -l" fixes it, but I want it to happen on startup. 

Create the file ~/.fluxbox/overlay and put this line in it:

```
background: none
```_**OR**_

Delete "fbsetbg -l" in your startup file and then edit your ~/.fluxbox/init file and change the line

```
session.screen0.rootCommand:
```to 

```
session.screen0.rootCommand: fbsetbg -l
```EDIT:

You also run the command in the background in your startup file:

```
fbsetbg -l **&**
```
EDIT #2:

Personally, I would use the overlay file. 

Some Fluxbox styles have a background that is set when you choose that style from your Fluxbox menu. 

When your desired background is set at startup and you subsequently choose one of those styles, it will apply _its own_ background if you don't use the overlay file. Using the overlay file will prevent this from happening so that your nice background is always there. :)

The overlay file is a way to specify your settings that will apply no matter what style you choose.

Here's mine:

```

# add rounded corners to the menu
#menu.roundCorners: TopRight TopLeft BottomRight BottomLeft

# add rounded corners to the windows
#window.roundCorners: TopRight TopLeft BottomRight BottomLeft

# add rounded corners to the toolbar (only applies to the top corners)
#toolbar.shaped: true

background: none
```If I want rounded corners, I can simply edit the overlay file and uncomment the relevant lines. This is much easier than editing the individual style files. ;)

---

### Post by Gadren on 2007-06-20
Thanks for the help -- I couldn't get the overlay to work, but the rootCommand did work.

---

### Post by RedSquirrel on 2007-06-23
It looks like the "background: none" setting in the overlay file was introduced in January of this year. The Fluxbox from the Ubuntu repositories is older than that. Oh well, the rootCommand is still a reasonable solution. :)

---

