---
title: "Reinstall Gnome Screensaver"
date: 2010-02-06
forum: Desktop Environments
---

### Post by thegreatpenguin on 2010-02-06
Anyone have the terminal command to reinstall gnome screensaver  I accidentally deleted it thanks.

---

### Post by howefield on 2010-02-06
Do you want to install the package gnome-screensaver ?

```
sudo apt-get install gnome-screensaver
```

---

### Post by thegreatpenguin on 2010-02-06
Yea I was messing with xscreen saver and screwed it all up ill try that thank you.

---

### Post by thegreatpenguin on 2010-02-06
Well I used the command it says it installed but I have no icon in preferences to access the screen savers I looked in main menu but its not there either any ideas thanks.

---

### Post by howefield on 2010-02-06
> **thegreatpenguin said:**
> Well I used the command it says it installed but I have no icon in preferences to access the screen savers I looked in main menu but its not there either any ideas thanks.

It may need a reboot to get the preferences icon to show in your menu. Or at the least a logout/back in of your session.

You could launch from terminal

```
gnome-screensaver-preferences
```

---

### Post by thegreatpenguin on 2010-02-06
I did a reboot after the install all those years on windows lol it did not show in preferences   I will just use that command to open it and call it good thanks for your help.:popcorn:

---

### Post by howefield on 2010-02-06
If the icon hasn't appeared, you could also create an icon for it, using System > Preferences > Main Menu, then click Preferences in the left window pane, and then press the New Item button.

---

