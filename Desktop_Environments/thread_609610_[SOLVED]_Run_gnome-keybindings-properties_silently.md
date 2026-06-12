---
title: "[SOLVED] Run gnome-keybindings-properties silently"
date: 2007-11-11
forum: Desktop Environments
---

### Post by Linicks on 2007-11-11
Hi all,

I have switched to Fluxbox from using Gnome on my Inspiron 6400n laptop.

I sorted the suspend etc. from loading /usr/bin/gnome-power-manager in $HOME/.fluxbox/startup  file.

I also found that running gnome-keybindings-properties sets up all the sound and other desktop keys to work correctly on my laptop - except you get a window to configure and then have to close it manually.

What I need to do is run gnome-keybindings-properties and silently exit so the existing keybind setings just get applied.

Can this be done with a switch, or will I have to run a script to start it and then kill it.

Thanks,

Nick

---

### Post by spupy on 2007-11-11
Why not use the Fluxbox' keys file to set your keybindings? It's located in ~/.fluxbox/keys
This wiki page will help you use the file: [http://fluxbox-wiki.org/index.php/Keyboard_shortcuts]("http://fluxbox-wiki.org/index.php/Keyboard_shortcuts")
Try running gnome-settings-daemon. It "sets" the theme for gnome apps and perhaps gnomes keybindings, too. 
On a side note: With fluxbox i try to be as independant from GNOME as I can be. The only gnome things i run are the settings-daemon (soon to be replaced with .gtkrc) and the gnome volume manager (soon to be replaced with ivman).

---

### Post by Linicks on 2007-11-11
Yes, I looked at all that, but my issue is I don't know what gnome-power-management/keybindings-properties does to the assigned fn+key for e.g. to suspend... or make the front audio buttons work - or what it does to turn on/off the wireless key etc.

Nick

---

### Post by spupy on 2007-11-11
> **Linicks said:**
> Yes, I looked at all that, but my issue is I don't know what gnome-power-management/keybindings-properties does to the assigned fn+key for e.g. to suspend... or make the front audio buttons work - or what it does to turn on/off the wireless key etc.

You have a valid point. You can't set the Fn keys in fluxbox. My Fn keys work on a hardware level, independent of the OS, so i never noticed that.

---

### Post by Linicks on 2007-11-11
Yes.  It's no big deal as running gnome-power-managent from fluxbox startup file works perfectly for the fn+keys, and at the moment I have a menu entry so I can run as user to assign the gnome-keybindings-properties (unless I forget to run it ;-) ).

I would just like to try to run gnome-keybindings-properties silently 'native' rather than knocking up a script to start/kill it during login.

Nick

---

### Post by Linicks on 2007-11-15
OK, sorted this.  I noticed that 'gnome-keybindings-properties' is actually a sub-part of Gnome processes.

Using:

gnome-settings-daemon &

in fluxbox startup file loads it all fine at log in.

Nick

---

