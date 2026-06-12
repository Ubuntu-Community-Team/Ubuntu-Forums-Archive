---
title: "Bash command for Maximizing and Unmaximizing windows in gnome?"
date: 2009-04-13
forum: Desktop Environments
---

### Post by carlosandcamy on 2009-04-13
Hello,

Does anyone know the bash command to Maximize and Unmaximize windows in the gnome desktop environment?  

I want to designate my upper right corner of my touchpad to Maximize and Unmaximize windows.  I found the synaptics driver command to activate the upper right corner of the touchpad.  I am hoping that I can somehow tie an event to the RTCornerButton button option in the xorg.conf file.  

According to what I found on the internet that command has 12 possible options, the first three just emulate a left, right, or middle button cliks.  The remainder of the options don't do anything that is obvious to me.  I am hoping I can designate the 4th option in the RTCornerButton to bash a command to maximize or unmaximize a window.

Thanks in advance for any kind of help,

Carlos

---

### Post by crazy ivan on 2011-02-12
I would be bolder and ask this question for X in general..

I've been fiddling around with

xdotool
xprop
wmctrl

but no luck! I need this feature badly, because else maximus makes windows unusable, when I switch it off.

When trying xdotool, windows will receive alt+F5, but just interpret it as keys.. Window commands are ignored. Xprop returns

```

xprop -id 0x200007
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  21 (X_ListProperties)
  Resource id in failed request:  0x200007
  Serial number of failed request:  11
  Current serial number in output stream:  11

``` 

for any window. And wmctrl seems to be lacking such features.

I know it can be acessed via the window class for GNOME [http://library.gnome.org/devel/gtk/unstable/GtkWindow.html]("http://library.gnome.org/devel/gtk/unstable/GtkWindow.html") [http://www.pygtk.org/docs/pygtk/class-gtkwindow.html](http://www.pygtk.org/docs/pygtk/class-gtkwindow.html). BUt there ought to be some command line way to do it.

---

### Post by mcduck on 2011-02-12
*wmctrl* is the tool you are looking for... :)

[http://linux.die.net/man/1/wmctrl]("http://linux.die.net/man/1/wmctrl")

---

### Post by Krytarik on 2011-02-13
Specifically he will mean a command like this:
```
wmctrl -i -r 0x200007 -b toggle,maximized_vert,maximized_horz
```
Of course you would have to determine the id before, I recommend "xwininfo" for that:
```
winid=`xwininfo -name NAME |grep 'Window id:' |cut -d" " -f4`
wmctrl -i -a "$winid"

```
Or use its name instead with wmctrl, but that only works correct if there is no other window which also contains the string in its name, wmctrl doesn't even handle the case.

I had to do the upper workaround for MPlayer and mplayerTV. ;-)

---

### Post by stinkeye on 2011-02-13
To toggle the focused window maximized/unmaximized...
```
wmctrl -r :ACTIVE: -b toggle,maximized_vert,maximized_horz
```
...and I find the best way to use it is with easystroke mouse gestures
because performing the gesture on a window brings it into focus.

---

### Post by crazy ivan on 2011-02-15
Thanks guys, that's pretty cool stuff, even though the search function is better implemented in xdotool. Thanks for the cut code.

I used "wmctrl -k" to show the desktop in another script, never thought to go further. Anyhow, my problems with maximus have been somewhat sorted out since I found the gconf entries 

"/apps/maximus/undecorate" to work with it on dual screens and 

"/apps/metacity/window_keybindings/toggle_fullscreen" and 

"/apps/metacity/window_keybindings/toggle_maximized" 

to repair the "damage" it has done to some apps (guess calling these shortcuts amounts to calling wmctrl). 

Bound "toggle_maximzed" to "<Super>F5" and "toggle_fullscreen" to "<Super>F11" now, and thus rescued mozilla thunderbird and Openoffice out of unintended fullscreen created by maximus.

---

### Post by crazy ivan on 2011-03-12
Thanks again Krytarik and stinkeye. With these commands, I managed to write a little script that shows the time in a notification box, disabling the fullscreen of mypaint which usually runs as a notepad on my tablet's screen blocking the notifications:

```

#!/bin/sh
date_time="`date | cut -d' ' -f1,2,3,4`"
wmctrl -r MyPaint -b remove,fullscreen
notify-send "$date_time"
sleep 5
wmctrl -r MyPaint -b add,fullscreen

```
Not quite perefect, since it does not hide the menu, as it does when I press F11. Don't think wmctrl can acess this property though..

Also I added "wmctrl -r :ACTIVE: -b toggle,maximized_vert,maximized_horz" and "wmctrl -r :ACTIVE: -b toggle,fullscreen" to easystroke gestures :)

---

### Post by Krytarik on 2011-03-12
You could also simply pass the option "-u critical" to notify-send to show the notification even while in fullscreen. :p
```
notify-send -u critical "`date | cut -d' ' -f1,2,3,4`"
```

---

### Post by crazy ivan on 2011-03-13
thx! works even better.. :D

---

### Post by crazy ivan on 2011-03-18
And thanks for the 
```
 winid=`xwininfo -name NAME |grep 'Window id:' |cut -d" " -f4` 
```
line. I ran into 
```
 wmctrl -r -c NAME 
```
not shutting down the programs at all **.

Now I use 
```

winid=`xwininfo -name NAME |grep 'Window id:' |cut -d" " -f4`
wmctrl -i -c "$winid"

``` for most programs..
For some I had to try harder and got the line (with the modification "wminfo -root -tree" it is somewhat similar to "ps aux" for WIDs instead of PIDs) 
```

xwininfo -root -tree 2>/dev/null | grep NAME | awk '{print $1}'

```
from chewearn [http://blog.chewearn.com/2010/01/18/find-window-id-of-a-process-id-in-bash-script/]("http://blog.chewearn.com/2010/01/18/find-window-id-of-a-process-id-in-bash-script/"). Now I can also make gedit, eclipse, inkscape and referencer ask me if I want to save before quitting trough the command line:

```

$app=" gedit"
wmctrl -i -c `xwininfo -root -tree 2>/dev/null | grep "$app" | awk '{print $1}'`

```
Note the odd " gedit" string to distinguish it from the parent processes.

** By the way, can one get any output from that wmctrl.. I mean they have "-v Provide verbose output. This is really useful when debugging wmctrl itself." which does nothing. Its somehow unsatisfying that it does not show any response to wrong input...

---

### Post by Krytarik on 2011-03-18
LOL:p  The correct command would be like this, without the "-r" option:
```
wmctrl -c gedit
```
And yes, I also don't get any error messages from wmctrl, in fact somewhat annoying!

---

