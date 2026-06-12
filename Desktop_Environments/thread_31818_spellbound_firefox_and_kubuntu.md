---
title: "spellbound firefox and kubuntu"
date: 2005-05-04
forum: Desktop Environments
---

### Post by jlv on 2005-05-04
I am trying to install the spellbound extension for Firefox 1.0.3.  Apparently this needs to be done as root and the spellbound site and the ubuntu parts of this forum recommend doing:

```
sudo -H firefox
```

which results in:

```
$ sudo -H firefox
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firefox-bin:12573): Gtk-WARNING **: cannot open display:
```

any suggestions?

---

### Post by buldir on 2005-05-05
Try gksudo instead of sudo.

---

### Post by mlmurray on 2005-05-05
Or you could first type (as a normal user):  ```
xhost +localhost
```
Then, do: ```
sudo -H firefox
```

---

### Post by jlv on 2005-05-05
for the record ```
xhost +localhost
``` didn't work (for me) with sudo, however ```
gksudo -S firefox
``` did work, although I had to first install gnome-sudo.  So thanks!  :-P

---

### Post by crazybill on 2005-05-06
worked for me too. Thanks

---

