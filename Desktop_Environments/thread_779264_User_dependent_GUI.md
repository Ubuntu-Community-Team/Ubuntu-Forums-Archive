---
title: "User dependent GUI?"
date: 2008-05-02
forum: Desktop Environments
---

### Post by curtis1552 on 2008-05-02
I want to use KDE4, my wife Gnome, and my Mother-in-law likes KDE 3.5 and doesn't want to fool with 4 yet.

How can I set it up to automatically load a different GUI when users login (no by selecting the GUI under sessions)? It currentlt boots to the default of KDE.

I installed Kubuntu 8.04 (the KDE version, not the KDE4 version) on the system.

---

### Post by kerry_s on 2008-05-02
you could try just making a ~/.xinitrc or ~/.Xsession with the de you want to start.

or

you'd probably use a script to kill what ever current de was running and start the one you want, stick the launcher in ~/.bash_profile to load at login.

not really sure, never tried something like that. you'd better wait for others to give ideas.

---

### Post by Xiong Chiamiov on 2008-05-03
A little Googling got me [this]("http://www.ocforums.com/showthread.php?p=5604974").  See what you can figure out, and if you have problems, feel free to ask us.

---

### Post by curtis1552 on 2008-05-10
Wow, you sure googled a post I made on the only other forum I look at. I got fed up with Kubuntu - I'm not used to it yet - and am switching to Ubuntu and adding KDE, then switch to KDE4 when it's supported a bit better.

---

### Post by angry_johnnie on 2008-05-11
Actually it's much much easier than that.  Just log in and choose whichever session you want, then when it asks you whether you want to set it as default, choose yes.  It's the same for all users.  My desktop computer has three user accounts, one with Gnome as default, one with kde, and one with E17.  And that was the way it was set up.

---

### Post by Xiong Chiamiov on 2008-05-11
> **curtis1552 said:**
> Wow, you sure googled a post I made on the only other forum I look at. I got fed up with Kubuntu - I'm not used to it yet - and am switching to Ubuntu and adding KDE, then switch to KDE4 when it's supported a bit better.
lol, I totally didn't notice at all.

And for what johnnie said, yeah, that's quite a bit easier...

---

