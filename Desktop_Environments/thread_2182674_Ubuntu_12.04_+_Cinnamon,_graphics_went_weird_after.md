---
title: "Ubuntu 12.04 + Cinnamon, graphics went weird after update (I guess it was the update)"
date: 2013-10-22
forum: Desktop Environments
---

### Post by Jedit Ojanen on 2013-10-22
Hi,

I'm not sure what caused the graphic bugs but it happened after restarting my computer so I assume some of the installed updates did that. Problem is that gui theme seems to be changed to something else that it supposed to be. For example, Nautilus doesn't show folder icons, folders look like unknown files. Terminal doesn't have icon either. When I try to change theme in "Appearance" from ambient to some other nothing happens. Also windows theme has changed. I would like to get all back to normal simple gui what it was supposed to be. Could anyone help?

Also, I got a problem that my computer is trying to connect to wireless network between certain periods of time. This got nothing to do with gui but it's another issue I'm having. So it opens a window every time showing username and password. If I leave my computer on for longer periods it might open dozens if not hundreds of those windows. All I can do then is to restart my computer.

---

### Post by Jedit Ojanen on 2013-10-23
Bump

---

### Post by Jedit Ojanen on 2013-10-28
pump

---

### Post by MoebusNet on 2013-10-28
+1

Ubuntu 11.10 upgraded to 12.04 with Cinnamon DE installed last year. One of the changes I noted after the Cinnamon update was that some gnome dependencies appeared to be removed, but didn't appear to affect Gnome DE at the time. Now my wallpaper is gone, windows don't want to close and display doubled and changing desktop environments is wonky.

Suggestions, anyone?

[ATTACH=CONFIG]247337[/ATTACH]

---

### Post by MoebusNet on 2013-10-28
Well, I solved my issues by removing Cinnamon:

```
 sudo apt-get purge cinnamon 
```

---

### Post by Jedit Ojanen on 2013-11-21
Anyone could help? This is still bothering me... :(

---

