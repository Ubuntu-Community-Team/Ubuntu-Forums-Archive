---
title: "I have lost keyboard shortcuts"
date: 2006-03-06
forum: Desktop Environments
---

### Post by Alex^77 on 2006-03-06
I have lost some keyboard shortcut. 
This is my situation: 

[[img]http://img330.imageshack.us/img330/9821/screenshot6al.th.jpg[/img]](http://img330.imageshack.us/my.php?image=screenshot6al.jpg)

Exactly, I have lost all settings in Windows Managment!!

What can I do for restore the shortcut??

Can I copy and paste a copy from other PC??

---

### Post by WackToMack on 2006-03-06
Do you know how it happened?  Maybe if you know how, we can point you in the right direction.  But If you don't, I'm useless, because I'm stumped...lol. :D

---

### Post by Alex^77 on 2006-03-06
Yes, the problem has appared when I have INSTALLED -> TRY -> UNINSTALLED Expocity (the clone of MAC Exposè for GNOME).

After this, My shortcut don't work!!

I have try to watch in Gconf -> Apps -> Metacity and comparing this folder with other installation of Ubuntu, I have found MORE DIFFERENCE (in My PC there isn't some folders and some parameter).

So I have tryed to copy this folder in my PC, but the problem persists!!

Now I hope to have been more clear!!

---

### Post by Alex^77 on 2006-03-06
UP :rolleyes:

---

### Post by Alex^77 on 2006-03-06
UP :rolleyes:

---

### Post by awi on 2006-03-24
[QUOTE=WackToMack]Do you know how it happened?  Maybe if you know how, we can point you in the right direction.  But If you don't, I'm useless, because I'm stumped...lol. :D[/QUOTE]

I lost my keyboard shortcuts too, yesterday I Installed some "*cairo*" updates, with the standard applet, and that was the only change in my Ubuntu. I suspect that it has something to do with it.
I have also created a brand new user, to see if there was something wrong with my configurations, and got the same.
I have checked the gconf's metacity tree too, and the keyboard shortcuts are gone. :(

---

### Post by aysiu on 2006-03-24
It sounds as if that program may have messed with some files in the /etc/gconf/gconf.xml.defaults/schemas/apps/metacity folder or the /etc/gconf/gconf.xml.defaults/apps/metacity folder.

You can try ```
sudo apt-get reinstall metacity
```

---

### Post by awi on 2006-03-26
[QUOTE=aysiu]It sounds as if that program may have messed with some files in the /etc/gconf/gconf.xml.defaults/schemas/apps/metacity folder or the /etc/gconf/gconf.xml.defaults/apps/metacity folder.

You can try ```
sudo apt-get reinstall metacity
```[/QUOTE]

Problem solved! Thanks a lot** aysiu**, the exact command line I used  was

```
# apt-get --reinstall install metacity
```

---

