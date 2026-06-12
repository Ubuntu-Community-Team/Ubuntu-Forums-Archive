---
title: "gnome- no theme in synaptic or nautilus@root"
date: 2010-08-02
forum: Desktop Environments
---

### Post by spam1408 on 2010-08-02
I have a gtk & emerald theme installed on ubuntu 10.04 and when i open synaptic or nautilus as root it's like i have no theme...don't know how to describe exactly. anyone experienced this too? please help me!

---

### Post by mcduck on 2010-08-02
That sounds like you are using a GTK theme that is installed for your user only, not system-wide. Since the apps running as root are, well, running as a different user, they don't have those themes available.

There's two possible solutions:

First one is to install all your themes in /usr/share/themes, and icons in /usr/share/icons.

And the second one, which I actually prefer if I don't need the themes to be available for every user, just for my own and root. You can just link your user's theme directories into root's theme directories:

```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

---

