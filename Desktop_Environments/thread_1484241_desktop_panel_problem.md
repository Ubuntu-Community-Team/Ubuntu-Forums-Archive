---
title: "desktop panel problem"
date: 2010-05-15
forum: Desktop Environments
---

### Post by KruSuPhy on 2010-05-15
hey everyone im running ubuntu 9.10, and i have a bunch of music i listen to while i play modern warfare 2. my limewire decided to not play one day, so i brought out some rhythm box music player that was on my system, and then later while i was listening, it seems like all of my music comes up on my panel at the top and there's like 150 music icons right there, and i can't click on applications or places or anything, when i do some music video player comes up and it's getting really frustrating. can someone help?

---

### Post by mhgsys on 2010-05-15
open a terminal and type:

```
gconftool-2 --recursive-unset /apps/panel

```
and restart gdm after that

in console (Ctrl+Alt+f1 ,f2, f3, etc) type

```
sudo /etc/init.d/gdm stop
```
```

sudo /etc/init.d/gdm start

```

---

