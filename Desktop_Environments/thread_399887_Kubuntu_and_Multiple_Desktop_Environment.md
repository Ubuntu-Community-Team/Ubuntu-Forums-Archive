---
title: "Kubuntu and Multiple Desktop Environment"
date: 2007-04-02
forum: Desktop Environments
---

### Post by tim042849 on 2007-04-02
Hi:
I prefer KDE, but I would like to experiment with FVWM. I have ordered the latest
kubuntu. I prefer using runlevel 3. In the past, I have set up some scripts to allow
me to start fvwm or KDE at will. (on RH 9.0 and slack 10.0)

I'd like to do the same with kubuntu.

Any tips?
Examples: Installation options
                Pointers to related threads or URLs on this subject 

Thanks
Tim

---

### Post by aysiu on 2007-04-02
I don't know what all this business is about run levels, but if you install the *fvwm* package, you should be able to select before you log in whether to use FVWM or KDE (just select which "session," then type in your username and password).

---

### Post by rillip on 2007-04-03
IIRC, runlevel three is basically terminal access.  So.. what difference does it make which gui is running?

---

### Post by tim042849 on 2007-04-03
> **rillip said:**
> IIRC, runlevel three is basically terminal access.  So.. what difference does it make which gui is running?
:) It appears that our Ubuntu Master Roaster only uses runlevel 5, I can live with either
runlevel.

I just wanted to know if there might be 
installation options
 that might make setting up a multiple desktop environment 
easier
 OR 
harder. 
Let me repose my question, 'cuz I haven't finished my first cup of coffee:

Different display managers are available for runlevel 5 (gui login).
 For examples for RH see:
[http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/ref-guide/s1-x-runlevels.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/ref-guide/s1-x-runlevels.html)
When I do the installation will I be presented with a choice of display managers
to install?
If so, which option will give me the most flexibility for multiple environments.

Please accept my apologies if I didn't pose this question so clearly at first.
I  added "display manager" as a tag. 
regards
tim

---

### Post by rillip on 2007-04-03
Each installer comes with its own DM, Ubuntu = Gnome, Kubuntu = KDE, Xubuntu = XFCE (edit; had a d instead of a C)

They all basically have the same installer, with none making it particularly easier to install the guis than others.  From what you're telling me, Kubuntu sounds like it might hit your sweet spot.  The Adept package manager is a little more "advanced" than Synaptifc (which comes with Ubuntu).  I know absolutely nothing about Xubuntu.

It should be trivially easy to install other guis, however.  For example, from level 3 you'll type sudo apt-get install ubuntu-desktop for the Ubuntu desktop package (which includes Gnome, the GDM login manager, etc).  You pretty much change ubuntu to xubuntu or kubuntu in the above example to get the others.

As for installing fvwm, I'll have to refer you to it's instructions.  I imagine it's just sudo apt-get install fvwm but I don't know anything about it to try it.  You can probably also add an FVWM entry in grub, though I'll have to refer you to grub's help for how to do so. As aysiu said, you can also do it from the login prompt.

Hope this helps!

---

### Post by tim042849 on 2007-04-03
Thanks a lot!
Yes, I think that kubuntu will hit my sweet spot..

I'll look to fvwm on the side to see if it will help my productivity
(I'm a programmer).

I appreciate the input. Great help!
tim

---

