---
title: "Jumbled Top Bar"
date: 2011-01-20
forum: Desktop Environments
---

### Post by Cornova on 2011-01-20
For the past month, the top right corner of my screen, where the power button and pc-name button are becomes screwed up. That is, the power button disappears and there are two pc-name buttons jumbled into each other. Is there a way to reload this top bar so I don't have to keep sudo rebooting via the terminal every time it happens?

---

### Post by Frogs Hair on 2011-01-20
Reset panels
```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by hsoulen on 2011-01-21
Also happens to me on occasion... Very annoying.

The above solution works, you can just create a shell script and put it on your desktop to run when it happens.

Alternatively you can just move the panel to the right or left of the screen and then back to the top or bottom (depending on where you keep the panel) and this will reset it as well.

Don't ya just hate silly quirks like that?

Cheers,

Hank

---

