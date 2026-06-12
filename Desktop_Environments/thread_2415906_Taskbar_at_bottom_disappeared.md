---
title: "Taskbar at bottom disappeared"
date: 2019-04-02
forum: Desktop Environments
---

### Post by sgroffman on 2019-04-02
I am using lubuntu 16.04. About two weeks after install, I opened it and the taskbar at bottom (showing start button, network info, audio control, etc.) had disappeared. I tried reinstalling lxpanel, but this did not get it to reappear. Any suggestions?

---

### Post by Mr. Swiveller on 2019-04-03
I've never used LXDE, but assumedly it has a menu of some sort where you can enable and disable elements of the interface. Try right-clicking on the desktop.

---

### Post by Frogs Hair on 2019-04-05
Try the following command, logout and back in:
```
cp /usr/share/lxpanel/profile/Lubuntu/panels/panel ~/.config/lxpanel/Lubuntu/panels
lxpanelctl restart
```

---

### Post by sgroffman on 2019-04-11
User on another thread recommended I update to lubuntu 18.04, since 16 is going out of support soon. Did that and the taskbar is fine.

---

