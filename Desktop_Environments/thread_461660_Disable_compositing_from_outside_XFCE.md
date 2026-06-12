---
title: "Disable compositing from outside XFCE"
date: 2007-06-01
forum: Desktop Environments
---

### Post by botulismo on 2007-06-01
I was fiddling with XFCE (I just installed it to try it out on this older laptop. GNOME runs ok but I'd prefer something a little faster as this isn't a speed demon) and I wanted to see if compositing would work when I was fiddling through the "Window Manager Tweak" settings. Well, bad idea. XFCE froze and now whenever I try to start an XFCE session, all I get is a black screen with a mouse. How do I disable the composite manager from outside of XFCE? I would be happy to edit a configuration file if it's possible. I tried opening up the xfce-settings applet but it told me that since metacity was running the applet would have no effect on it... Duh, I'm trying to fix xfce but I can't load it to fix it!

---

### Post by dustigroove on 2007-06-19
[FONT=Arial][SIZE=2][COLOR=Black]Bump.
[/COLOR][/SIZE][/FONT]

---

### Post by eight10man on 2007-07-18
(my first ubuntu post!!)

i had done exactly the same thing on my old revitalised vaio n505 with xfce4

shutdown windowmanager (black screen + cursor) with Ctrl+Alt+Backspace

goto to settings directory
```
cd ~/.config/xfce4/mcs_settings
```

edit the wmtweaks file to disable compositing
```
sudo nano wmtweaks.xml
```

disable compositing by changing the line 'UseCompositing' to:
```
<option name="Xfwm/UseCompositing" type="int" value="0" />
```

press Ctrl+X and save the file with the same given filename

start xfce4
```
startxfce4
```

---

### Post by agonified on 2008-05-05
> **eight10man said:**
> (my first ubuntu post!!)

i had done exactly the same thing on my old revitalised vaio n505 with xfce4

shutdown windowmanager (black screen + cursor) with Ctrl+Alt+Backspace

goto to settings directory
```
cd ~/.config/xfce4/mcs_settings
```

edit the wmtweaks file to disable compositing
```
sudo nano wmtweaks.xml
```

disable compositing by changing the line 'UseCompositing' to:
```
<option name="Xfwm/UseCompositing" type="int" value="0" />
```

press Ctrl+X and save the file with the same given filename

start xfce4
```
startxfce4
```

Thank you very much buddy! You saved me from digging for this setting for an hour! Much appreciated...

---

