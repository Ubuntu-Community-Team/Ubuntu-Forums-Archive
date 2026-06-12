---
title: "Input method icon not appearing in systray"
date: 2012-08-16
forum: Desktop Environments
---

### Post by Kremlin on 2012-08-16
After installing lubuntu, I went to the Language settings and installed Japanese, and set the input method to ibus. Then I added the Anthy input in the Keyboard Input Methods settings panel. The input works as expected, but there is no ibus/Anthy icon in the systray. It only shows battery and wifi icons. I would like to have the icon because it's helpful to know which language input mode I'm in, and also the icon has a submenu in which I can change settings quickly. 

Any ideas?

---

### Post by Kremlin on 2012-08-20
Bump.

---

### Post by GeorgeWhite5 on 2012-08-20
LXPanel doesn't seem to show the iBus system icon.

You can still switch languages through keyboard shortcuts, however.

Could you install another desktop enviroment? (E17 (enlightenment), Xfce (xfce or xfce-desktop) etc.)

---

### Post by Kremlin on 2012-08-24
Yeah, I could probably. When I was running e17 on another install it worked without a problem. I just figured I'd give LXDE a shot - it runs very nicely and only a few niggles.

---

### Post by Kremlin on 2012-09-24
This is fixed by installing the package python-appindicator and restarting. For some reason, that is an unspecified dependency of the ibus daemon which is not installed in lubuntu.

From the terminal:

```
sudo apt-get install python-appindicator
```

And reboot. You might simply be able to log out/back in again, but a reboot will do the trick.

---

