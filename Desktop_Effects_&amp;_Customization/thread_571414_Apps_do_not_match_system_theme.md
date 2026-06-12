---
title: "Apps do not match system theme"
date: 2007-10-09
forum: Desktop Effects &amp; Customization
---

### Post by rettie on 2007-10-09
Hey everybody! Just a small problem, certain applications (Firefox, gaim and synaptic package manager) do not match the system theme I'm using, but instead have oldish grey scroll bars, buttons etc. Does anyone know how I would go about changing this? I'm just using 'polyester' as a style, but changing this has no effect on the cosmetics of the programs. Oddly, sometimes when I boot up all the apps will have the nice scrollbars and buttons etc. It's like its teasing me haha, help please!! I'm new to this so be gentle :)

Cheers

---

### Post by Forlong on 2007-10-09
Are you using Xgl?

Try running:
```
gnome-settings-daemon
```

---

### Post by rettie on 2007-10-09
Yes I am, I'm also using KDE 3.5, FF 7.04, sorry should have specified that! Right so I ran that and got this output:

xrdb:  "*Label.background" on line 243 overrides entry on line 170
xrdb:  "*Text.background" on line 249 overrides entry on line 211
xrdb:  "*Label.foreground" on line 255 overrides entry on line 171
xrdb:  "*Text.foreground" on line 261 overrides entry on line 212

loving the help man! Any ideas how to correct this without running the daemon every time?

Cheers

---

### Post by FuturePilot on 2007-10-09
Well if you're using KDE you need to make sure you tell KDE to use your KDE theme over GTK apps. Kmenu>System Settings>Appearance (I think. Haven't used KDE in a while) There's a thing in there about GTK apps. If it's already set to that, try undoing it and redoing it.

---

### Post by Forlong on 2007-10-09
If you're on KDE then you need to run a similar command for that, I guess.
Sorry, I never really used KDE...

But as soon as you find out, you just need to add the command to your start up programs.
Sorry again, don't know where this is to be set in KDE - hopefully some Kubuntu user comes along to help us out.

---

### Post by rettie on 2007-10-09
Sorted! I just downloaded a gtk theme engine from synaptic and ticked some boxes. Cheers guys! :D

---

