---
title: "Installed GNOME over KDE"
date: 2010-08-03
forum: Desktop Environments
---

### Post by sparta2 on 2010-08-03
Hello. I know this may not exactly be the right place for this but I am fairly new to linux and everything I google alot of the answers come from this forum, So I figured Id ask for some help.
I am currently running Backtrack 4 and while surfing google I read about a method to install GNOME over my KDE.
It told me I could do it with one simple command using apt get ubuntu desktop or such.
Well to say the least it worked fine, however I can not login as root anymore on BT. and being a newby i never added another account to BT, just my main root : toor.
When I try to login to GNOME it will not let me returning an error about I can not login as root from this screen.

Any help?\

THanks

---

### Post by Yuri sss on 2010-08-03
You should absolutely **never, ever** login as root! [-X

Instead, if you net to run an app with root privileges, do the following:

**Kde:** Right-click the desktop and select "Run command", then enter e.g.:
```
kdesudo kwrite
```
Replace "kwrite" with whatever app you need to run as root.

**Gnome:** Press Alt+F2 for the Run dialog and enter e.g.:
```
gksu gedit
```
Replace "gedit" with whatever app you need to run as root.

---

### Post by sparta2 on 2010-08-03
> **Yuri sss said:**
> You should absolutely **never, ever** login as root! [-X

Instead, if you net to run an app with root privileges, do the following:

**Kde:** Right-click the desktop and select "Run command", then enter e.g.:
```
kdesudo kwrite
```
Replace "kwrite" with whatever app you need to run as root.

**Gnome:** Press Alt+F2 for the Run dialog and enter e.g.:
```
gksu gedit
```
Replace "gedit" with whatever app you need to run as root.
Thanks , but see I can not log in at all because the only account I have is a root account that was built into backtrack.

---

