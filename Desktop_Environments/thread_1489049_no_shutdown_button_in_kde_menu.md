---
title: "no shutdown button in kde menu"
date: 2010-05-20
forum: Desktop Environments
---

### Post by sgerdan on 2010-05-20
Hi there,
 My problem is I can't shutdown directly from kde, I can only log out to gdm. How can I fix this?

---

### Post by angry_johnnie on 2010-05-20
well, if you had ubuntu-desktop and then installed kde on top of it, and decided to keep gdm instead of kdm, it would make some sense.

when you shutdown, you're doing it via gdm, but then you have kde.

a quick and dirty fix (not even sure if there's a clean fix), is to edit the sudoers file

```
sudo visudo
```


and include:

```
%admin ALL=NOPASSWD: /sbin/shutdown
```

and then create a new item in your menu that runs

```
sudo shutdown -h now
```

then, it will shutdown.

you could do this without editing the sudoers file, of course, but then you would be asked for your admin password every time you tried to shut down the machine.

hope that helps to some extent. :)

---

### Post by JustinR on 2010-05-20
If I remember, some settings in KDE will allow you to disable shutdown and other various other "leave" buttons.

Try finding the KDE settings dialog and see if anythings there.

---

