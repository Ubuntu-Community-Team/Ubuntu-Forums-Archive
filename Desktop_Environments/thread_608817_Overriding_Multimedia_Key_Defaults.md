---
title: "Overriding Multimedia Key Defaults"
date: 2007-11-10
forum: Desktop Environments
---

### Post by abresch on 2007-11-10
Right now, several of the keys on my keyboard (logielite) are useless because KDE insists that they do specific things. All the keys are recognized and work properly, by the volume control dial and media button cannot be reconfigured. The volume control adjust's KMix's master volume and the media button shifts focus to Amarok (assuming I'm on the right desktop).

I want these buttons to do other things, but cannot turn off the current behavior and the key-commands are intercepted above the level of other KDE hotkeys. I see nothing in any shortcut key control section to change these settings, and I cannot find any config file that affects this.

Is there anywhere that these settings are controlled from?

---

### Post by abresch on 2007-12-04
Seriously, these keybindings set by the system which are uneditable is just ridiculous. I upgraded, and now the media key can be set to whatever I want, but the mute key and e-mail key are useless and the volume control is still out of my control.

---

### Post by boast on 2007-12-05
same here;

:confused:

---

### Post by sorin.stirbu on 2007-12-07
Hy guys !! I am having kind of the same problem as you do. I am trying to change the "rhythmbox" command with the "audacious" command that my "Player" key has ..... i have tried from System -> Keyboard Shortcuts, but there i can only change the button that opens the player ... not the player that i wan't to open.

Do you have any ideea how to change that ??? Or if you know what file (the location) where the instructions (and commands) for the multimedia keys are in File System (so i can edit that file) ???

---

### Post by abresch on 2007-12-08
I have finally managed to find a solution to this problem.

Run the command "kcmshell kcmkded" and turn off the KMilo service, or uninstall KMilo.

This will completely disable the program that runs above all other keybindings in the system and causes the multimedia keys to do things in a completely unconfigurable manner.

---

