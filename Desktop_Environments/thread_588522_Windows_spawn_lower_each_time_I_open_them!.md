---
title: "Windows spawn lower each time I open them!"
date: 2007-10-23
forum: Desktop Environments
---

### Post by Punio4 on 2007-10-23
Here's the problem: Using gutsy with compiz-fusion.
Every time I open a window, it spawns about a titlebar height lower then last time. What could be causing this?
It's really irritating, especially for windows I set below the panel, like gimp or pidgin.

[EDIT]
When I disable desktop effects it's fine, so it's probably compiz. Any way to fix this?

---

### Post by Perpetual on 2007-10-23
In Advanced Desktop Effects, check for 'Place', 'Put' and any other window related options.  I am not on my Ubuntu machine right now but you can change how windows are placed with these options.  I use Centered but their are other options.

If you do not have compizconfig-settings-manager installed:

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by Punio4 on 2007-10-23
Already checked... Nothing.
Also tried disabling blur, animations, fade... Hell, even "move".
It remains the same.

---

### Post by Punio4 on 2007-12-01
Ok, bumping my own thread. Here's a gif included:
[IMG]http://i4.photobucket.com/albums/y136/Punio4/window_lower.gif[/IMG]
Now I noticed another thing too. The reopened application also spawns a border widht to the right each time... Really weird.

---

### Post by Perpetual on 2007-12-01
Did you try enabling 'Place' in CCSM and setting it to 'Centered' (or one of the options you prefer)?

---

