---
title: "one user gnome, another user kde"
date: 2006-09-02
forum: Desktop Environments
---

### Post by Second_Player on 2006-09-02
is there any way to do this, i've been wanting too but i wasnt sure if it would change everything and i have things set up how i like them, i would just like to be able to experiment with kde.

---

### Post by angustia on 2006-09-02
you can try installing kde-core (a minimal kde) and kde-i18n-** (if you want it in other language than english).

one thing:

the gnome loggin manager is gdm, and gnome shutdown or restart your computer through it. The kde loggin manager is kdm, but kde can work with both. if you install kdm (well, and put it as default loggin manager), gnome will lose the shutdown and reboot buttons from the logout screen.

---

### Post by Crooksey on 2006-09-02
Log in as the user you want for gnome

```
 sudo gedit ~/.xinitrc
```

Make the file look like

```

#!/bin/sh/

exec gnome-session

```

Then logout, and log in as the user you want for KDE

```
 sudo gedit ~/.xinitrc
```

Make the KDE file look like
```

#!/bin/sh/

exec startkde

```

Now startx will be diffrent for each user.

---

### Post by Second_Player on 2006-09-02
cool, just about to log out and try kde for the first time, hope i did everything correctly

---

### Post by Second_Player on 2006-09-02
it didnt work, i installed the kde core and changed the .xinitrc files for the users but it still just came back up with gnome when i logged in.  i'm also not quite sure what you meant by startx.

---

### Post by aysiu on 2006-09-02
Each user has her own preferences. You don't need to manually change .xinitrc files.

Use GDM for the login manager. When one user logs into Gnome, that'll be fine. When the other user logs into KDE, she'll be asked if that should be her default desktop environment. If she says "make default," it won't in any way affect the other user.

---

### Post by Second_Player on 2006-09-02
this may be a stupid question, but how do i log into kde then?

---

### Post by aysiu on 2006-09-02
You pick it from the session menu.

Look at the screenshots at the bottom of this page:
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

---

### Post by Second_Player on 2006-09-02
thank you

---

