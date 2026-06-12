---
title: "Compiz Key Binding Bugs in Gutsy"
date: 2007-12-31
forum: Desktop Effects &amp; Customization
---

### Post by silverhammermba on 2007-12-31
I'm getting a bunch of weird bugs when changing key bindings in Compiz. The most annoying one currently is that when I try to change certain key bindings, the binding will briefly say "Disabled" and then the key binding menu will collapse. When I expand it again, the previous key binding will be there again - making it impossible to change. Even if I change the value through the configuration editor, it will show the new value but the key binding will not actually work. Also, my enter key no longer works (hence the single paragraph). I believe that it has been captured by a wayward key binding. I did bind something to enter by accident but quickly changed it, and now I can't find any key bindings that even involve enter. I'm about to just remove compiz and start from scratch.

---

### Post by silverhammermba on 2007-12-31
Okay, I gave up. I found I had accidentally put "Disable" instead of "Disabled" for a button binding in the configuration, but even after fixing that nothing changed. I reset my compiz profile to the defaults. My enter key still doesn't work and I'm not sure if that has fixed the immutable key bindings either...

---

### Post by croco44-MN on 2008-02-11
I have this exact same problem. Also, sometimes it will let me set a key binding without complaint (without collapsing the key binding list) but it will not work, and if I close and re-open the settings manager the binding will be disabled.

Has anyone worked around this?

---

### Post by croco44-MN on 2008-02-11
Actually, it appears that if I set the key binding manually in gconf I get it to work temporarily (for that session). However, even with it set this way the binding does not show up in the Compiz configuration Settings Manager. When I reboot, the binding no longer works. It still shows up in gconf though.

---

