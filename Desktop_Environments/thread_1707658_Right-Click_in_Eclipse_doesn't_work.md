---
title: "Right-Click in Eclipse doesn't work"
date: 2011-03-15
forum: Desktop Environments
---

### Post by alienjon on 2011-03-15
I haven't used Eclipse on my laptop for a few months now, but all of a sudden I can't seem to right click anywhere in the program.  The right mouse button still works for everything else (ie: in Firefox I can right click and the menu will appear).  In Eclipse, though, if I right click on a project name, it will select the project, but no menu will appear (even if it is currently open project).  This isn't how it used to act (nor is it, obviously, how is should act) but I'm not entirely sure what would have caused it.  In all likelihood there was a system update that I forgot about, but has anyone come across this problem before?

---

### Post by alienjon on 2011-03-19
Sorry to bump, but {bump}

---

### Post by ilCatania on 2012-06-01
Hi,

happened the same to me during the last hour. I'm on:

[LIST=1]
[*]  ubuntu precise
[*]unity
[*]intel graphics card
[*]logitech usb mouse
[*]dell latitude laptop
[*]Eclipse: Version: 3.7.2 Build id: M20120208-0800
[/LIST]
 
I'll add some details, hope it helps to diagnose the problem:

[LIST=1]
[*]when right clicking in eclipse, the context menu would not show up, but was in fact there: navigating up and down with the arrow keys and hitting enter would trigger the selected action (only you couldn't see which action you were selecting).
[*]after right clicking to bring up the context menu, and failing, the application menus (File, edit, etc) would also stop appearing. The same for context menu in other applications
[*]switching the ubuntu workspace (either by pressing ctrl+alt+right or by using the workspace switcher) would temporarily restore the context menus in other applications, until right clicking again in eclipse would kill it again
[*]i solved the problem by closing firefox and restarting Eclipse (i'm not joking)
[/LIST]

---

