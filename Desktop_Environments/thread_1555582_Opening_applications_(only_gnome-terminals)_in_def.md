---
title: "Opening applications (only gnome-terminals) in defined workspace"
date: 2010-08-18
forum: Desktop Environments
---

### Post by konrad_f on 2010-08-18
Ideally I would like to set a keyboard shortcut to open a set of applications. The applications (mainly different gnome-terminals) should be opened in different, previously defined workspaces. I had a look around but could not find a simple solution (maybe it could be done in devilspie but I would like to avoid that).

If I limit myself only to gnome-terminal and instead of using the keyboard shortcuts call the application in the shell the placement of the terminal can be done by using "--geometry"  (see "man gnome-terminal" and "man X") e.g.  "gnome-terminal --geometry 50x20+200+300". wmcrtl show me that my 6 workspaces are treated as one desktop (my interpretation - maybe wrong):

```
$ wmctrl -d
0  * DG: 7680x1024  VP: 0,0  WA: 0,1 1280x1023  Desk 1
```So I assumed I could place the terminal by using the parameter like this

```
$ gnome-terminal --geometry 50x20+1500+0
```which should move the terminal to the next working space. Unfortunately it does not work and the terminal cannot be started beyond the borders of the current workspace.

Any proposal how to solve this? Many thanks in advance.

Konrad ;)

---

### Post by mcduck on 2010-08-18
Are you using Compiz? If you are, you can simply define the desired locations & workspaces for each app in the "Place Windows"-plugin's options.

And to make it work for multiple terminals you can create many terminal profiles, define a different window title for each profile (make sure you set it to always keep that title), and then use the window title to distinguish the different terminals in the "Place Windows"-plugin.

---

### Post by konrad_f on 2010-08-18
Yay, works like a charm! :p I just had to install the CompizConfig Settings Manager (ccsm) first. Many thanks, mcduck.

---

