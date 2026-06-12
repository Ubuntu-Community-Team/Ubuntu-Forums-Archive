---
title: "Fullscreen VNC on a single workspace"
date: 2006-08-28
forum: Desktop Environments
---

### Post by one_stinky_bum on 2006-08-28
Hello folks,

I am able to run fullscreen VNC on Dapper (it even works with compiz+aiglx), but it covers all workspaces? Is there a way to run a fullscreen VNC session but restrict it to only one workspace? I did a search, but didn't come up with anything conclusive.

Thanks.

---

### Post by one_stinky_bum on 2006-08-30
bump. :confused:

---

### Post by eclectic_rookie on 2006-10-11
You can use Ctr+Alt+Return to switch between full screen and the desktop. 
I hope this helps.

---

### Post by one_stinky_bum on 2006-10-12
Thanks for the tip.

---

### Post by thrutchy on 2008-01-03
Here are a few tips:

* use krdc.  it's full-screen button doesn't seem to go to all workspaces.  Unfortunately, you may have to click it a few times to get it really full-screen.  It is a kde app, maybe it doesn't play as well for gnome.  The big benefit of krdc is auto-scaling.  It is the only kde app I have.

* pull up gconf-editor.  Give a key for apps -> metacity -> window_keybindings -> toggle_fullscreen.  In any vncviewer use this instead of F8->fullscreen or -fullscreen from the command-line.  This seems to go to one workspace instead of all.  compiz also looks at this key binding.

* don't use compiz.  Set system->preferences->appearences->special effects to None.  This will switch back to the meta-city window manager.  I found several problems with vncviewers and compiz:
  + when using an external monitor with a larger resolution, it sometimes thought that full-screen is the smaller monitor size.  Even just changing focus would sometimes shrink to the smaller screen.
  + the password prompt for all but krdc took forever to come up (30-60 seconds).  no problems with metacity.  strange.

I'm now using krdc on metacity.  Too many little issues with compiz.

---

