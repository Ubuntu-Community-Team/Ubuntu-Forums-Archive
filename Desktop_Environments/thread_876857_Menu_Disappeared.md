---
title: "Menu Disappeared"
date: 2008-08-01
forum: Desktop Environments
---

### Post by Asheboy on 2008-08-01
My menu (applications, places, system) and the panel that holds your open windows has disappeared after I restarted. Here is a screen shot of what I mean...

[http://img361.imageshack.us/img361/6797/screenshotph1.png]("http://img361.imageshack.us/img361/6797/screenshotph1.png")

If someone could help me it would be great :).

---

### Post by K2712 on 2008-08-01
The panels have probably just locked up for some reason.

Use Alt+F2 to bring up the run box and enter:

```
killall gnome-panel
```

This should cause the panels to restart.  If they still won't come back, try
```
gnome-panel
```

in the run box and that should bring them back up.

---

### Post by Herb Taylor on 2008-08-01
I have a similiar problem with the Gnome desktop.  I am running 8.04 using both the Gnome Desktop and the KDE desktop. Somehow I did something to the Gnome desktop.  Now when Gnome starts all I can get is my home files.   All of my ICONS have disappeared such as Thunderbird, Gramps, Opera, ETC.  I can't find a way to get the regular desktop back.  The KDE is working fine.  It looks like a screen shot but I don't remember doing it.

Herb Taylor

---

### Post by Asheboy on 2008-08-01
I had to reinstall gnome-panel. Try that :).

---

### Post by CharlesTowers on 2008-08-01
Well, you can allways add again the panel and add the default applets. They go like these: Menu-->Firefox launcher, Evolution launcher, Help (Yelp)--------> Change User, notification area, time and date, and logout (exit)

---

### Post by K2712 on 2008-08-01
> **Asheboy said:**
> I had to reinstall gnome-panel. Try that :).

Just out of curiosity, what were you doing before you restarted?  Did you edit any config files, or adjust a lot of settings on the panel?

---

### Post by sebastian.gasparetti on 2009-08-23
> **K2712 said:**
> The panels have probably just locked up for some reason.

Use Alt+F2 to bring up the run box and enter:

```
killall gnome-panel
```This should cause the panels to restart.  If they still won't come back, try
```
gnome-panel
```in the run box and that should bring them back up.

Perfect! The Menu appeared after "killall gnome-panel". 
When I tried with "gnome-panel" the following message appeared "Cannot register the panel shell: there is already one running."
Thanks!

---

