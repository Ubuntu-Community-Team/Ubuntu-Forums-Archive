---
title: "How does one kill Beryl?"
date: 2006-11-08
forum: Desktop Environments
---

### Post by drummer4lifex on 2006-11-08
Hello,

After extensive searching I've read that turning beryl on and off is as simple as a mouse click, but apparently I'm oblivious to such method. Please help! I'm using the following code to start beryl on the start of the session:
```

dbus-launch beryl --use-cow --force-aiglx
emerald --replace
```

Thanks in advance!

edit: I forgot to mention that my goal is to be able to startup with AIGLX and turn it off when I'm about to play a game, and then when I'm done turn it back on.

---

### Post by po0f on 2006-11-08
drummer4lifex,

I think one of either of the following will work, depending on your DE:
```
$ metacity --replace & # for GNOME
$ kwin --replace & # for KDE, not sure about this one
```

Beryl will still be running in the background, but switching back to your native DE's window decorator should fix it.  When you are done gaming, just restart Emerald (it doesn't require a & at the end):
```
$ emerald --replace
```

---

### Post by d3v1ant_0n3 on 2006-11-08
Do you have the beryl icon in your system tray (I'm still not quite sure what it's called in gnome)? 

If so, swapping WM's is as simple as right-click the icon >'Select Window Manager' >then check 'metacity'/'kwin'/'whatever WM you wish to use'

---

### Post by drummer4lifex on 2006-11-08
Thanks for the replies guys, right now I'm tweaking the windows partition (the comp is for a friend) so I can't test anything yet. However, I know for a fact that the icon in the tray does not exist.

---

### Post by d3v1ant_0n3 on 2006-11-08
You should be able to make it appear with 'beryl-manager' in terminal (also the command I have in sessions to start beryl on boot)

---

### Post by drummer4lifex on 2006-11-09
> **d3v1ant_0n3 said:**
> You should be able to make it appear with 'beryl-manager' in terminal (also the command I have in sessions to start beryl on boot)

Ah! That's what I'm looking for! Thank you very much!

---

