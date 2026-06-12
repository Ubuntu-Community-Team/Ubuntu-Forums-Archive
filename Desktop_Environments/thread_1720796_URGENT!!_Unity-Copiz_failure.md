---
title: "URGENT!! Unity-Copiz failure"
date: 2011-04-03
forum: Desktop Environments
---

### Post by agarner98 on 2011-04-03
I was messing around with my new 11.04 Natty Beta when I decided to change a few things on my Compiz. Idecided to enable my dektop cube, disabled Unity support (which I've done before without problems) so I could temporarily fix a few of the conflicts. All of a sudden, my launchers and panels re gone, so I 'switch user' then it logs me out. I tried logging into it again with the same problems. I switche the user *AGAIN *(fruitlessly) trying to log out and back in to the GNOME environment. I did so, but my panels were missing now, too. I tried doing a fresh restart but it took me straight to Unity (which also no longer worked.) How do I fix this? I'm writing a book and ALL of the files are on there...
 
EDIT: My laptop is set up to log into Unity by itself.

---

### Post by kerry_s on 2011-04-03
in 11.04 unity, compiz draws the panel & launcher. you need to switch to classic gnome session at the log in screen.
press ctrl+alt+f1
run sudo killall gdm
that should throw you to the log in screen.

---

### Post by agarner98 on 2011-04-03
Thank you, I will try that and re-enable Unity support. People on Facebook were giving me useless answers like 'Don't upgade to beta' or 'get a mac'...lol

---

### Post by agarner98 on 2011-04-03
No juice... it just takes me to a terminal screen (like you see at boot-up). Is there a certain command I need to type in to start gnome in that prompt?:confused:

---

### Post by Copper Bezel on 2011-04-03
Yeah, he was telling you to run that command,

```
sudo killall gdm
```

at the console. There's a simpler way, though. Go back to Ctrl+Alt+F7 (your graphical login) and hit Ctrl+Alt+T. It'll bring up a terminal (whether you're in Unity or Classic Gnome.) Type ccsm, and it'll launch Compiz again, so that you can re-enable Unity.

If you can resist the temptation to mess with the cube, do so. It conflicts with the Unity plugin (not in terms of keybindings - they use different layouts for virtual desktops, so it's difficult to get both at the same time and requires a hack.)

I don't know why you didn't have panels in Gnome Classic - they're unrelated.

---

