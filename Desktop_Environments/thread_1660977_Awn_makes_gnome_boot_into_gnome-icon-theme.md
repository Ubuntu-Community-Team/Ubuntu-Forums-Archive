---
title: "Awn makes gnome boot into gnome-icon-theme"
date: 2011-01-06
forum: Desktop Environments
---

### Post by Lebuin on 2011-01-06
Hi

I have avant-window-navigator in my startup appplications. This apparently causes gnome to use the Gnome icon theme on boot, instead of the Humanity theme I selected in Preferences->Appearance. I just have to go to Preferences-Appearance again to get the Humanity theme back to work (I don't even have to change any settings, just going there is enough.)
When I remove awn from my startup applications, this problem doesn't occur.
How can I solve this?

---

### Post by stinkeye on 2011-01-06
The problem occurs whether awn is loaded at boot or not. It seems to happen randomly.
A lot of people having this problem. [http://ubuntuforums.org/showthread.php?t=1575703]("http://ubuntuforums.org/showthread.php?t=1575703")

 > I just have to go to Preferences-Appearance again to get the Humanity theme back to work (I don't even have to change any settings, just going there is enough.)
By starting Preferences-Appearance you are starting the **gnome-settings-daemon**.

Temp fix is to you run
```
gnome-settings-daemon && pkill nautilus
```

---

### Post by Lebuin on 2011-01-07
Thanks  for that. I started playing around a little with startup applications, and found that if I run the following script on startup instead of the regular awn startup, my problem is solved (I haven't booted a lot of times yet, so I can't be sure if it always works).
```

sleep 3
avant-window-navigator

```

---

### Post by stinkeye on 2011-01-07
It will be back.
When you said AWN was causing the problem I removed AWN from startup and 
on my third reboot the theme reverted.

---

### Post by Lebuin on 2011-01-09
I've booted about 15 times now I think, and it seems like it does work for me. Perhaps something else is causing the problem for you?
EDIT: sometimes it does indeed load the wrong theme, but this is only about once every 10-15 boots.

---

