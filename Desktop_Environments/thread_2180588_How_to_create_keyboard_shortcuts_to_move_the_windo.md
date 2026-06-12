---
title: "How to create keyboard shortcuts to move the window to the center of the desktop?"
date: 2013-10-13
forum: Desktop Environments
---

### Post by thienthanh on 2013-10-13
Please help me how to create keyboard shortcuts to move the focused window to the center of the desktop!


Thanks in advance

---

### Post by Toz on 2013-10-20
Hello and welcome to the forums.

To use the following script, you need to have the package **xdotool** installed. Look for it in the Software Centre or install it manually via:
```
sudo apt-get install xdotool
```



Once thats done, with root privlidges, create the file /usr/local/bin/cw (from a terminal window):
```
sudo -i mousepad /usr/local/bin/cw
```
...or if you have an earlier version of Xubuntu with leafpad:
```
sudo -i leafpad /usr/local/bin/cw
```
...enter your password when prompted then copy/paste the following:
```
#!/bin/bash

PANEL_HEIGHTS=0
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
...and save the file.

Next, make the file executable via:
```
sudo chmod +x /usr/local/bin/cw
```

You can now test the script by opening a terminal window, moving it away from centre, then executing the command:
```
cw
```
...and the window should centre. 

The script acts on the currently focused window, so by adding it to a keyboard shortcut, it will act on whichever window is currently active. To create a keyboard shortcut in Xfce, go to Settings Manager -> Keyboard -> Application Shortcuts, click on the "Add" button, for the command enter:
```
/usr/local/bin/cw
```
...press "Ok" then press the keyboard combination you want to use.



Note: The script includes two variables:
> PANEL_HEIGHTS=0
PANEL_WIDTHS=0
Feel free to adjust these by giving them the values (in pixels) of the total widths/heights of your panels if you want the window to centre relative to the panels (not screen dimensions).

---

### Post by thienthanh on 2013-10-23
Amazing! Thank you very much

---

