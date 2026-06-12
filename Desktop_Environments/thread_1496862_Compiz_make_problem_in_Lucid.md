---
title: "Compiz make problem in Lucid"
date: 2010-05-29
forum: Desktop Environments
---

### Post by komitaltrade on 2010-05-29
Compiz changed (for me is not clear how) title bar in all users accounts with enabled compiz to GDM GTK theme titlebar (compiz was enabled in GDM), but also mous is changed (???).

I deleted all users, completely removed compiz (with elements), reinstalled compiz, created new users, but problem is still same.

- What configuration file compiz left after deinstallation?

---

### Post by hok00age on 2010-05-29
> **komitaltrade said:**
> Compiz changed (for me is not clear how) title bar in all users accounts with enabled compiz to GDM GTK theme titlebar (compiz was enabled in GDM), but also mous is changed (???).

I deleted all users, completely removed compiz (with elements), reinstalled compiz, created new users, but problem is still same.

- What configuration file compiz left after deinstallation?

To change cursor theme with compiz enabled:

Run:
```
sudo gedit /etc/alternatives/x-cursor-theme
```

You'll get:
```
[Icon Theme]
Name = Oxygen White
Comment = Oxygen mouse theme. Oxygenize your desktop!
Inherits = oxy-white
```

Name = Cursor theme name (or fill as you want)
Comment = (optional)
Inherits = FOLDER NAME OF YOUR CURSOR THEME (usually saved in /usr/share/icons)

Now, change your cursor theme gnome-appearance-properties

Hope it works
Regards :)

---

### Post by komitaltrade on 2010-05-29
Yes it worked for mouse perfectly (but it is not still clear why I cant change it in gdm appearance), but now problem is solved manually.

---

### Post by Larry Hammer on 2010-05-30
Having the same problem here, but the fix above didn't do the trick for me.
(the fix above did work for some of the themes but not all such as UE 2.5 theme)
what is working for me is to  link the theme folder to default
after I renamed default to defaultbak.
hope to get real fix soon, I don't like messing with the core.
good day:)

---

### Post by hok00age on 2010-05-30
> **Larry Hammer said:**
> Having the same problem here, but the fix above didn't do the trick for me.
(the fix above did work for some of the themes but not all such as UE 2.5 theme)
what is working for me is to  link the theme folder to default
after I renamed default to defaultbak.
hope to get real fix soon, I don't like messing with the core.
good day:)

Is UE 2.5 theme located in /usr/share/icons? the theme must located in that folder to get this trick works and also you might consider rename your theme folder with simple name e.g. ue25

Hope it helps you 
Regards :)

---

