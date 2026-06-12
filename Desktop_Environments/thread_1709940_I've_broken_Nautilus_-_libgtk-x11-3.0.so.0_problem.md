---
title: "I've broken Nautilus - libgtk-x11-3.0.so.0 problem - fixable?"
date: 2011-03-19
forum: Desktop Environments
---

### Post by infinitejones on 2011-03-19
OK, hands up, I've been fiddling, and I've broken Nautilus. My fault entirely. No lectures please! ;)

I'm using Natty and I enabled a PPA in Ubuntu Tweak (the Gnome 3 one, I think) that I didn't really understand, to see what it would do. Well you have to fiddle, don't you, otherwise you never learn anything.

Anyway, so now Nautilus won't start:

```
nautilus: error while loading shared libraries: libgtk-x11-3.0.so.0: cannot open shared object file: No such file or directory
```

Simple question - is it fixable (if so - how?) or is it easier just to re-install Ubuntu? (I have a separate /home partition so that's not the end of the world.)

---

### Post by infinitejones on 2011-03-21
Bump

Any thoughts?

---

### Post by sonicb00m on 2011-03-23
i have this problem today after running the regular updates on the standard nautilus.

---

### Post by fishears on 2011-03-23
Fix this by opening a terminal and type:
cd /usr/lib
sudo ln libgtk-x11-2.0.so.0 libgtk-x11-3.0.so.0

and enter your root password

---

### Post by infinitejones on 2011-03-24
Hmmm. This didn't work for me personally, but I should add that I've already also used the "defaultthunar" script on [https://help.ubuntu.com/community/DefaultFileManager]("https://help.ubuntu.com/community/DefaultFileManager") to install and use Thunar (from XFCE) as default, since Nautilus wasn't working for me.

If I run the script to change the default back to Nautilus, I just get no response at all when running nautilus from the command line - no error messages, just a new command prompt and no Nautilus window.

Never mind - I actually don't mind using Thunar - I'll probably wait until Natty is released and then just do a fresh install.

---

### Post by voku1987 on 2011-03-25
> **fishears said:**
> Fix this by opening a terminal and type:
cd /usr/lib
sudo ln libgtk-x11-2.0.so.0 libgtk-x11-3.0.so.0

and enter your root password

thx, worked for me ... :)

---

### Post by christo91 on 2011-03-25
Thanx. It's work for me:-)

---

