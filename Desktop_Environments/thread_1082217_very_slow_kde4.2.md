---
title: "very slow kde4.2"
date: 2009-02-27
forum: Desktop Environments
---

### Post by natman on 2009-02-27
I am using kde4.2 in kubuntu 8.10 it works fine but its just very slow on the desktop like poping up and down windows. I have turned off all the desktop effects. XP is way faster compared to it, I am using a dell optiplex gx 270 ( i think it has an intel extreme 2 graphics  ). Am i asking too much from it, or am i missing somthing?

Thanks:

---

### Post by Name change on 2009-02-27
Well the data is scarce, but let's try the most obvious thing at first...
go to .kde/share/config and find everything kwin related and delete it...
Maybe "kill" kwin first, but I advise to "kill" it just before the actual deleting of files. you "kill" it with:
```
kquitapp kwin
```

Hope that helps. If not try some of those optimization tips.
Or you can get the best help on [kde forum]("http://forum.kde.org/")

---

### Post by khelben1979 on 2009-02-27
The new version of KDE 4.2 is probably not mature enough, maybe? Debian chose to stick with KDE 3.5.10 in their latest stable release.

---

### Post by Name change on 2009-02-27
> **khelben1979 said:**
> The new version of KDE 4.2 is probably not mature enough, maybe? Debian chose to stick with KDE 3.5.10 in their latest stable release.
No it is. I'm using KDE4.2 full time and it's "rock solid"
Had no major problem with it.
Only if you count the missing shutdown button from log-off screen a major problem I don't.
there's always:
```
sudo shutdown -h now
```

---

### Post by khelben1979 on 2009-03-02
> **Primo&#382 said:**
> No it is. I'm using KDE4.2 full time and it's "rock solid"
Had no major problem with it.
Only if you count the missing shutdown button from log-off screen a major problem I don't.
there's always:
```
sudo shutdown -h now
```

Or going to a text console and press: ctrl + alt + delete. Also works.

---

