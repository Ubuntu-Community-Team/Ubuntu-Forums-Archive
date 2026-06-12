---
title: "System tray icons changed"
date: 2015-03-10
forum: Desktop Environments
---

### Post by milen2 on 2015-03-10
I wanted to try some desktop environments, but I didn't like them so I decided to remove them. Apparently I made a mistake somewhere and I did not remove everything, because the tray icons from the old DEs remain. How can I fix that ? Here is a screenshot: 

[IMG]http://i.imgur.com/LmEwl2p.png[/IMG]

---

### Post by ajgreeny on 2015-03-10
I imagine that a new DE you installed has brought with it a new icon theme so you may be able to go back to what you had before by changing icon theme back to original. Unfortunately as I don't use unity I do not know how you change such a thing, so you will have to search for yourself.

---

### Post by Frogs Hair on 2015-03-10
If you have not logged out and back in since removing the other desktop/s try that. Open system settings > appearance >and apply one of the default icon sets or install the unity tweak tool and try from there. Removing unwanted icon sets is possible from the synaptic package manager if you know which ones to remove. Synaptic is not installed by default and changes may not appear until logout or reboot.

---

### Post by CantankRus on 2015-03-10
...can also reset to default icons via terminal...
```
dconf reset /org/gnome/desktop/interface/icon-theme
```

---

### Post by milen2 on 2015-03-11
> **CantankRus said:**
> ...can also reset to default icons via terminal...
```
dconf reset /org/gnome/desktop/interface/icon-theme
```
Didn't work :(

---

### Post by CantankRus on 2015-03-11
What does this output in terminal?
```
dconf read /org/gnome/desktop/interface/icon-theme
```

---

