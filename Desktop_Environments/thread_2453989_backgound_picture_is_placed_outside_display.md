---
title: "backgound picture is placed outside display"
date: 2020-11-20
forum: Desktop Environments
---

### Post by xhudik on 2020-11-20
Hi there,
I have encounter a strange problem. I have successfully changed background picture. All looks fine:
```
gsettings list-recursively org.gnome.desktop.background
org.gnome.desktop.background picture-options 'wallpaper'
org.gnome.desktop.background primary-color '#000000000000'
org.gnome.desktop.background show-desktop-icons false
org.gnome.desktop.background picture-uri 'file:///home/tom/team/thj.jpg'
org.gnome.desktop.background color-shading-type 'solid'
org.gnome.desktop.background draw-background true
org.gnome.desktop.background picture-opacity 100
org.gnome.desktop.background secondary-color '#000000000000'
```
However, my background doesnt work and looks like:

[ATTACH=CONFIG]287395[/ATTACH]

Strange is that when I click on Activities, my background picture appear:

[ATTACH=CONFIG]287394[/ATTACH]

Once I finish Activities, background picture is gone and my background is black again.

Any idea what might be wrong?


thx, Tomas

---

### Post by deadflowr on 2020-11-20
Your colors settings look to be too long, it should be six characters long.
like #000000, or #FFFFFF
try resetiing them to the system defaults.
```
gsettings reset org.gnome.desktop.background primary-color 
gsettings reset org.gnome.desktop.background secondary-color 
```

I'm not sure if that's the issue, but it's something I noticed.

---

### Post by xhudik on 2020-11-23
thanks @deadflowr

i tried:
```
gsettings list-recursively org.gnome.desktop.background
org.gnome.desktop.background picture-options 'zoom'
org.gnome.desktop.background primary-color '#023c88'
org.gnome.desktop.background show-desktop-icons false
org.gnome.desktop.background picture-uri 'file:///usr/share/backgrounds/gnome/adwaita-timed.xml'
org.gnome.desktop.background color-shading-type 'solid'
org.gnome.desktop.background draw-background true
org.gnome.desktop.background picture-opacity 100
org.gnome.desktop.background secondary-color '#5789ca'
```

but problem is still there. If I click in Activities I can see background picture, otherwise I dont.
Really strange

---

