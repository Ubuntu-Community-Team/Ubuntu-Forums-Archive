---
title: "Media keys"
date: 2008-02-02
forum: Debian
---

### Post by p_quarles on 2008-02-02
I just switched my desktop to Lenny (have been using Etch on my home server for a while). Nearly everything went perfectly.

The one exception is my media keys. In Ubuntu, xev registered them as events like "X86vol_up" for the "increase volume" key. In Debian, however, they don't seem to work as smoothly. Attempting to use them for shortcuts within apps does nothing, and xev registers them as numeric keycodes.

Is there a package that would allow these keys to function?

---

### Post by mojoman on 2008-02-02
> **p_quarles said:**
> I just switched my desktop to Lenny (have been using Etch on my home server for a while). Nearly everything went perfectly.

The one exception is my media keys. In Ubuntu, xev registered them as events like "X86vol_up" for the "increase volume" key. In Debian, however, they don't seem to work as smoothly. Attempting to use them for shortcuts within apps does nothing, and xev registers them as numeric keycodes.

Is there a package that would allow these keys to function?

I set up my media keys in the desktop environment and window managers I got installed (KDE for my girlfriend and fluxbox for me). Works perfectly.

---

### Post by Whiffle on 2008-02-02
Xmodmap should be able to do that I should think, as long as they've got numeric keycodes.

---

### Post by p_quarles on 2008-02-03
Okay, I'll try playing with Xmodmap. I was just kind of hoping that since Ubuntu (=based on Lenny/Sid) recognized them out of the box, there was some sort of Debian package that enabled this.

---

### Post by Whiffle on 2008-02-03
From what I've seen, Ubuntu has *alot* of behind the scenes work done to make such things work.  Just poke around in the /etc/acpi directory on an ubuntu system versus a standard Debian install.  Thats where most of the magic happens (or so it seems).  When I used Slackware I managed to sort of copy some of that functionality over but never really fully got it working (which is why I've got feisty on the laptop now...because *everything* works perfectly out of the box, except networkmanager).

---

### Post by p_quarles on 2008-02-03
Thanks, that's a good idea. I do still have Ubuntu on my laptop, so I'll have a peek at that directory there.

---

### Post by cknight on 2008-02-03
p_quarles, some window managers (e.g. fluxbox) allow keycodes to be used as keybindings.  Could this give you the functionality you need?

---

### Post by p_quarles on 2008-02-03
> **cknight said:**
> p_quarles, some window managers (e.g. fluxbox) allow keycodes to be used as keybindings.  Could this give you the functionality you need?
I did not know that. I'm using Fluxbox, so that should work just fine. Thanks for the tip.

---

### Post by cknight on 2008-02-03
> **p_quarles said:**
> I did not know that. I'm using Fluxbox, so that should work just fine. Thanks for the tip.

No problem.  If you have any other Fluxbox keys questions, try here [http://ubuntuforums.org/showthread.php?t=617812]("http://ubuntuforums.org/showthread.php?t=617812")

---

