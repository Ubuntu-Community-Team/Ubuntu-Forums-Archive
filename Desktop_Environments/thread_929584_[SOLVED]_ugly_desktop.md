---
title: "[SOLVED] ugly desktop"
date: 2008-09-25
forum: Desktop Environments
---

### Post by Bv202 on 2008-09-25
First of all Im sorry for my spelling. My keyboard settings wont change anymore for some reason

everything is ugly here
changing styles doesnt help

Im not able to post a nice post here as its really hard to type this message
here is a picture

[[IMG]http://img263.imageshack.us/img263/5738/schermafdruk1vh1.png[/IMG]](http://imageshack.us)

everything is ugly win 98 theme and the blue color cant be changed too
i tried every style already but it didnt change anything

compiz fusion seems to work

what can i do

---

### Post by Bv202 on 2008-09-25
Okay, my keyboard settings are to normal now.

This problem happened after updating Ubuntu a few weeks ago. But it could also be something that doesn't work properly..

---

### Post by Hairy_Palms on 2008-09-25
open up a terminal from the applications menu and type gnome-settings-daemon
see what it spits out as a response and post it here :)

---

### Post by Bv202 on 2008-09-25
I'm getting an error:

```
** (gnome-settings-daemon:6367): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:6367): WARNING **: Could not acquire name

```

EDIT:
I just found out that I can't change my resolution. nothing happens if I try to change it.

---

### Post by Hairy_Palms on 2008-09-25
hmm my best suggestion is go to System->Admin->Users and Groups and create a new user, then logout and login as the new user to see if the problem is the settings daemon or some config in your own user.

---

### Post by Bv202 on 2008-09-25
I've tried that already... it didn't solve it.

---

### Post by masterwillems on 2008-09-25
Did you install the graphic card drivers (or is your graphic card propperly supported?) i dont know if ubuntu changes the look if the graphic card drivers arnt installed propperly but i think its worth the try.
btw, greetings from the netherlands ;)

---

### Post by Bv202 on 2008-09-25
I live in Belgium :lolflag:

I tried already to uninstall them, but that doesn't work. I have the Compiz Fusion effects and they work fine, so the drivers should be okay.

---

### Post by fourthofjuly on 2008-09-25
Bv202,

if you wish to have a new theme, visit[http://gnome-look.org]("http://gnome-look.org") to download new themes...

---

### Post by masterwillems on 2008-09-25
> **Bv202 said:**
> I live in Belgium :lolflag:

I tried already to uninstall them, but that doesn't work. I have the Compiz Fusion effects and they work fine, so the drivers should be okay.

how did you install your effects? (now i am at work (winXP) so cant guide you trough, but its in the same window as the background tab (only then the one far left if im correct.)
BTW what videocard is in your system?

---

### Post by Bv202 on 2008-09-25
Four, NONE of the themes works..

Master, via the compiz settings or something... I did that before on my old computer and it worked fine.

No, the problem occured AFTER installing updates/downloading something..

---

### Post by fourthofjuly on 2008-09-25
NONE of the themes works?

what themes have you tried to install and what are the file names?

exactly, how are you trying to install from the theme files?

---

### Post by Bv202 on 2008-09-25
It just stays ugly if I change them. It also stays blue, nothing else..

---

### Post by masterwillems on 2008-09-25
No what i ment was

System -> Preferences -> Appearance preferences 
and then the tab Visual Effects

---

### Post by Bv202 on 2008-09-25
Yes, I tried all of these...

---

### Post by Hairy_Palms on 2008-09-25
i think people are misunderstanding, his problem isnt that he cant install a theme, its that the settings daemon is not working properly, hence any theme changes he makes do not work, and gnome defaults back to using no theme engine.

Try uninstalling the package xserver-xgl, and see if this fixes the problem

---

### Post by Bv202 on 2008-09-25
xserver-xgl isn't installed..:(

---

### Post by Hairy_Palms on 2008-09-25
hmm ok, try purging and reinstalling the settings daemon

> sudo dpkg -P --ignore-depends=gnome-settings-daemon gnome-settings-daemon
sudo apt-get install gnome-settings-daemon

---

### Post by Bv202 on 2008-09-25
Wow... it ruined like... everything.

If I login, my screen changes to a very bad resolution. I can't access the menu's at the top anymore or something, so I can't do anything anymore (and it's so ugly and everything is so big now lol)

On the other site, I had a feeling it was back normal... now the resolution should be changed back..

---

### Post by Bv202 on 2008-09-25
It's solved!
I've managed to login via the xterm safe mode and changed the resolution.

Everything is normal now!
Thank you VERY much for your help!!

---

### Post by Hairy_Palms on 2008-09-25
no problem, glad you sorted it out :)

---

### Post by crimesaucer on 2008-09-25
I'm glad you solved it, I was going to suggest making sure that you had the proper gtk theme engine if you were installing a new theme, because that is what the default theme looks like if you write incorrect code in the gtkrc.

---

### Post by DropZeroN on 2008-10-05
So I had the exact same problem.  I ran the scripts mentioned previously.  When I login, everything looks normal for about 3 seconds but then the background changes back to the solid orange.  Now the touch mouse pad doesnt work so i cannot use my mouse at all.  Any suggestions?

Oh btw, I am new to Ubuntu so you kinda have to talk to me like im a child. :/

---

