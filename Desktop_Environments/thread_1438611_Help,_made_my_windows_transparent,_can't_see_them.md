---
title: "Help, made my windows transparent, can't see them"
date: 2010-03-25
forum: Desktop Environments
---

### Post by cubanitolatino1 on 2010-03-25
Hello! I've been using Ubuntu for about a year now. Yesterday I decide to test drive version 10.04. I was trying to make it look really nice so I decided to add some transparency to the windows, except I made the big mistake of leaving the transparency at 0 and now I can't see any windows nor anything :sad:

Anyone knows how to disable compiz or reset this setting? Remember, I can't see anything on my screen, just the wallpaper and transparent panels without buttons. It has to be by keyboard shortcut or going into some kind of safe mode or something like that. Any help is appreciated, I don't want to have to install it again. Although is not hard to do.

Thank you very much in advance for helping a fellow Ubuntu user.

---

### Post by mr.rhtuner on 2010-03-25
Posting here so hopefully somebody can help you out.

I was in a similar situation a few months back and couldn't find a 'system restore' or a safe mode to undo changes.

good luck

---

### Post by gradinaruvasile on 2010-03-25
Now this is original...
Press alt+f2, type in: "metacity --replace" without the quotes, press enter. This will disable compiz.

---

### Post by 3Miro on 2010-03-25
Goto compiz config settings, use synaptic to install it. Then from System -> Prefs -> Compiz config you can dig into the options and change the transparency settings as well as many other settings.

---

### Post by stinkeye on 2010-03-25
> **gradinaruvasile said:**
> Now this is original...
Press alt+f2, type in: "metacity --replace" without the quotes, press enter. This will disable compiz.

I've seen quite a few of these. Done it myself also.
By default the opacity is set at 0 but it's called window values.
So if you don't change it before adding your windows, instant invisibility.

---

