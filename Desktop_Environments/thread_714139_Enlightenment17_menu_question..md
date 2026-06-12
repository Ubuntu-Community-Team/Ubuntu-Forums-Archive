---
title: "Enlightenment17 menu question."
date: 2008-03-03
forum: Desktop Environments
---

### Post by Freddy on 2008-03-03
Greetings all.

I was trying to build my own E17 setup only using KDE applications and kcontrol to theme them. Now I have stumbled onto a small (read big) problem, It's my menu, it doesn't pick up ant of my installed applications.

I tried to
> cp /etc/xdg/menus/kde-applications.menu ~/.config/menus/applications.menu

but it didn't help much, 3 applications found their way onto my e17 menu. After a closer look at the 'kde-applications-menu' I found out that it picks up 'applications-kmenuedit.menu' which is probably where my applactions are configured since  I used 'kmenuedit' to configure it. 

How do I intergrate this into my Enlightenment17 menu?

/Thanks

---

### Post by smartboyathome on 2008-03-04
I don't think you can. E17 follows the same menu structure as GNOME, so unless you can convert the menu layout to GNOME's menu layout, I don't think it will work.

---

### Post by Freddy on 2008-03-07
> **smartboyathome said:**
> I don't think you can. E17 follows the same menu structure as GNOME, so unless you can convert the menu layout to GNOME's menu layout, I don't think it will work.
Yeah I have come to this conclusion as well, I have seen that some people have managed to integrate their KDE menus into their e17 ones but I don't think it's worth the hassle. So I did it the ugly way but at least now it works.

---

### Post by angry_johnnie on 2008-03-08
So what happens if you run this?

```
sudo update-menus
```

Or --if you don't have the menu package installed--

```

sudo apt-get install menu && sudo update-menus
```

That has always worked for me :-)

---

### Post by Freddy on 2008-03-08
That was on of the first things I tried and nope that doesn't work. thanks anyways.

---

