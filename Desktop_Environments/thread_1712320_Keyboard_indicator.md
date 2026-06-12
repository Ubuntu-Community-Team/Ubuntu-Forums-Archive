---
title: "Keyboard indicator"
date: 2011-03-22
forum: Desktop Environments
---

### Post by nick_goodfate on 2011-03-22
After the last reboot, instead of the default indicator for keyboard layout i see this "x" icon(screenshot below). This icon seems to me that belong to the Faenza icon set. The strange think is that even when i change the icon set i'm using this icon remains the same. 
Any idea of how can i fix this?

---

### Post by Krytarik on 2011-03-22
Some items of the gnome-panel don't immediately adapt to the newly chosen icon theme. For those you need to restart gnome-panel:
```
killall gnome-panel
```Greetings.

---

### Post by nick_goodfate on 2011-03-22
> **Krytarik said:**
> Some items of the gnome-panel don't immediately adapt to the newly chosen icon theme. For those you need to restart gnome-panel:
```
killall gnome-panel
```Greetings.

I did, remains the same. 

If you don't know how to fix this, do you know if i can remove it without removing the entire notification area?

---

### Post by Krytarik on 2011-03-22
Did you try to re-login after switching the icon theme!?

To disable the keyboard layout indicator run this command (may not work in 10.10 due to a bug):
```
gconftool-2 -s /desktop/gnome/peripherals/keyboard/general/disable_indicator -t bool true
```

---

### Post by nick_goodfate on 2011-03-22
I don't have the nerves to fix this...
Just removed it with your command. Thank you for your help!

---

