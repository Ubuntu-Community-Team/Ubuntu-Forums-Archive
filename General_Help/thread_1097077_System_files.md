---
title: "System files???"
date: 2009-03-15
forum: General Help
---

### Post by MissKitty on 2009-03-15
Ok this is driving me up the wall. Ubuntu doesn't seem to have a program file where all it's programs are, like windows. If for some reason you need a program and it's missing from your desktop you can always go in and find it in the programs file. Well I can't find anything! I just got myself an AWN (the Mac dock) and I'd like to add launchers to it such as firefox, emesene, open office and so on. Where in the world are these things in system files?

---

### Post by OutOfReach on 2009-03-15
Ubuntu has a different way of storing programs than Windows.
Most executables are contained in /usr/bin

---

### Post by Declanthedork on 2009-03-15
You can't expect the world to revolve around Windows. Linux operates differently.

---

### Post by drs305 on 2009-03-15
> **MissKitty said:**
> Where in the world are these things in system files?

You can usually find the location of the app's executable file with:
```

which *[COLOR="DarkRed"]appname[/COLOR]*

```
Example: which gimp

You can find the location of the app's files with:
```
whereis *[COLOR="DarkRed"]appname[/COLOR]*
```
Example: whereis gimp

---

### Post by MissKitty on 2009-03-15
> **Declanthedork said:**
> You can't expect the world to revolve around Windows. Linux operates differently.

Now that's why I am asking, thanks.](*,)

---

### Post by MissKitty on 2009-03-15
But like I said before, I'm trying to add launches in awn-manager but it's not working. Like what do I put in for the command. I tried clicking "open" and found the executable but it wont let me open the executable. Am I doing this wrong?

---

### Post by Yashiro on 2009-03-15
Just list which apps you are trying to add.
Someone will probably give you the lines to enter for the command.

Or you can think about it a bit. The posts above have told you how to do it.

Firefox, for example, is /usr/bin/firefox

---

### Post by Tibuda on 2009-03-15
You can try to drag the launcher from your Applications menu to the dock. I'm not sure if it works with AWN, as I use another dock (Docky), but I believe it does.

---

