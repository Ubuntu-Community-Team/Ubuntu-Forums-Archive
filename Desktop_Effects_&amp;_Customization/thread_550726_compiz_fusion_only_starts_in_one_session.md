---
title: "compiz fusion only starts in one session"
date: 2007-09-14
forum: Desktop Effects &amp; Customization
---

### Post by ZipoTe on 2007-09-14
Hi guys!!

My problem is easy:

I have two users with their respective sessions. In both I have "compiz --replace -c emerald" at the startup but... it only works in one of them, in the other I have to run iby pressing alt+F2 and typing the command.  why? i don't know.... :confused:

any ideas??

---

### Post by praet on 2007-09-14
Long in to each account and check the session configuration:
```
gnome-session-properties
```
or System > Preferences > Session

Check for .desktop files in each user's home directory.  
```
ls -al ~/.config/autostart
```

Also check the gnome-session default:
```
/usr/share/gnome/default.session
```

Check that the actual selected session from the login screen (Options > Gnome) are the same.

Also, if you are using the new compiz fusion  from Amaranths repo, the run command -c will not work, use this instead:
```
compiz --replace && emerald --replace
```

---

### Post by ZipoTe on 2007-09-14
```
compiz --replace && emerald --replace
```

thanks!! that worked!! :D

---

### Post by praet on 2007-09-14
great!

---

