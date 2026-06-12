---
title: "[SOLVED] Background Wallpaper does not show up"
date: 2008-12-24
forum: General Help
---

### Post by jackmetal on 2008-12-24
Hi All,

I have a strange problem that has popped up a time or two for me.  The first time, I just created a new user, reconfigured everything like I like it and copied everything over.  Well, it's happened again, and instead of just doing that, I'm trying to determine the exact issue instead.  :-)

I'm running Ubuntu 8.10 on this system.  Gnome Desktop and I've been using Desktop Drapes as my wallpaper switcher.  Currently my desktop wallpaper doesn't show up any longer.  I've stopped Desktop Drapes and even tried setting the wallpaper via the normal 'right-click, change desktop wallpaper' option, but it still doesn't show up.  

Any ideas at all?

Thanks,
JM

---

### Post by gettinoriginal on 2008-12-24
In your terminal type

metacity --replace

---

### Post by northern lights on 2008-12-24
> **jackmetal said:**
> I've stopped Desktop Drapes and even tried setting the wallpaper via the normal 'right-click, change desktop wallpaper' option, but it still doesn't show up.
What does "show up" instead?
You have panels and all, but the screen's black?
Does nautilus work correctly otherwise (nautilus draws the desktop, it's not a question of the WM)?

---

### Post by jackmetal on 2008-12-24
Thanks.  Tried that, but it didn't work.  This is definitely a strange one, I hope we can figure it out.  :-)

I've tried numerous things thus far: rebooted (same issue), unloaded Desktop Drapes and stopped it from starting then rebooted (same issue), tried restarting desktop drapes and selecting a new wallpaper, tried selecting a new wallpaper from a right-click - change wallpaper, and even via nautilus right-click - set as wallpaper.  I keep just getting a blank screen with no wallpaper.  If I log in as another user, it's working fine.  

This thing has me stumped.

---

### Post by jackmetal on 2008-12-24
> **northern lights said:**
> What does "show up" instead?
You have panels and all, but the screen's black?
Does nautilus work correctly otherwise (nautilus draws the desktop, it's not a question of the WM)?

Yeah, everything else shows up fine (panels, applets, etc.).  Just the wallpaper doesn't.  It's just a blank screen (which I can change the color of).

---

### Post by northern lights on 2008-12-24
Could you have accidentally set nautilus to not draw the desktop?

Run```
gconf-editor
``` and check the "Show Desktop" radio box under /apps/nautilus/preferences/

[EDIT]
> **jackmetal said:**
> It's just a blank screen (which I can change the color of).
This is even stranger. Where do you alter the color?
[/EDIT]

---

### Post by jackmetal on 2008-12-24
> **northern lights said:**
> Could you have accidentally set nautilus to not draw the desktop?

Run```
gconf-editor
``` and check the "Show Desktop" radio box under /apps/nautilus/preferences/

[EDIT]

This is even stranger. Where do you alter the color?
[/EDIT]


Ok, that was it.  Thank-You very much, you are a life-saver!! 
Somehow, nautilus had been set to not draw the desktop.  

Now, if I can determine what is changing it.  It's happened a few times in the past (only on my 8.10 systems).

---

### Post by gettinoriginal on 2008-12-24
The next time you log in, at the log in screen, choose options, and choose gnome session.  :P

---

### Post by northern lights on 2008-12-24
> **jackmetal said:**
> Now, if I can determine what is changing it.  It's happened a few times in the past (only on my 8.10 systems).
I've never used the Drapes-thingy, maybe it's buggy. I have no idea how this could accidentally happen.

Anyhow, merry Christmas.

---

### Post by jackmetal on 2008-12-24
> **northern lights said:**
> I've never used the Drapes-thingy, maybe it's buggy. I have no idea how this could accidentally happen.

Anyhow, merry Christmas.


That's an excellent point.  I'll keep drapes on some of my systems and try a new wallpaper switcher on a couple others and see if it's Drapes causing it.

Thanks again for the help, and Merry Christmas to you too!!

---

