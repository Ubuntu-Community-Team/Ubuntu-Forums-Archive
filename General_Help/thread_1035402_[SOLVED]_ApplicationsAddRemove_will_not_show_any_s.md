---
title: "[SOLVED] Applications/Add/Remove will not show any software and menu bar"
date: 2009-01-09
forum: General Help
---

### Post by 73ckn797 on 2009-01-09
Intrepid 8.10 32bit.

I have no software or menu bar in the Add/Remove window under Applications. Do not know what happened. I rarely use it so I do not know when this began. 

Any suggestions of where to find switches or other ways to check into this?

See screenshot attached.

---

### Post by unutbu on 2009-01-09
By going to System>Pref>Main menu, you will find that "Add/Remove..." is linked to /usr/bin/gnome-app-install.
How about open a terminal, run```

/usr/bin/gnome-app-install
```
and see what error messages are printed.

---

### Post by namdung on 2009-01-09
```
sudo apt-get --reinstall install gnome-app-install
```

---

### Post by 73ckn797 on 2009-01-09
> **unutbu said:**
> By going to System>Pref>Main menu, you will find that "Add/Remove..." is linked to /usr/bin/gnome-app-install.
How about open a terminal, run```

/usr/bin/gnome-app-install
```and see what error messages are printed.

Results of */usr/bin/gnome-app-install*

```
** (gnome-app-install:6544): WARNING **: return value of custom widget handler was not a GtkWidget
```

I uninstalled the Widgets but no change. I installed it the other day. The screenshot I sent was also what resulted running the terminal code you gave.

---

### Post by 73ckn797 on 2009-01-09
> **namdung said:**
> ```
sudo apt-get --reinstall install gnome-app-install
```


That was the ticket my friend. Thanks (so marked). Though I would like to know what caused the issue. See post about the screenlets/widget stuff. Could that have messed something up? It was not a Canonical supported app.

---

### Post by rburkartjo on 2009-03-08
nam wish i had seen your answer a few weeks ago had the same problem with ubuntu 8.10 and had to to an upgrade to 9.04 beta to get add/remove to work.i just had the same thing happen
to ubuntu 9.04 a5 and it fixed this works great and i have bookmarked it/tks

---

