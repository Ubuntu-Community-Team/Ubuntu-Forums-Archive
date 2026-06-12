---
title: "in beryl windows from all workspaces appear in window list bar"
date: 2007-04-30
forum: Desktop Effects &amp; Customization
---

### Post by dr.silly on 2007-04-30
If I have a program in any workspace it appears on the bottom bar of all workspaces. Is this a flaw? If not how do I change?

I did go into window list preferences and check that but no luck.

---

### Post by john.nicholls on 2007-04-30
That appears to be the default behaviour. I don't know how you'd change it.

---

### Post by dr.silly on 2007-05-01
kinda makes the workspaces useless then doesn't it?

---

### Post by rolf-c on 2007-05-01
I only have this behavior when I am using the cube view.

---

### Post by dr.silly on 2007-05-01
I have it all the time

---

### Post by serialdae on 2007-05-01
Are you using KDE?

I could not find a good way around that in KDE and have converted to Gnome.

---

### Post by rolf-c on 2007-05-01
Looks like this is a bug and has been reported to the beryl team per their problem tracker at [http://bugs.beryl-project.org/ticket/1556](http://bugs.beryl-project.org/ticket/1556)

> Ticket #1556 (new Bug)

Opened 2 months ago
The 3D cube doesn't show correctly the process bar
Reported by: 	wam1791 	Assigned to: 	core-team
Priority: 	normal 	Milestone: 	0.2.0
Component: 	beryl-core 	Version: 	0.2.0-svn
Severity: 	Normal 	Keywords: 	
Cc: 		Status: 	Queued
Description ¶

When changing the desktop using the 3D-cube (with the mouse) all cube faces share the same process bar. So, even you're actually looking another cube side (another desktop) with only one window inside, its process bar show all the process you had in your current desktop (before changing).

---

### Post by dr.silly on 2007-05-02
I use gnome

and yep, that's precisely my problem

---

### Post by boom2k1 on 2007-08-17
yeah. the selection list on my taskbar always gets overcrowded with so many windows!!
does anyone know how to fix it?

I am using gnome too.

---

### Post by Dougle on 2007-08-19
I think:

Beryl uses virtual workspaces, using only one Gnome workspace.
You can set beryl to use the window manager's workspace system by checking General->Desktop Background->Desktop manager supports viewports

Gnome doesn't support this feature of beryl, only KDE does.

it sux, i'm looking for the same fix.

---

