---
title: "Theme Problems -- Moving the buttons from the right to the left"
date: 2012-06-29
forum: Desktop Environments
---

### Post by theWrkncacnter on 2012-06-29
Hello Ubuntu Forums,

tl;dr: I need to move my window buttons (close, maximize,minimize) to the left, PERMANENTLY.

A long time ago, I used gconf-editor to put the buttons on the right hand side. Now that unity is a little more coherent, I've been trying to move them back. The problem is, whenever I use gconf-editor to put the buttons to the left, They're back on the right after a restart.

Currently the buttons are on the right when the window is "popped out" so to speak, and on the left when fullscreen, combined with the unity system bar.

I tried looking for files to edit in /usr/share/theme/Ambiance based on what worked for this guy ([http://mikebeach.org/2010/09/07/move-ubuntu-windows-buttons-from-left-to-right-and-make-it-permanent/](http://mikebeach.org/2010/09/07/move-ubuntu-windows-buttons-from-left-to-right-and-make-it-permanent/)) but found nothing.

Are there any ideas what's causing the buttons to default to the right? Is there anyway I can permanently assign the buttons to the left?

Thanks,
Patrick

---

### Post by theWrkncacnter on 2012-06-29
Just found a solution -- in dconf-configure, go to
org.gnome.desktop.wm.preferences 

it has button-layout stanzas just like gconf. Set those, and click "set to default" on the bottom. Feels good man!

---

### Post by theWrkncacnter on 2012-07-10
Actually don't click "set default" just save. Set to default returns it to whatever the default was -- in my case, the wrong setting.

---

