---
title: "gnome-shell is gone after ALT F2 + 'r'"
date: 2011-10-24
forum: Desktop Environments
---

### Post by v923z on 2011-10-24
Hi All,

I did some changes to my gnome-shell, and in order to save a logout, I just pressed Alt+F2, and then typed 'r'. It seems that was a mistake. The shell is gone now. It is offered at login, and if I choose that, I get to a desktop which doesn't resemble the shell, not even remotely. Even worse, I can't really do anything there (there are no menus, or Cntr+Alt+T won't open a terminal). The only option in these cases is that I press Cntr+Alt+F1, login in the text shell, and reboot the computer from the command line. Anyway, to cut a long story short, could someone tell me how I can recover the gnome-shell? It's really a pit that it is gone now...:( I have the 64-bit version of Oneiric.
Cheers,
v923z

---

### Post by yo_bhan on 2011-10-24
login to unity or classic, and delete gnome shell you're using before. or from tty ```

sudo rm -rf /usr/share/gnome-shell/theme_use
```

and login back to gnome session(gnome shell), make sure you're using gnome shell compatible with gnome 3.2 ;)

---

### Post by v923z on 2011-10-24
Thanks for the reply! That didn't actually help, but since I had to backup the shell settings anyway, I just re-installed it. Still, it is a bit odd, that it went away so easily...
Cheers,
v923z

---

### Post by v923z on 2011-10-24
In the meantime, I have figured out what causes the problem. This happens, when I install the gnome-shell-extenstions-alternative-status-menu. It's a bit odd, because yesterday it was all right...
v923z

---

### Post by yo_bhan on 2011-10-24
try to remove all extension with gnome tweak tool, logout and login.
then install extension again, I hope this worked.

---

### Post by deepclutch on 2012-01-05
> **v923z said:**
> In the meantime, I have figured out what causes the problem. This happens, when I install the gnome-shell-extenstions-alternative-status-menu. It's a bit odd, because yesterday it was all right...
v923z
I am also facing this issue after installing alternative-status-menu. even after removing, commands like "r","lg" etc is not working with gnome-shell. 

Any Idea what happened? I've even reinstalled gnome-shell package.
Solution:
**You have to enable development tools in gsettings for gnome-shell. so, the solution is :**
```

gsettings reset org.gnome.shell development-tools
```

explanation:
Allows access to internal debugging and monitoring tools using the Alt-F2 dialog

TIA+

---

