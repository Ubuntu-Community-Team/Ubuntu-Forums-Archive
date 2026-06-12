---
title: "Volume keyboard shortcuts resets on reboot"
date: 2010-10-25
forum: Desktop Environments
---

### Post by RuneLacroix on 2010-10-25
The volume keyboard shortcuts on my Asus Eee 1008p resets on reboot.. (going back to no shortcut at all).
It works for the session, if i set it, but after reboot i have to set it again.

Can anybody help?

Kind Regards, Rune

---

### Post by RuneLacroix on 2010-10-26
SOLVED.

- open gconf-editor
- go to /apps/gnome_settings_daemon/keybindings
- unset values for volume_down, volume_mute and volume_up (by right-clicking each key and selecting "Unset key")

---

### Post by RuneLacroix on 2010-10-26
Well.
I was a little to fast on this one... I forgot to check if it actually worked after reboot.
It doesn't. It goes back to having no shortcut.
Some time ago i installed the Eee control daemon. Before that i couldn't use any of the specific shortcuts on the keyboard. But in the Eee control settings the sound shortcut settings isn't featured. 
Hmm. 
Can anyone help me further?

---

