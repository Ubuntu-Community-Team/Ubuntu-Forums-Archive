---
title: "Virtual XSession Gnome classic"
date: 2014-02-26
forum: Desktop Environments
---

### Post by bobbyallen9292 on 2014-02-26
I am trying to open virtual gnome classic session  on TTY8 using 

```
startx gnome-session -- :1 vt8
startx gnome-session --session=gnome-classic -- :1 vt8
```

I am unable to get it to start. I've been messing around with other virtual terminals as well but i would like to get gnome classic to work.
i have used several others and been able to get those sessions to load correctly like kde, blackbox, fluxbox...

```
startx startkde -- :1 vt8
startx blackbox -- :1 vt8
startx fluxbox -- :1 vt8
```

i have also tried

```
startx gnome-classic -- :1 vt8
```
that didn't work either.

any help would be appreciated.

---

### Post by bobbyallen9292 on 2014-02-26
I was able to get this to work using 
```
gsettings set org.gnome.desktop.session session-name ubuntu-2d
```

---

