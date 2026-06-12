---
title: "Checkgmail and pidgin tray icons invisible in Unity"
date: 2012-02-13
forum: Desktop Environments
---

### Post by Elitist on 2012-02-13
Hey

I have been fighting with checkgmail and pidgin, because after a while their tray icons disappear in unity. Also the black message boxes don't show up with pidgin (e.g. when someone writes a message to me), when the task tray icons are not visible. Weirdly enough, when I switch between workspaces, the icons are visible during the switching. systray-whitelist is set to "['all']", so it shouldn't be a problem. the icons work just fine in the fallback session of gnome. I am using Ubuntu 11.10

Anyone else experiences anything similar?

---

### Post by Edemoe on 2012-02-25
The same problem here (with Pidgin and Remmina). Please share your findings if any...

---

### Post by ivanhelguera on 2012-06-13
see the last post in [http://ubuntuforums.org/showthread.php?t=1710616](http://ubuntuforums.org/showthread.php?t=1710616)
the solutions is to enter 
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```
in the terminal

---

