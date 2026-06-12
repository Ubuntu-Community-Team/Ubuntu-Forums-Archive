---
title: "Scale UI via command line"
date: 2018-02-02
forum: Desktop Environments
---

### Post by Donnut on 2018-02-02
Hi. I have Ubuntu 17.10 installed via Parallels, with a High DPI screen. However, I can't seem to set the UI scaling, it is not in the display settings. Is there a way to do this manually?

---

### Post by again? on 2018-02-02
You can use gsettings in terminal.
eg
```
gsettings set org.gnome.desktop.interface scaling-factor **2**
```
You may need to restart gnome-shell or logout to see changes.

To set back to default...
```
gsettings reset org.gnome.desktop.interface scaling-factor
```

---

### Post by Donnut on 2018-02-03
Worked like a charm, thank you!

---

