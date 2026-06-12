---
title: "Panel shortcut to minimize active window; resize / move windows with right mouse drag"
date: 2008-05-05
forum: Desktop Environments
---

### Post by Ferdil on 2008-05-05
I am trying to build a very customized interface. I am a great fan of global menus and window buttons, because I think they're fast and comfortable.

I already managed to make the mac-style menu work (global menu, search on google), but I also wanted to have global close / maximize / minimize buttons.
I managed to add the close and maximize buttons, installing wmctrl and creating launchers with the following commands:

Close
```
wmctrl -c :ACTIVE:
```

Maximize/Restore
```
wmctrl -r :ACTIVE: -b toggle,maximized_vert,maximized_horz
```

The problem is that wmctrl doesn't seem to support minimizing of the active window. Do you know a program and/or command to make it work?


Another thing that I'm trying to do is to enable window moving and resizing by dragging only the right mouse button. (I know this can be done with alt+leftclick and alt+middleclick, but that's not what I want), but I don't know if something like this is possible.


I use Compiz as the default Window Manager.

---

### Post by Ferdil on 2008-05-08
I found a way to minimize from a launcher, but I still want to know if there's a way to move windows by dragging the right mouse button.

Also, do you know any terminal programs/commands that give in output the name of the active window?

---

### Post by Dirjel on 2009-02-18
Could you explain how you were able to minimize a window from a launcher?  Was that still in compiz, or did you have to use a different window manager?

---

### Post by zhocchao on 2009-02-18
This gives you the ID of the active Window:

xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)" |awk '{print $5}'|sed 's/0x/0x0/g'

I dont't know why, but I had to make this to have it working in a Bash script:

a=$(xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)" ) 
akt=$(echo $a |awk '{print $5}'|sed 's/0x/0x0/g')


Moving windows could be done with xbindkeys. Assign alt+leftclick to right mouse button. Don't know if that works, but if I would try that way.

---

