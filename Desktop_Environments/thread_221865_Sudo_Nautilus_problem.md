---
title: "Sudo Nautilus problem"
date: 2006-07-24
forum: Desktop Environments
---

### Post by seshomaru samma on 2006-07-24
```
sesho@kubuntu:~$ sudo nautilus
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(nautilus:16271): Gtk-WARNING **: cannot open display:

```

this problem might be related to what I did [here]("http://ubuntuforums.org/showthread.php?t=216193")

---

### Post by philippe_carlo on 2006-07-24
```
gksudo nautilus
```

---

### Post by seshomaru samma on 2006-07-24
thanks but.....
```
sesho@ubuntu:~$ gksudo nautilus
GTK Accessibility Module initialized
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(nautilus:19817): Gtk-WARNING **: cannot open display:
application finalize called

```

---

