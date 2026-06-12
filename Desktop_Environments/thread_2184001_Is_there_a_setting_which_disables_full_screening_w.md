---
title: "Is there a setting which disables full screening when top borders are doubleclicked?"
date: 2013-10-27
forum: Desktop Environments
---

### Post by Jim_Granite on 2013-10-27
Is there a setting which disables full screening when top borders are doubleclicked in non-maximized windows?

Why?
For reasons stated elsewhere, full-screen windows in Unity are problematic, so, in an attempt to disallow any full-screen windows in Ubuntu 13.10, I'm seeking a way to prevent accidental full screening of a window when its top border is doubleclicked.
[ATTACH=CONFIG]247300[/ATTACH]

---

### Post by mc4man on 2013-10-27
Limited options - 
```
 gsettings set org.gnome.desktop.wm.preferences action-double-click-titlebar none
```

or (which may work fast or a bit slow depending on system
```
 gsettings set org.gnome.desktop.wm.preferences action-double-click-titlebar 'toggle-shade'
```

or what could max but not into panel (seems a bit inconsistent here, but maybe best fit for you

```
gsettings set org.gnome.desktop.wm.preferences action-double-click-titlebar 'toggle-maximize-vertically'
```

Possible values are seen by - 
```
gsettings range  org.gnome.desktop.wm.preferences action-double-click-titlebar
```

---

### Post by mc4man on 2013-10-27
Forget the toggle-max... it doesn't max into panel initially here, but after a log out/in it will

---

### Post by Jim_Granite on 2013-10-29
To update this thread, I'm starting to get used to resizing a window when it first opens, to just under full screen.
Luckily, most subsequent windows seem to follow suit. 
When a windows DOES open up full screen, what I've learned is that simply doubleclicking on the top border puts it back at less than full size in that case.
So, the use model isn't all that bad. 

It would be best if the window-control location bug didn't exist, but, with respect to full-size windows, the workaround is just to manually resize to less than fullsize, and then to doubleclick on the top border of any window that still comes up full sized.

This keeps the window controls where they belong (mostly).

---

### Post by Jim_Granite on 2013-11-05
> **Jim_Granite said:**
> This keeps the window controls where they belong (mostly).

Since I have a manual workaround, which is clearly not a solution, but, which means I've abandoned all further attempts to solve the problem, do we have a way of marking this task "abandoned"?

---

