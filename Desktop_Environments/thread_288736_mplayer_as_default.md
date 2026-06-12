---
title: "mplayer as default"
date: 2006-10-30
forum: Desktop Environments
---

### Post by hraposo on 2006-10-30
How can I make mplayer as default player for web pages in Edgy.

---

### Post by pay on 2006-10-30
You need a plugin called mplayerplug-in to be able to use it in firefox```
sudo aptitude install mozilla-mplayer
```should install it

---

### Post by hraposo on 2006-10-30
I already install mozilla-mplayer but totem still as default player

---

### Post by hraposo on 2006-10-30
Problem solved

---

### Post by hraposo on 2006-10-30
The problem is not completly solved. the mplyar open embebed on web page but stops without play? What can I do?

---

### Post by hraposo on 2006-10-30
If I copy the link and open mplayer then its plays fine... Is this a firefox problem?

---

### Post by seelk on 2006-10-30
I fixed this by manually removing the libtotem* files from this directory:  /usr/lib/mozilla-firefox/plugins.  This way the only movie plugin Firefox references is mplayer*.

I did this because trying to remove totem-mozilla results in removing ubuntu-desktop.  I don't think I want the latter removed...  :p

---

