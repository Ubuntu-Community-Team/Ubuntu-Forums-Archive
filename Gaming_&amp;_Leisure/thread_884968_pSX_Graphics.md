---
title: "pSX Graphics"
date: 2008-08-09
forum: Gaming &amp; Leisure
---

### Post by dragonboss on 2008-08-09
I've got the pSx playstation emulator and it works fine but the video output appears on top of everything else so even the menus at the top have to be selected by guessing.I even displays on top of the screen saver.Please help!

---

### Post by FranMichaels on 2008-08-09
Sigh, intel driver issue, lack of redirected direct rendering. Happens will all opengl stuff when compositing is turned on... 

Disable compiz compositing when playing the game will solve the issue until we get that new driver... :D

System -> Preferences -> Appearance -> visual Effects to none

Or install fusion icon. There are various methods posted on the forum to toggle compiz/metacity compositing on and off...

---

### Post by dragonboss on 2008-08-09
I've installed the fusion icon, so what do i have to do to stop that?

---

### Post by tjwoosta on 2008-08-09
> Disable compiz compositing when playing the game will solve the issue until we get that new driver...

System -> Preferences -> Appearance -> visual Effects to none

Or install fusion icon. There are various methods posted on the forum to toggle compiz/metacity compositing on and off... 

yes disabling compiz will do the trick but there is a better way of doing it

if you were to go to System-Preferences-Appearance and disable the visual effects it would reset all of you compiz configurations (you would need to reconfigure everything when you restart compiz)
(also its time consuming)

the best and easiest way that i have found to temporarily disable compiz is from the terminal

to disable compiz do this
```
metacity --replace
```

to re-enable compiz do this
```
compiz --replace
```

(doing it this way will keep all of your compiz configureations the same when you re-enable it)

---

### Post by FranMichaels on 2008-08-09
> **dragonboss said:**
> I've installed the fusion icon, so what do i have to do to stop that?

Right click on the icon, select Window Manager, choose metacity.

---

### Post by dragonboss on 2008-08-09
thanks

---

### Post by dragonboss on 2008-08-09
> **FranMichaels said:**
> Right click on the icon, select Window Manager, choose metacity.
thanks

---

### Post by dragonboss on 2008-08-24
Umm.. switching the window manager so often is causing some malfunctions so i'll just use it like that.

---

### Post by GSZX1337 on 2008-08-24
> **FranMichaels said:**
> There are various methods posted on the forum to toggle compiz/metacity compositing on and off...

What do you think of Compiz Switch?

---

### Post by dragonboss on 2008-08-25
Thanks, I'll check it out.

---

### Post by benhur99ph on 2008-11-20
For me what I did is install simple-compiz-config-settings-manager. This will add the "custom" entry on the visual effects tab. Select it and configure your compiz. After that when I play pSX. I just right-click on the screen and change the visual effects to "None". After playing, I re-enable compiz buy selecting "Custom". It retains all of my settings.

---

### Post by tjwoosta on 2008-11-20
> For me what I did is install simple-compiz-config-settings-manager. This will add the "custom" entry on the visual effects tab. Select it and configure your compiz. After that when I play pSX. I just right-click on the screen and change the visual effects to "None". After playing, I re-enable compiz buy selecting "Custom". It retains all of my settings.


that works now, but at the time when this thread was new it wouldn't have

---

### Post by benhur99ph on 2008-11-23
> **tjwoosta said:**
> that works now, but at the time when this thread was new it wouldn't have

Ahh, I see. Well I just thought I'd share it.

---

### Post by dashnak on 2008-11-30
I seem to have a problem running pSX in my acer aspire one. When I run it in Linux, it is extremely slow, just as if it were rendering by software, that doesn't happen in windows. ePSXe runs just fine. I have disabled compiz. My video card is, as far as I remember, and intel 950. Any thoughts on the matter? I realy want to get this working.

---

