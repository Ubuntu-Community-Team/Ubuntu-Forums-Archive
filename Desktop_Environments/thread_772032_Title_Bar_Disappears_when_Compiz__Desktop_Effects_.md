---
title: "Title Bar Disappears when Compiz / Desktop Effects are Enabled"
date: 2008-04-28
forum: Desktop Environments
---

### Post by shinkaide on 2008-04-28
Hi all, just wondering if anybody else is experiencing this and/or has found a solution.

I've Hardy Heron installed on a 1Ghz Pentium 3 with 512MB RAM and a 32MB GeForce II graphics card. The system is very responsive, Compiz works and runs smoothly without any hitches unless I enable a lot of the extra effects (which is of course, crazy and unnecessary).

Everything worked great the first day I've installed and tweaked everything to run (restricted drivers and whatnot). But today, when desktop effects is enabled, the titlebar disappears! Didn't happen yesterday. When I disable desktop effects, the titlebars appear. 

Anyone else going through this? :confused:

---

### Post by Cygnus on 2008-04-28
> **shinkaide said:**
>  But today, when desktop effects is enabled, the titlebar disappears! Didn't happen yesterday.

Sounds like the decorator is dying, at least that was my problem. Try running "kde-window-decorator" and see if they reappear.

---

### Post by shinkaide on 2008-04-29
> **Cygnus said:**
> Sounds like the decorator is dying, at least that was my problem. Try running "kde-window-decorator" and see if they reappear.

Um... even if I use Gnome?

---

### Post by Cygnus on 2008-04-29
> **shinkaide said:**
> Um... even if I use Gnome?

Oh, sorry I was too fast, I was thinking kubuntu. 

I don't use gnome so I am not sure exactly what you could use there. But I think there is something called emerald that can decorate your windows also. Maybe worth a shot.

---

### Post by SweMartin on 2008-04-29
> **shinkaide said:**
> 
Everything worked great the first day I've installed and tweaked everything to run (restricted drivers and whatnot). But today, when desktop effects is enabled, the titlebar disappears! Didn't happen yesterday. When I disable desktop effects, the titlebars appear. 


I have seen exactly the same thing on my configuration. The strange thing is that everything worked perfect for many months on 7.10, but after upgrade this problem (among others) appeared.
I tweaked around a bit with Decoration and finally got it to work.

After this, all kinds of fishy things have occured, such as:
Shift key stops working on the keyboard until I reset keyboard settings.
Found the pink shadows around my windows (found a thread on how to solve that though)
Compiz settings are lost after a while.
FireFox suddenly dies when entering text in any window of FF, such as address bar.
Strange and spooky indeed. Probably worth starting a new thread on....

Ideas on what might be wrong, or where to start looking?

---

### Post by Krydahl on 2008-04-29
First thing to try is make sure that Compiz knows which windows decorator it's using.

Install compizconfig-settings-manager if you haven't already (in synaptic).

Go into Preferences->Advanced Desktop-Effects.

Find Window Decoration and make sure it's ticked. Go into it. In the Command box type "Emerald". See if that fixes things.

---

### Post by VitaminBB on 2008-11-26
Having the same problem here and window decoration is selected ...

Titlebar is present and emerald seems to be running when I login but after awhile it just disappears for some reason ...

---

