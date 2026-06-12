---
title: "GNOME keyboard shortcuts"
date: 2006-07-04
forum: Desktop Environments
---

### Post by thor on 2006-07-04
Hello!

Is there any way to bind special commands to certain keys?

I want to bind 'mpc toggle' command to Win+3 key, etc.

---

### Post by frodon on 2006-07-04
I wrote a small guide on this topic there : 
[http://ubuntuforums.org/showthread.php?t=79560](http://ubuntuforums.org/showthread.php?t=79560)

---

### Post by thor on 2006-07-04
Wow, thanks! I tried searching the forums, but haven't find that guide.

---

### Post by mlind on 2006-07-04
[QUOTE=thor]Hello!

Is there any way to bind special commands to certain keys?

I want to bind 'mpc toggle' command to Win+3 key, etc.[/QUOTE]

Yes you can.

I've binded Ctrl+Alt+Pause to non-locking screensaver like this:

[LIST]
[*] open gconf-editor 
[*] find key */apps/metacity/global_keybindings*
[*] set **run_command_1** to <Ctrl><Alt>Break
[*] find key */apps/metacity/keybinding_commands*
[*] set **command_1** to *gnome-screensaver-command --activate*
[/LIST]

Win -key is called as Super_L, but Win+3 is probably <Mod4>3

---

### Post by aysiu on 2006-07-04
Well, first you'll have to make the Windows key a modifier key instead of its own key. Go to System > Preferences > Keyboard to change the Windows key properties.

Then press Alt-F2 ```
gconf-editor
``` Apps > Metacity

In Keybinding Commands, Command_1 use ```
mpc toggle
``` and in Global Keybindings, type the keyboard shortcut. You may have to play around in System > Preferences > Keyboard Shortcuts to see what Ubuntu calls your Windows key.

---

### Post by thor on 2006-07-04
I went metacity route and have my keys working exactly as a want, great! :)

Linux rocks, again!

But if would choose xbindkeys  - should I run it every time I log in into Gnome? What is the best way to start it automatically - make it part of my gnome session?

---

### Post by frodon on 2006-07-04
In my case i added "xbindkeys" at gnome session startup commands thus it's running each time i login GNOME, so for me it's the best way.

---

