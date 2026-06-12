---
title: "Problem with fullscreen games"
date: 2009-09-21
forum: Gaming &amp; Leisure
---

### Post by snakeman21 on 2009-09-21
Hi all.  I've been having this problem for a while, but I always assumed that it was my hardware.  But recently, I've tested it on multiple computers with the same OS (Ubuntu 9.04).  This was also a problem for me in previous versions of Ubuntu.  

What happens is I'll be playing a fullscreen game such as Urban Terror, Frets on Fire, or Alien Arena.  I can only play for 15 minutes or so before the game quits to a windowed version (no longer fullscreen) and all controls for it are disabled.  The only way for me to play again is to use the "force quit" applet or "killall program_name" in the Terminal and start over.  I have tried disabling all power options, thinking that this may have been the problem, but with no success.  I tried changing the game settings to windowed mode, but after (approx.) fifteen minutes, all the controls are disabled, just as before.  This is especially frustrating in Urban terror, because I always get killed and taunted when it happens.  

Does anyone else have this issue or know how to fix it?

---

### Post by SuicideSmurf on 2009-09-21
> **snakeman21 said:**
> Hi all.  I've been having this problem for a while, but I always assumed that it was my hardware.  But recently, I've tested it on multiple computers with the same OS (Ubuntu 9.04).  This was also a problem for me in previous versions of Ubuntu.  

What happens is I'll be playing a fullscreen game such as Urban Terror, Frets on Fire, or Alien Arena.  I can only play for 15 minutes or so before the game quits to a windowed version (no longer fullscreen) and all controls for it are disabled.  The only way for me to play again is to use the "force quit" applet or "killall program_name" in the Terminal and start over.  I have tried disabling all power options, thinking that this may have been the problem, but with no success.  I tried changing the game settings to windowed mode, but after (approx.) fifteen minutes, all the controls are disabled, just as before.  This is especially frustrating in Urban terror, because I always get killed and taunted when it happens.  

Does anyone else have this issue or know how to fix it?

Did you disable the screensaver?

---

### Post by themusicalduck on 2009-09-21
I had this problem with a couple of games. I found disabling compiz before playing seemed to fix it.

---

### Post by SuicideSmurf on 2009-09-21
Yes, disable Compiz ....

---

### Post by juancarlospaco on 2009-09-21
**killall gnome-screensaver**

---

### Post by Melcar on 2009-09-21
Disable the screensaver.

---

### Post by snakeman21 on 2009-09-21
Screensaver is already disabled, I did that while disabling power settings, but I will try disable compiz and see what happens.  I'll report back.  Thanks!

---

### Post by Perfect Storm on 2009-09-22
Instead;

```
sudo apt-get install compizconfig-settings-manager
ccsm
```

General ---> General Options

In the general tab, unselect "Unredirect Fullscreen Windows"

---

### Post by snakeman21 on 2009-09-22
Problem solved!  There was on power option that I overlooked.  I disabled it, and played Urban Terror for an hour with no issues.

---

### Post by SuicideSmurf on 2009-09-22
> **snakeman21 said:**
> Problem solved!  There was on power option that I overlooked.  I disabled it, and played Urban Terror for an hour with no issues.

What was the option?

---

### Post by snakeman21 on 2009-09-22
Put display to sleep when idle.

---

### Post by fluxlizard on 2009-09-22
There's a nice little tool for this called compiz switch.

There's a deb for it here: [http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

Once installed, you can find it under Applications-Accessories menu.

I drag it from the menu down to the lower panel left hand corner. Click it once, compiz is off go play urban terror come back to the desktop click it again and compiz is on again. Easy as a click and a click for off and on again for games.

---

### Post by snakeman21 on 2009-09-22
Thanks, I will look into it.

---

### Post by Nevon on 2009-09-23
One workaround for this problem that doesn't involve disabling the screensaver and powersaving options is to use [Caffeine](http://www.blastfromthepast.se/caffeine/index.php?title=Main_Page). With version 0.3 you can specify applications or processes that are disrupted by the screensaver and have Caffeine automatically inhibit the screensaver whenever those apps are running.

---

