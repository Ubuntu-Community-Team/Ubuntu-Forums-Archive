---
title: "Problem with wallpapers and compiz"
date: 2009-10-10
forum: Desktop Environments
---

### Post by yadayada2 on 2009-10-10
Hello everybody,

I want to use compiz fusion under Xubuntu 9.04/XFCE. So, compiz works fine, but I want to have different wallpapers for each face of the cube.

Thus, I enabled the wallpaper plugin, but it doesn't show the wallpapers I selected. Instead, all faces of the cube show a wallpaper, which is set under Application -> Settings -> Desktop.

Already I have disabled nautilus' show desktop and gnome draw background with gconf-editor. Doesn't matter.

Please tell me, how to successfully enable or better to say use the wallpaper plugin of compiz.

Best regards

Martin

---

### Post by Drakonis on 2012-04-12
I know this is an old thread but in case you didn't find a solution and for anyone else currently experiencing this, you have to stop xfdesktop so it doesn't control the desktop.

```
sudo xfdesktop --quit
```

I haven't logged out/rebooted since doing it so I don't know if I'll have to add a startup command for it or if it'll stay disabled but it solved the problem.

EDIT:  Selecting "save session" when logging out works but I ran into a problem.  Cairo Dock wasn't terminating so I ended up with several instances of it running and sucking up large amounts of memory slowing the entire system down.  I fixed that problem by editing /etc/xdg/xfce4/xinitrc and stopping xfdesktop from loading at all.

I just commented out this line (line 276 in mine)

```
xfdesktop&
```

so it now looks like this

```
#xfdesktop&
```

Deselected "save session" and problem solved, no more multiple instances of cairo dock and system is fast again.

---

