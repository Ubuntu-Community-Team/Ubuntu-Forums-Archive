---
title: "gconf-editor keyboard shortcuts don't work - no compiz"
date: 2007-11-04
forum: Desktop Environments
---

### Post by crazybilly on 2007-11-04
I'm having problems with my keyboard shortcuts.  

First of all, shortcuts I set up in gconf-editor, in metacity don't work at all.  I'm not running compiz, as far as I know (I don't have any fancy fx, but I am on Gutsy).

Second, I can set up shortcuts that work using the system preferences->keyboard shortcuts tool.

But I can't get the windows key+E to open my home directory.  Despite the fact that windows+s opens the panel menu just fine.

I tried setting keyboard shortcuts in the compiz part of gconf-editor and it didn't seem to work.  But then again, maybe I did it work (maybe I missed a setting somewhere?).

Any ideas?

---

### Post by crazybilly on 2007-11-05
UPDATE:

I figured it out.  Turns out metacity isn't my window manager at all, now that I'm runnign Gutsy.  Compiz is my window manager, even though I don't have any fx turned on.  

So what I did was install ccsm, which is the compiz control panel.  There, in General options, are two tabs (like in gconf-editor): commands (for program names) and actions (for keyboard shortcuts).  

Bizarrely, the commands fields were populated w/ what I filled in for keyboard shortcuts in metacity in gconf.  Not sure why...nor why they were backwards (it had keyboard shortcuts where program names should be.  Bizarre).

So that takes care of the programs that wouldn't work right.

However, windows+e still won't work.  I got an error a minute ago: compiz told me that super+e is Expo's shortcut.  However, I've tried disabling both Expo and its keybinding and I still can't get my home directory to open up.  Argh.

---

