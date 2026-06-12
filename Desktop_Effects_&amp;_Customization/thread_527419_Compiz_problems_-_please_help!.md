---
title: "Compiz problems - please help!"
date: 2007-08-16
forum: Desktop Effects &amp; Customization
---

### Post by Sparky222B on 2007-08-16
```

compiz --replace
Checking for Xgl: not present.
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity

```

That's the error output I get. How do I fix this?

---

### Post by sdowney717 on 2007-08-16
looks like a video driver issue, what is your card?
Try the ENVY installer for ATI and Nvidia cards.

---

### Post by Sparky222B on 2007-08-16
ATI Radeon X1950, and I have the driver installed and enabled under restricted - i shouldn't need to try Envy

---

### Post by sdowney717 on 2007-08-16
Checking for Xgl not present

are you in an XGL session or a gnome session?

[https://help.ubuntu.com/community/Beryl/ATI/Feisty](https://help.ubuntu.com/community/Beryl/ATI/Feisty)

have you set up XGL and at login select XGL session?

(ignore the beryl stuff)

---

### Post by Sparky222B on 2007-08-16
Okay, I did that.

Now I get:

```

sparky@SparkyPC:~$ compiz --replace
Checking for Xgl: present.
Converting gconf plugin list: ''
Checking for nVidia: not present.
Checking for Xgl: present.
Enabling Xgl with fglrx ATi drivers...

(gtk-window-decorator:14698): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:14698): Wnck-WARNING **: Unhandled action type (nil)
Segmentation fault (core dumped)

(gtk-window-decorator:14698): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:14698): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:14698): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:14698): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:14698): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:14698): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:14698): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:14698): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:14698): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:14698): Wnck-WARNING **: Unhandled action type (nil)

```

and the keys set in my config app don't do anything.

---

### Post by psyopper on 2007-08-16
Try opening the CompizConfig Settings Manager (System - Preferences) and setting the backend (button in the lower left corner) to "flatfile." Then try launching Compiz again.

---

### Post by Sparky222B on 2007-08-17
Worked, thanks.

---

