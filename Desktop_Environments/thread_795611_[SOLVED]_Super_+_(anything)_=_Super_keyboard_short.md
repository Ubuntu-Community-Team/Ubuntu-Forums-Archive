---
title: "[SOLVED] Super + (anything) = Super keyboard shortcut"
date: 2008-05-15
forum: Desktop Environments
---

### Post by xIke on 2008-05-15
I'm trying to do Super + E and Super + L, but my shortcuts end up as Super L (left super button) instead.  How can I get the keyboard shortcuts panel to let me use super as a modifier key and not a single key.  I'm holding super down, then pressing the other key.

Thanks!

---

### Post by hermes0710 on 2008-05-16
Go to System>Preferences>Keyboard and press the Layout options button. There is a root entry for Win/Alt keys or something, there you can set that Super is mapped to win keys.

---

### Post by xwyantx09 on 2008-05-16
I dont know everything about Linux, but i do know that you cant set any letter buttons to a shortcut in Windows, i would check for you but im sitting in class on my windows machine. what he said in the above reply i belive was correct, i think its system >> admin >> keyboard shortcuts, or something close to that. I hope im wrong, and you get your keyboard shortcut working, good luck

---

### Post by xIke on 2008-05-16
hermes0710, that seems to be exactly what I needed- though it didn't work. :P

When I set the shortcut, it called it mod4 instead of super (fine by me) and allowed for it to be a modifier key, but pressing that combo afterwards did not work.  Any ideas?  I chose the "Super is mapped to the Win-keys" option in Keyboard Preferences.

---

### Post by hermes0710 on 2008-05-16
Change of plans :P From the keyboard layout options turn it back to what it was (or else press "Reset to defaults"). I suppose you have compiz enabled. Go "System>Preferences>Advanced desktop settings" and in the general settings, i think in the second tab you can assign custom commands and keybindings for these commands. So, type "nautilus" as command1 for example and in the below section (keybindings) press the button to assign key and in the window that appears press Grab combination: press the keys you want and everything will be fine. I did in my pc and works fine. I am not home right now so i will get back to you later this evening

---

### Post by xIke on 2008-05-16
> **hermes0710 said:**
> Change of plans :P From the keyboard layout options turn it back to what it was (or else press "Reset to defaults"). I suppose you have compiz enabled. Go "System>Preferences>Advanced desktop settings" and in the general settings, i think in the second tab you can assign custom commands and keybindings for these commands. So, type "nautilus" as command1 for example and in the below section (keybindings) press the button to assign key and in the window that appears press Grab combination: press the keys you want and everything will be fine. I did in my pc and works fine. I am not home right now so i will get back to you later this evening

I don't have Advanced Desktop Settings.  I do have compiz enabled though.

---

### Post by hermes0710 on 2008-05-16
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by xIke on 2008-05-16
> **hermes0710 said:**
> ```
sudo apt-get install compizconfig-settings-manager
```

Nice.

Anyone know a command for lock screen so I can put in in the same way?  Thanks!

---

### Post by hermes0710 on 2008-05-16
try this:

gnome-screensaver-command --lock

---

### Post by xIke on 2008-05-19
Great, that got it!  In case anyone else has problems, I was trying to use Super+L which was also the keystroke for zoom area lock (but it didn't warn me of this and silently failed.)

---

