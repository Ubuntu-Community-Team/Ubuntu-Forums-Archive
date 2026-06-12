---
title: "How to uninstall HUD on ubuntu 12.04"
date: 2012-05-22
forum: Desktop Environments
---

### Post by woxuxow on 2012-05-22
How can i uninstall HUD on ubuntu 12.04
i don`t want to disable HUD i just want to uninstall it completely

---

### Post by Isaacgallegos on 2012-05-22
That would mean customization. That's frowned upon in 12.04.

---

### Post by woxuxow on 2012-05-22
> **Isaacgallegos said:**
> That would mean customization. That's frowned upon in 12.04.

Isn`t there any easy way to uninstall HUD

---

### Post by Hylas de Niall on 2012-05-22
I'm not sure why anyone would want to? It stays out of your way until it's invoked.
Is it causing you issues?

---

### Post by wilee-nilee on 2012-05-22
> **MustafaJF said:**
> Isn`t there any easy way to uninstall HUD

Not even listed as HUD in synaptic, as the gangster would say "forget about it"

You have to be very careful about just removing packages, dependencies usually are associated.

---

### Post by Enigmapond on 2012-05-22
The HUD is all part of Unity. If you don't want to use it. Use the Gnome Classic fallback. There is no way to purge the Hud without it affecting other things as well.

---

### Post by papibe on 2012-05-22
Hi MustafaJF.

As we chat on ubuntuforums, and for reference:

The easiest way is to disable HUD is by blanking its shortcut:
```
Open System Settings > Keyboard > Shortcuts > Launchers > Key to show HUD 
```

Source: [this]("http://askubuntu.com/questions/122209/how-do-i-modify-or-disable-the-huds-use-of-the-alt-key").

Regards.

---

### Post by woxuxow on 2012-05-24
> **papibe said:**
> Hi MustafaJF.

As we chat on ubuntuforums, and for reference:

The easiest way is to disable HUD is by blanking its shortcut:
```
Open System Settings > Keyboard > Shortcuts > Launchers > Key to show HUD 
```

Source: [this]("http://askubuntu.com/questions/122209/how-do-i-modify-or-disable-the-huds-use-of-the-alt-key").

Regards.

Yeah i remember you 
thank you
i forgot about it 
i changed the hotkey of enabling HUT in that way you mentioned
so there is no easy way to remove HUD

---

### Post by zombifier25 on 2012-05-24
> **MustafaJF said:**
> Yeah i remember you 
thank you
i forgot about it 
i changed the hotkey of enabling HUT in that way you mentioned
so there is no easy way to remove HUD

HUD is a part of Unity itself. I don't see you should be concerned with removing the HUD anyway. Neither does it slow down Unity when kept, nor does it make it any faster when removed.

NOTE: I can't check (because I'm on Classic and currently downloading a really big file) but there's an executable that might be responsible for HUD: /usr/lib/indicator-appmenu/hud-service

---

### Post by woxuxow on 2012-05-24
yeah
and there is deamon too
i`m busy now but i`ll remove theme to see what will happen and tell the issue here

---

