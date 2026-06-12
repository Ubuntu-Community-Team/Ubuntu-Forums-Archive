---
title: "Complete Remove Ku-/Xubuntu-desktop"
date: 2008-08-14
forum: Desktop Environments
---

### Post by Jompa on 2008-08-14
I use regular Ubuntu, but have installed the Kubuntu and Xubuntu desktop to test it out. But now I never use any of them, so my question is how can I completly remove the Kubuntu and Xubuntu desktop from my computer?

---

### Post by snowpine on 2008-08-14
Here you go:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by sayakb on 2008-08-14
```
sudo apt-get purge kubuntu-desktop
sudo apt-get purge xubuntu-desktop
```
XFCE uses some gnome components as well. I'm not sure if removing the xubuntu-desktop package will remove them or not.

---

### Post by Jompa on 2008-08-14
snowpine's method removed alot of things i wannted to keep, like VLC and stuff, but what can I do about that now

---

### Post by sayakb on 2008-08-14
The uninstallation of xubuntu-desktop might have removed them. Just mark them for reinstallation. If the latest package is there in the pat cache, you may not even need to download them all over again.

---

