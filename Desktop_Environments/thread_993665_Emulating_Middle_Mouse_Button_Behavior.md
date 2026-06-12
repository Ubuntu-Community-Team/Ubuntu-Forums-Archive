---
title: "Emulating Middle Mouse Button Behavior"
date: 2008-11-26
forum: Desktop Environments
---

### Post by MooseBoys on 2008-11-26
Hey all I'm new here (and new to Ubuntu, relatively new to linux as well).  I've got 8.10 installed on my laptop, and my touchpad doesn't have a middle mouse button.  One of the apps I use frequently requires middle mouse button dragging (not just clicking), so I was wondering if anyone had any suggestions on how to emulate this using a control key (eg. Windows Key + LMB = MMB).

Thanks all.


edit: I realize that RMB->LMB = MMB, however my touchpad is somewhat worn to say the least, and doing this usually results in awful things.  It would be nice to have a more reliable solution.

---

### Post by Super Jamie on 2008-11-29
I have done the same on my laptop, here's the full description of how i did it:
[http://linuxaleph.blogspot.com/2008/11/mapping-middle-click-to-keyboard-key.html](http://linuxaleph.blogspot.com/2008/11/mapping-middle-click-to-keyboard-key.html)

basically, **sudo apt-get install xkbset**, edit the file **/usr/share/X11/xkb/compat/mousekeys** and remove everything between **interpret.repeat= False;** and **// New Keysym Actions**, then use Preferences - Sessions to autostart a script like this as you login:

```
#!/bin/bash
# set XKB layout
setxkbmap -layout us
# turn on mousekeys
xkbset m
# stop mousekeys expiring after a timeout
xkbset exp =m
# map keysym to other keysym
xmodmap -e "keysym Menu = Pointer_Button2"
# this also works
# xmodmap -e "keycode 135 = Pointer_Button2"
```

use **xev** to find the keycode if you don't want to use the Menu button

---

### Post by P4man on 2009-10-23
Hi super jamie. That tip actually (finally) enables me to reassign my search key as a middle mouse button. However, since it relies on mousekeys, it also disables my numeric keypad. Do you have any solution for that?

---

### Post by kanikilu on 2009-10-23
Other people reported the same behavior in this huge thread on the MX Revolution:

[http://ubuntuforums.org/showpost.php?p=1861141](http://ubuntuforums.org/showpost.php?p=1861141)

Someone posted an alternative solution that doesn't use mousekeys:

[http://ubuntuforums.org/showpost.php?p=1861141&postcount=33](http://ubuntuforums.org/showpost.php?p=1861141&postcount=33)

It's several years old, though, so I don't know if it still works.

There are also other suggestions in that thread, such as mapping the middle mouse function to the left thumb wheel...

---

