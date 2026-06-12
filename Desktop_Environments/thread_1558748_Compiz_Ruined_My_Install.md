---
title: "Compiz Ruined My Install"
date: 2010-08-22
forum: Desktop Environments
---

### Post by FireDemonSiC on 2010-08-22
This is the second time this has happened and is really starting to urk me.

While playing around with the opacity settings in Compiz, I inadvertently turned all the windows, menus and the taskbar invisible.  I can't simply reverse this through the CCSM because I can no longer see what I'm doing.  The window is there you just can't see it.  The first time it happened I simply reinstalled Ubuntu since it was off a fresh install but I don't want to install it for a THIRD time plus I need to learn how to fix these kinds of errors in case something like this occurs in the future when the OS has reach maturity.

On the last install I tried apt-get remove compiz and ccsm but that didnt restore my windows and menus.  How do I fix this?  I really am kind of surprised a feature with the potential to go horribly wrong such as this doesnt have the "Would you like to keep these new settings? (reverting in 15 seconds)" window.

---

### Post by cariboo on 2010-08-22
This is a better place for your question, than Multimedia & Video.

---

### Post by heluani on 2010-08-22
Well, if it is just the settings that are bugging you, you first need to check how they are stored. Compiz has a couple of different backends to store its settings. If you see a file ~/.config/compiz/compizconfig you can safely delete it as it will be recreated (you might remove the whole compiz directory). If you on the other hand had activated the gconf backend, then you will need to run gconf-editor to look for the options that bug you. Alternatively, you can remove the directory ~/.gconf/apps/compiz/ and I think this should be enough. You can always go back to metacity with 
```
gconftool-2 --type=string --set /desktop/gnome/session/required_components/windowmanager metacity
```

Cheers,

R.

---

### Post by PaulReaver on 2010-08-22
press ctrl Alt F1 and log in

then type (without the quotes)
"gconftool-2 --recursive-unset /apps/compiz" 

then type (without the quotes)
"exit"   

then press ctrl Alt F7 to take you back to your desktop.

---

### Post by stinkeye on 2010-08-23
Hover over where you think the window is,
hold down the alt key and scroll up with the mouse to increase the opacity.

---

