---
title: "Mysterious Missing System Tray Icon"
date: 2016-01-16
forum: Desktop Environments
---

### Post by Terone on 2016-01-16
I'm running Kubuntu 15.10. This problem came when I first installed kubuntu but since it was a graphical error, I didn't pay it any mind. Does anyone have a clue in how to fix this? There's just a blank space inbetween the other icons and moving icons around doesn't seem to fix it.

[ATTACH=CONFIG]266795[/ATTACH]

Is it a kubuntu bug? Or some ancient ghost inhabiting my computer?

---

### Post by andrei90 on 2016-01-17
Hi there,

If you right click on it, what does it say in the Title ?

---

### Post by Erik1984 on 2016-01-18
I'm still on KDE4 but when I right click on the system tray itself I have the option "System Tray Settings". There I can see which items are active and also show/hide them, maybe one application is not showing the icon correctly and you can hide it. IIRC there was a problem with some applications that use an older system tray : [http://blog.martin-graesslin.com/blog/2014/06/where-are-my-systray-icons/](http://blog.martin-graesslin.com/blog/2014/06/where-are-my-systray-icons/) Don't know if this is a problem in Kubuntu 15.10

---

### Post by andrei90 on 2016-01-20
You could try [one of these methods]("http://www.addictivetips.com/ubuntu-linux-tips/three-ways-to-restart-gnome-without-rebooting-system/") to restart your panel, everything should get back to normal afterwise.
Method 1:
**Ctrl**[COLOR=#000000][FONT=Arial]&#8211;[/FONT][/COLOR]**Alt**[COLOR=#000000][FONT=Arial]&#8211;[/FONT][/COLOR][B]Backspace

[/B]Method 2:
[B]sudo /etc/init.d/gdm restart

[/B]Method 3:
**killall gnome-panel**

---

### Post by Terone on 2016-01-23
Well, I just updated kubuntu, in Plasma 5.5.3 the problem has been resolved.

---

### Post by Terone on 2016-01-23
Heres what it looks like now. I'm digging the new icons in the latest update. 

[ATTACH=CONFIG]266918[/ATTACH]

---

