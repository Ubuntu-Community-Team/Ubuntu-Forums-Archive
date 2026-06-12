---
title: "keyboard shortcuts broken in gnome-shell"
date: 2012-01-27
forum: Desktop Environments
---

### Post by Arancaytar on 2012-01-27
After installing gnome-shell in Ubuntu 11.10, almost all my keyboard shortcuts have stopped working. Some of them are obviously broken by the theft of the Mod4 key (a different problem that I haven't yet managed to fix) but that's unrelated since some are broken that don't even use that key.

This doesn't just affect custom shortcuts either; for example, all media and volume control keys are broken, even though in the gnome-control-center they're configured correctly. The keys themselves also work, since they will be recognized when adding a shortcut.

I've experimented a bit and found that the only shortcut still working is the Terminal launcher. The key combination itself is unimportant. The terminal launcher will work with nearly any key combination, while those same combinations can't launch anything else, like text editors, web browsers, modifying the volume, etc. I'm confused.

---

### Post by lolpenguin on 2012-01-27
Mod4 is the Super/Meta/Windows key. Have you tried System Settings > Keyboard?

---

### Post by Arancaytar on 2012-01-28
That's exactly where I set the keyboard shortcuts that aren't working, which as mentioned don't contain the Mod4/Super/Windows key. 

To recap again: The only macro that works is the gnome-terminal launcher; and this is independent of the key used. If I change it to Ctrl+< or Ctrl+X or anything, that change will take effect immediately. 
Other macros like volume changing do not work at all, even when giving it a combination like Ctrl+X, which worked moments ago when assigned to launch gnome-terminal. New custom command macros do not work either.

---

### Post by Frogs Hair on 2012-01-28
There are some keyboard shortcuts for the shell at the link and as you may know the command prompt  Alt + F2 is disabled by default in the shell . You may have conflicting shortcuts if you also run Unity with Compiz effects or have a laptop / netbook .   [http://live.gnome.org/GnomeShell/CheatSheet](http://live.gnome.org/GnomeShell/CheatSheet)

---

### Post by Arancaytar on 2012-01-28
Unity and compiz aren't running while in a gnome-shell session, though. If they were, there'd be worse conflicts than just a few keyboard shortcuts. Alt+F2 appears to be enabled by default; that's one of the ones that work, along with the Super key itself, the Alt+Tab/Alt+^ application switchers, Alt+F1 and pretty much all the default gnome-shell stuff, which is also all that link describes. None of that is related to the shortcuts set in the System Settings (ie. the gnome-control-center application).

If it weren't for the single working "terminal launch" macro, I'd conclude that the System Settings shortcuts are simply ignored entirely.

---

### Post by Shade0o on 2012-01-29
Use Alt+F2 to open the prompt and enter
```
dconf-editor
```
go to ```
org > gnome > setting-daemon > plugins > media-keys
```
Quite a bit of keys that i couldn't rebind though system settings were in this list. they all work for me now.

Not all keys are here, so you might want to look ever the dconf a bit more as i've forgotten where the rest are

---

### Post by Arancaytar on 2012-01-29
All my custom key bindings are listed correctly in that path, but right at the top there was a big glaring "active" setting that was switched off. Thanks!

After toggling that, all my keybindings seem to work, even - to an extent - the ones containing the Mod4 key. However, those key combinations are touch and go, often requiring multiple presses, so I'll replace them with C, m or C+m bindings.

Edit: That is to say, my custom key bindings for existing macros are working. My own custom commands aren't working yet, and I also can't find them in dconf.

---

