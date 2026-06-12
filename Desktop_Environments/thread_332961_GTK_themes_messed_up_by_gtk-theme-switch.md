---
title: "GTK themes messed up by gtk-theme-switch?"
date: 2007-01-06
forum: Desktop Environments
---

### Post by jem7v on 2007-01-06
So I was experimenting with Fluxbox for a little while and I used the switch2 program from the gtk-theme-switch package to pick my GTK themes in Fluxbox, and when I came back to Gnome (because I was too lazy to do the work necessary for Fluxbox to be super) I discovered that it had also changed my GTK theme here. The problem, though, is that gnome-theme-manager can't seem to change to another GTK theme any more... the window foreground and background colors will change, but the buttons and scrollbars and such stay the same as the last theme I chose with switch2.  Only switch2 manages to actually change my themes now, and sometimes it DOESN'T change the background and foreground.

Any suggestions on what I can change to fix this?  It isn't of life-or-death importance, but it's annoying as hell.

---

### Post by jem7v on 2007-01-06
Okay, I found the issue and resolved it myself, no thanks to the rest of the internet (because 2 hours of searching Google turned up nothing). Here's the solution, in case anyone else runs into this issue and manages to find this thread:

switch2 from gtk-theme-switch adds a line to your ~/gtkrc-2.0 file that shouldn't be there, and after you use switch2 it looks like this:

```
# -- THEME AUTO-WRITTEN DO NOT EDIT
include "/home/bryce/.themes/Cillop-Mediterranean/gtk-2.0/gtkrc"

include "/home/bryce/.gtkrc-2.0.mine"

# -- THEME AUTO-WRITTEN DO NOT EDIT
```

the first include SHOULD NOT be there, because then it automatically uses that GTK theme no matter what you change your theme to in gnome-theme-manager (System->Preferences->Themes) and it's only changed by switch2. So even though the file says "do not edit," git rid of that line and save it anyway.  It should solve the problem.  (It did for me.)

---

### Post by 3rdalbum on 2007-01-07
I just *switch*ed the GTK theme back to what it says in Gnome Theme Manager, and that worked. (and it fixed my fonts, which I'd stuffed up months ago!)

---

### Post by jem7v on 2007-01-07
Yeah, I tried that, but it stayed stupid. Oh well. :)

---

### Post by nevin on 2007-07-11
oh my goodness, thank you so much.

the same EXACT thing happened to me... i tried uninstalling fluxbox, but that didnt work... so i had to reinstall it just so i could switch themes... a real pain.

but perfect!  it works!

---

### Post by RedSquirrel on 2007-07-11
You could just comment that line (put # in front of it):

```
 # -- THEME AUTO-WRITTEN DO NOT EDIT
[COLOR=Red] #i[/COLOR]nclude "/usr/share/themes/Clearlooks/gtk-2.0/gtkrc"

include "/home/user/.gtkrc-2.0.mine"

# -- THEME AUTO-WRITTEN DO NOT EDIT
```I don't think GNOME really needs the ~/.gtkrc-2.0 file, so you could also rename the file to something else or move it to another directory (e.g., some subdirectory of /home/user). You could probably just remove it, but I like to keep things around for a while by renaming or whatever... ;)

---

### Post by Wiorka on 2007-07-28
**@jem7v:** Thank you so much :) The same history here, fluxbox + gtk theme switch..

---

### Post by JMO707 on 2007-07-31
Recently I had the same problem. But I keep one doubt: how can I change the GTK theme ONLY for Fluxbox?

My Fluxbox session has a totally different style from the GNOME one =p

---

### Post by JMO707 on 2007-08-01
Someone?

---

### Post by manelik on 2008-06-25
try adding a line

```
export GTK2_RC_FILES=/YourThemePath/gtk-2.0/gtkrc
```

to your fluxbox startup script

---

