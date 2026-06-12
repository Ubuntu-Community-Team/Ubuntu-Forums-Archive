---
title: "Panel issues."
date: 2010-03-21
forum: Desktop Environments
---

### Post by venividibitchy on 2010-03-21
Hey folks,

Sometimes, I turn on my computer, only to find my top panel is "locked" and a solid color. None of my icons, weather applets, the time, etc. are present. Occaisonally, a few icons are present, but they're not clickable. I'll look at my processes and find that panel is "not responding".

I resolve the problem by typing ctrl+alt+f1, typing in my username+password and entering, "killall gnome-panel".

My panel will then appear and be fully functional (though usually without my weather applets). Sometimes, the applets will appear upon my next restart and work fine.

What could be going on, and how can I permanently fix it?

---

### Post by Jakey_TheSnake on 2010-03-21
Are you using unsupported applets? 

Try going to System > Preferences > Startup Applications and then adding a new one, call it "panel fix" and the command: ```
sh -c "sleep 1 && killall gnome-panel &"
```

Which will refresh your gnome panel 1 second after login. This should only be a work-around fix, though, as your panel should not have to be restarted. I just have no ideas otherwise >_<

---

### Post by venividibitchy on 2010-03-30
Thanks for the suggestion -- I added the fix.

I just wish I could get to the root of the issue. It seems other people in another thread are having the same/similar issues.

No, nothing unsupported -- I'm using the included weather applets, and really love using them, so I would hate to have to uninstall them.

ETA: Restarted the PC, and the panel fix did not work. Go figure.

---

### Post by venividibitchy on 2010-04-03
Any more suggestions?

---

### Post by lidex on 2010-04-04
Remove your panel config and start from default:
```
gconftool --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

