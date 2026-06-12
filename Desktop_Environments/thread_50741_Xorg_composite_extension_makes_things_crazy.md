---
title: "Xorg composite extension makes things crazy"
date: 2005-07-21
forum: Desktop Environments
---

### Post by alegomes on 2005-07-21
When I turn on composite extension at /etc/X11/xorg.conf with

```

Section "Extensions"
        Option "Composite" "On"
EndSection 
```

some behaviors get changed. For example:

1) The gnome bars (up and bottom) lost its "always visible" property.

2) Click on System > Exit halts all the Ubuntu box.

Is it caused by the experimental state of composite extension or there is a way to work around it ?

thanks

---

### Post by frodon on 2005-07-21
[QUOTE=alegomes]1) The gnome bars (up and bottom) lost its "always visible" property.

2) Click on System > Exit halts all the Ubuntu box.

Is it caused by the experimental state of composite extension or there is a way to work around it ?

thanks[/QUOTE]
1) In order to solve that, go to System>Preferences>session and add xcompmgr command to be the first launched. A simple "killall gnome-panel" also do the job but only for this session.
2) I have the same behaviour, so i think it's a common bug. I just kill xcompmgr before using end session button
There is a lot of informations about it in this [thread](http://www.ubuntuforums.org/showthread.php?t=20769) .

---

### Post by Hobo Joe on 2007-08-17
I don't know if it will make a difference, but try changing 'on' to 'enable'.

Woah holy crap, i didn't realize I was bumping and old thread, my apolgies. D:

---

