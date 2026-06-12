---
title: "Keyboard shortcuts for snap left, snap right"
date: 2011-11-08
forum: Desktop Environments
---

### Post by neotaruntius on 2011-11-08
Hi all

I am currently working on Ubuntu 11.10 and am enjoying the following amazing keyboard shortcuts - 
 ctrl + alt + kp 4 (snap left)
 ctrl + alt + kp 6 (snap right)
 ctrl + alt + kp 5 (maximize)
* kp = keypad

You can use these shortcuts for other numbers too.

However, yesterday, I tried out the Gnome interface and it is very interesting too. Now, I would like to move over to gnome, however these keyboard shortcuts don't work over there. I know the snapping feature is there to use, because if I use my mouse to drag the window to the left edge, it snaps and takes up half of the monitor on the left.

Can someone please help me find/configure they keyboard shortcuts for snapping windows left and right using the above combinations  in ubuntu 11.10 gnome?

(I have been to keyboard shortcuts, and couldn't find anything relevant)

Thanks for all your help guys!! Stay awesome.

---

### Post by bhatbhai on 2011-11-30
Got the same problem as you, man.

[http://ubuntuforums.org/showthread.php?p=11502288#post11502288](http://ubuntuforums.org/showthread.php?p=11502288#post11502288)

Any help would be awesome.

---

### Post by Bufke on 2011-12-01
I assume you're talking about using gnome-shell which doesn't use compiz so therefore you can't use grid which is what does the snapping so nicely.

There is an imperfect way to do it. First install wmctrl
then make a script like this and call it snapleft.sh or whatever really.

```
#!/bin/bash
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x' `
HALF=$(($WIDTH/2))
wmctrl -r :ACTIVE: -b remove,maximized_horz,fullscreen
wmctrl -r :ACTIVE: -b add,maximized_vert
wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-1

```

For snapright.sh
```
#!/bin/bash
WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x' `
HALF=$(($WIDTH/2))
wmctrl -r :ACTIVE: -b remove,maximized_horz,fullscreen
wmctrl -r :ACTIVE: -b add,maximized_vert
wmctrl -r :ACTIVE: -e 0,$HALF,0,$HALF,-1

```

Now you can assign the script to a keyboard shortcut in gnome keyboard settings. 

However it's not nearly as nice as grid. You'd really have to take time scripting it to all the different locations grid can do. Also the keyboard shortcuts on numpad don't work in gnome-shell! So you can't have it ctrl-alt-kp4. There is a [bug]("https://bugzilla.gnome.org/show_bug.cgi?id=664219") reported and they even mention window management so keep your fingers crossed for gnome 3.4.

---

