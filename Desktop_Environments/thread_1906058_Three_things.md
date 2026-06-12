---
title: "Three things"
date: 2012-01-08
forum: Desktop Environments
---

### Post by mandarke on 2012-01-08
Is it possible to:

- bind windows key + c to have the currently selected window centre itself
- have parole resize itself to the size of the video being played
- configure the focus so that I can have a web browser open in the background, mplayer in the foreground, and still be able to scroll the web page I have open without the web browser stealing focus

If so, how?

---

### Post by wkrekik on 2012-01-08
I think that wmctrl can do that, but it needs some configuration knowledge. To install  wmctrl :
```
sudo apt-get install wmctrl 
```

---

### Post by BobMarleyy on 2012-01-08
> **mandarke said:**
> 
- configure the focus so that I can have a web browser open in the background, mplayer in the foreground, and still be able to scroll the web page I have open without the web browser stealing focus

If so, how?

Go to settings manager -> window manager -> focus and check your "raise on click" setting, you probably want to turn this feature off.

---

### Post by Toz on 2012-01-08
> **mandarke said:**
> Is it possible to:

- bind windows key + c to have the currently selected window centre itself

Install xdotool, then use this script:
```

#!/bin/bash

PANEL_HEIGHTS=24
PANEL_WIDTHS=0

SCREEN_WIDTH=`xdotool getdisplaygeometry | cut -d' ' -f1`
SCREEN_HEIGHT=`xdotool getdisplaygeometry | cut -d' ' -f2`

ACTIVE_WINDOW_ID=`xdotool getactivewindow`

ACTIVE_WINDOW_WIDTH=`xwininfo -id $ACTIVE_WINDOW_ID | grep Width | cut -d' ' -f4`
ACTIVE_WINDOW_HEIGHT=`xwininfo -id $ACTIVE_WINDOW_ID | grep Height | cut -d' ' -f4`

xpos=$((($SCREEN_WIDTH-$PANEL_WIDTHS-$ACTIVE_WINDOW_WIDTH)/2))
ypos=$((($SCREEN_HEIGHT-$PANEL_HEIGHTS-$ACTIVE_WINDOW_HEIGHT)/2))

xdotool windowmove $ACTIVE_WINDOW_ID $xpos $ypos

```

Make sure to adjust the values of PANEL_HEIGHTS and PANEL_WIDTHS to the size of the panels that don't allow windows to go over them (struts enabled by default). 

Assign this script to your hotkey at Settings->Settings Manager->Keyboard->Application Shortcuts.

---

### Post by mandarke on 2012-01-08
> **BobMarleyy said:**
> Go to settings manager -> window manager -> focus and check your "raise on click" setting, you probably want to turn this feature off.

doesn't work exactly how i'd like, but it is a start. an example of what i am after is having a web browser maximised with wireshark in the foreground but i am still able to have some interaction (ctrl-click links, scroll up and down pages) with the web browser. as soon as i have the data i'm after from wireshark, i click on the web browser and it has full focus again with wireshark relegated to the background. this worked a treat in ubuntu 10.10.

---

### Post by mandarke on 2012-01-08
> **wkrekik said:**
> I think that wmctrl can do that, but it needs some configuration knowledge.

> **Toz said:**
> Install xdotool

looks like other than the placement tab in the window manager tweaks there isn't an easy way to achieve what i'm after in xfce.

---

### Post by Toz on 2012-01-08
Did you try the script in post #4? It will centre the active window on your screen.

---

### Post by mandarke on 2012-01-09
> **Toz said:**
> Did you try the script in post #4? It will centre the active window on your screen.

i'm trying to avoid installing little things so there is less to go wrong.

---

