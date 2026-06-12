---
title: "Gnome-&gt;Xfce"
date: 2006-09-06
forum: Desktop Environments
---

### Post by Inhumane on 2006-09-06
I installed Ubuntu the other day but already have it configured to my needs, is there a way to upgrade it to Xfce without losing my settings and such?

---

### Post by PathSpace on 2006-09-06
You can have XFCE installed alongside GNOME.  Just do "aptitude install xubuntu-desktop" as root (or use sudo if that's your thing ;) ).

---

### Post by aysiu on 2006-09-06
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by Inhumane on 2006-09-06
Hehe, ok I installed it and don't like it, how can I remove it? I tried doing apt-get remove xubuntu-desktop but it says it's in use even though I'm in Gnome. Will it also remove the programs it came with?

---

### Post by aysiu on 2006-09-06
If you installed it with these two commands: ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
``` then you can remove it with this command: ```
sudo aptitude remove xubuntu-desktop
```

If you installed it with *apt-get* or Synaptic, you can't uninstall it easily.

You can try this workaround, though:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

