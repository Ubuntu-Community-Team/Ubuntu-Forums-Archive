---
title: "Disappearing toolbars"
date: 2009-06-30
forum: Desktop Environments
---

### Post by bravo sierra echo on 2009-06-30
Xubuntu Jaunty Jackalope on a Packard Bell.

This machine has three user accounts - on the main administrator one, the toolbars at the top and bottom of the screen have disappeared.

I had a search around the forum and found [this thread,](http://ubuntuforums.org/showthread.php?t=234504) but still no joy - the toolbars disappear again when I close the terminal window, even using the ```
xfce4-panel &
``` command.

Help!

---

### Post by bravo sierra echo on 2009-06-30
Sorry, should have said.  The command brings back these errors:

```
caroline@ariane:~$ xfce4-panel &
[1] 3858
caroline@ariane:~$ 
(xfce4-mixer-plugin:3861): libxfce4mixer-CRITICAL **: xfce_mixer_get_track: assertion `GST_IS_MIXER (card)' failed

(xfce4-mixer-plugin:3861): xfce4-mixer-plugin-CRITICAL **: xfce_mixer_plugin_set_card: assertion `GST_IS_MIXER (card)' failed

(xfce4-mixer-plugin:3861): xfce4-mixer-plugin-CRITICAL **: xfce_mixer_plugin_set_track: assertion `GST_IS_MIXER_TRACK (track)' failed

** (gnome-system-monitor:4120): WARNING **: SELinux was found but is not enabled.
```

---

### Post by ajgreeny on 2009-06-30
Try running the command again, but in the run application dialog (Alt+F2 in gnome, I assume the same in xfce).  That may help keep it running all the time, but I can't imagine why it has disappeared.

---

### Post by bravo sierra echo on 2009-06-30
Thanks, ajgreeny.

That keeps the toolbars up for the duration of the session, but then when you restart they disappear again.

I have seen this once before with Xubuntu Hardy Heron - on a different machine - but I just re-installed on that occasion.  This machine has got all sorts of stuff on it so I'd rather try to fix it than re-install!

---

### Post by ajgreeny on 2009-06-30
Well, apart from adding that command to a startup script, I have no idea what you can do about that.  I'm sure somebody must know how to get the default panel back, but never having used xfce, I haven't got a clue, I'm afraid.

---

### Post by kerry_s on 2009-06-30
in the session & startup check the automatically save session.

---

