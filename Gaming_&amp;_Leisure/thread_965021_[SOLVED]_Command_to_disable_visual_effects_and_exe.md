---
title: "[SOLVED] Command to disable visual effects and execute game"
date: 2008-10-31
forum: Gaming &amp; Leisure
---

### Post by thetor on 2008-10-31
I am playing a game (a native Linux game, not using wine) that works fine when visual effects are disabled. When effects are enabled however, the graphics get garbled. Of course, it is easy to disable or enable effects by using the GUI tool at system -> preferences -> appearance, but that gets a little cumbersome when I have to do it every time I execute the game (and I don't want to disable effects permanently).

I am looking for a way to disable visual effects, execute the game and finally re-enable effects when the game exits, all in a single command. That way I can modify the game's application menu shortcut to do it all automatically.

Apparently, you can combine multiple commands on a single line by using the & character. Another way to achieve the same result would be to create a simple shell script.

Any input on how to enable/disable visual effects in this way would be greatly appreciated.

I am running Ubuntu 8.10 on a laptop with Intel GMA950 (945GM chipset).

---

### Post by crazyfuturamanoob on 2008-10-31
Try compiz-switch. It does the job.

```
sudo apt-get install compiz-switch
```

Switch on/off compiz with only one mouse click.

---

### Post by derekr44 on 2008-10-31
You can also get fusion-icon and use it to change your window manager on the fly from your system tray.

---

### Post by derekr44 on 2008-10-31
Stop effects:
> metacity --replace

Start effects:
> /usr/bin/compiz --replace ccp & /usr/bin/emerald --replace &

Don't run it in a terminal though.  As soon as the terminal closes, your switch will stop and it will go back to your default setting.

---

### Post by thetor on 2008-10-31
> **crazyfuturamanoob said:**
> Try compiz-switch. It does the job.
```
sudo apt-get install compiz-switch
```
Switch on/off compiz with only one mouse click.
It works, but compiz-switch isn't included in the repo. Instead of apt-getting it, I had to dowload it from [here]("http://forlong.blogage.de/entries/pages/Compiz-Switch").

> **derekr44 said:**
> Stop effects:
metacity --replace
Start effects:
/usr/bin/compiz --replace ccp & /usr/bin/emerald --replace &
Don't run it in a terminal though.  As soon as the terminal closes, your switch will stop and it will go back to your default setting.
Works too. The emerald commands fails though, as emerald isn't included by default (and I haven't installed it manually). Instead, the default compiz setup on 8.10 uses a GTK window decorator (compiz-gnome). This window decorator is started automatically with compiz if present on the system.

So, I made the following two shell scripts:
```
compiz-switch
<game executable>
compiz-switch
```

```
metacity --replace &
<game executable>
/usr/bin/compiz --replace ccp &
```

They both seem to work equally well. Great, just what I was looking for! Now I can just point the game's shortcut to the script and I have the behaviour that I wanted.

> **derekr44 said:**
> You can also get fusion-icon and use it to change your window manager on the fly from your system tray.
Yup, I find it practical to keep it running in the system tray for when I want to switch manually.

Thanks guys!

---

