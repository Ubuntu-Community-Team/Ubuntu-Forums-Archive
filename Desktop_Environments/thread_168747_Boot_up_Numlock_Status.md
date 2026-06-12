---
title: "Boot up Numlock Status"
date: 2006-05-01
forum: Desktop Environments
---

### Post by charlie. on 2006-05-01
How do I make Num Lock default to "on"?

---

### Post by iball on 2006-05-01
Install a program called numlockx: ```
sudo apt-get install numlockx
```

I hope this helps
--Ian

---

### Post by christhemonkey on 2006-05-01
[http://ubuntuos.com/2006/04/random-tip-turn-numlock-on-on-boot](http://ubuntuos.com/2006/04/random-tip-turn-numlock-on-on-boot)

Basically
```
sudo apt-get install numlockx 
```

---

### Post by charlie. on 2006-05-01
Wow. Two replies within five minutes of the original post. That IS good support. (No dodgy Windows operating systems have this support...) Thanks all.

Of course, I will only be able to test it once I restart.

---

### Post by louis_nichols on 2006-05-01
Still, just installing the package doesn't do it (happened to me). Now, KDE is easy in this way and has this option in the control center for superuser (under peripherals/keyboard). or gnome you'd have to follow [this]("https://wiki.ubuntu.com/NumLock").

---

### Post by iball on 2006-05-01
[QUOTE=louis_nichols]Still, just installing the package doesn't do it (happened to me). Now, KDE is easy in this way and has this option in the control center for superuser (under peripherals/keyboard). or gnome you'd have to follow [this]("https://wiki.ubuntu.com/NumLock").[/QUOTE]

The KDE setting is not only there for root, it also works for a normal user.

--Ian

---

### Post by louis_nichols on 2006-05-02
[QUOTE=iball]The KDE setting is not only there for root, it also works for a normal user.

--Ian[/QUOTE]

Oh! My bad! Thx for letting me know!

---

### Post by charlie. on 2006-05-04
Just another reason why KDE ROCKS!

It's also about 9 000 000 000 000 000 000% faster than a hypothetical desktop environment that was 9 000 000 000 000 000 000% faster than Gnome!

At least for me.

---

### Post by charlie. on 2006-05-05
In KDE Settings -> Peripherals -> Keyboard, you can change your own personal Numlock preference. This will take effect as soon as you log on. If you want to change the *system* numlock status, you can do this in /etc/kde3/kdm/kdmrc. This will effect the KDM login screen, usefull for people who type passwords with the numeric keypad.

I have no idea how to change the initial numlock status for a text-mode login.

---

### Post by elreteipos on 2007-02-14
[quote="charlie."]If you want to change the system numlock status, you can do this in /etc/kde3/kdm/kdmrc.[/quote]But how?

---

