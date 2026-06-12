---
title: "KDE control center from command line"
date: 2011-06-25
forum: Desktop Environments
---

### Post by pathorn on 2011-06-25
I recently updgraded to natty, and I found myself needing to change a few KDE settings.

How do I get to KDE's control center if I'm using Gnome? I'm talking about the window with all the nice icons, or whatever you get when you open the K menu and click "Settings". I used to be able to type "kcontrol", but that broke when Ubuntu switched to KDE4.

I was informed of "kcmshell4", but there are roughly 90 modules, and being a visual person, I prefer to have the nice icons to help me remember which section to visit, and I don't want to try about 5 commands to find what I'm looking for.

If the answer is to start an instance of "kicker" and click on the "K menu", then I'll do that, but I would be surprised if there was no way to open what I want from the command line without needing the whole kicker and menu around.

---

### Post by Zorael on 2011-06-25
The new KConfig is **System Settings**, which is sort of a misnomer as practically all settings therein pertain to KDE. It has its own **[systemsettings](apt://systemsettings)** package.

If you need to change a specific config value (say, in a script), you could use **kwriteconfig**.

---

### Post by SeijiSensei on 2011-06-25
In case it wasn't clear from Zorael's post, just type "systemsettings" at a prompt.

---

### Post by pathorn on 2011-06-26
Awesome, thanks--This is exactly what I was looking for!  I had looked through all commands with a "k" in front--but I guess plain systemsettings didn't occur to me.

---

