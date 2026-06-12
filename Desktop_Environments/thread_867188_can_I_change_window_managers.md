---
title: "can I change window managers?"
date: 2008-07-22
forum: Desktop Environments
---

### Post by dodle on 2008-07-22
How do I change the default window manager?  I really enjoy using xfce4 on my p3, it runs very smooth, but I hate the xfwm4 window manager.  Can I change it so that I can try out some others?  

Thanks in advance.

---

### Post by Potatoj316 on 2008-07-22
You can, you will have to install a bunch of packages and I think the take up a lot of space so you will probably want to remove the old ones but from there I dont know how to.

---

### Post by sisco311 on 2008-07-22
you can change the default window manager in /etc/xdg/xfce4-session/xfce4-session.rc
(wmii, openbox, fluxbox, blackbox ...)

---

### Post by dodle on 2008-07-22
> **sisco311 said:**
> you can change the default window manager in /etc/xdg/xfce4-session/xfce4-session.rc
(wmii, openbox, fluxbox, blackbox ...)

Nothing changed when I edited xfce4-session.rc, however, I was able to switch window managers by simply killing the xfwm4 process via the taskmanager then running the command for the new window manager (openbox).  When I do this, my desktop icons dissapear.  Is there a way to get openbox, or other WMs, to manage the desktop?

---

### Post by jviscosi on 2008-07-22
Most (all?) of the lightweight window managers don't natively support icons on the desktop, but there are a bunch of add-ons (of varying heaviness) that will do it.  Some I can think of off the top of my head are fbdesk, idesk, rox-desktop (I think), and gdesklets (using "Just An Icon").  I'm sure others will have more suggestions.  FWIW, I used to use fbdesk, but now I just don't use desktop icons at all.

---

### Post by urukrama on 2008-07-23
> **dodle said:**
> Nothing changed when I edited xfce4-session.rc, however, I was able to switch window managers by simply killing the xfwm4 process via the taskmanager then running the command for the new window manager (openbox).  When I do this, my desktop icons dissapear.  Is there a way to get openbox, or other WMs, to manage the desktop?

Make sure you still have xfdesktop running. You can run it independently from the window manager.

---

### Post by xdarkxanarchyx on 2008-07-27
You can also use Thunar or PCManFM to manage the desktop for icons, they're both fairly lightweight. Nautilus will do it to if you really want...

---

### Post by dodle on 2008-07-27
> **xdarkxanarchyx said:**
> You can also use Thunar or PCManFM to manage the desktop for icons, they're both fairly lightweight. Nautilus will do it to if you really want...

Can you explain how to set those up?  (it's pretty late, I don't want to think right now)

---

### Post by xdarkxanarchyx on 2008-07-27
```
 sudo apt-get update && sudo apt-get install pcmanfm 
```

PCMan FM:
Go to edit -> preferences and click on the desktop tab. It'll give you an option to show file icons on the desktop and to set wallpaper and/or choose colors. If you open the advanced section you can show the menus provided by your WM when you click the desktop.

Thunar:
I guess I lied about this part, sorry. I thought it was possible but, I think it will be in the future.

You can use feh.
```
 sudo apt-get install feh 
```
This is a lightweight image viewer that can also draw the background. You'd have to use it in combination with idesk or something similar. Make sure you run these all at startup.

```
 feh --bg-scale /path/to/your/wallpaper.png 
```

**--bg-tile, --bg-seamless, and --bg-center**
are other options for the wallpaper

---

