---
title: "Crashed  Desktop"
date: 2006-12-21
forum: Desktop Environments
---

### Post by dontgetshocked on 2006-12-21
My desktop wont start anymore, it just comes up with this enlightenment whatever that  is.
How can I recover from command rescue mode?
It seems to have lost the metacity desktop
I tried using metacity at the command prompt but it did not work,

---

### Post by iamhugeinjapan on 2006-12-21
Do you get no graphical interface at all?  Enlightenment is a desktop environment like GNOME and KDE, were you using that before it broke?

To check/reinstall Metacity try

```
sudo aptitude install metacity
```

Alternatively, to restore a default Ubuntu set up you could try 

```
sudo aptitude install ubuntu-desktop
```

Something more serious may be going on though. It's hard to decipher from your post.

---

