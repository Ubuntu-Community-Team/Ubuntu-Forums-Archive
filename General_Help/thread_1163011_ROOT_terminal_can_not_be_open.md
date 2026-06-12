---
title: "ROOT terminal can not be open"
date: 2009-05-18
forum: General Help
---

### Post by guitar_man on 2009-05-18
I cant open my root terminal...please do help

---

### Post by stefangr1 on 2009-05-18
what you can do is first open a terminal:

Press Alt+F2 to open the run dialog, and then give the command
xterm to open a terminal

To switch to root you can do sudo sh and provide your password. It is however recommended to give each command separately with "sudo" in front of it. This gives you the possibility to give commands as a normal user as if you were root.

---

### Post by guitar_man on 2009-05-18
when I open Application>>System Tool>>Root Terminal it wont open

---

### Post by michy99 on 2009-05-18
I read somewhere the other day that this is a bug in Jaunty. Apparently, it is not high on the list to fix either.

---

### Post by Yellow Pasque on 2009-05-18
Just open a normal terminal and:
```
sudo -i
```

As for why the Root Terminal menu option no longer works, see: [http://bugzilla.gnome.org/show_bug.cgi?id=564649](http://bugzilla.gnome.org/show_bug.cgi?id=564649)

---

### Post by michy99 on 2009-05-18
I found the other thread on this that I remembered:

[http://ubuntuforums.org/showthread.php?t=1143972](http://ubuntuforums.org/showthread.php?t=1143972)

---

### Post by guitar_man on 2009-05-18
so this is a bug???

---

### Post by Yellow Pasque on 2009-05-18
> **guitar_man said:**
> so this is a bug???
In the sense that the command won't run, no, it's not a bug (unless you're an old-school, elitist l-user that despises things like dbus and you believe that dbus IS a bug).

In the sense that Ubuntu shouldn't use that particular command for the Root Terminal option, yes, it's a bug.
In the sense that it could output a more descriptive and helpful error, yes, it's a bug.

---

