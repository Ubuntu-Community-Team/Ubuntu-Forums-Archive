---
title: "Fluxbox doesn't remember dimensions (apps)"
date: 2009-05-23
forum: Desktop Environments
---

### Post by Imperivm on 2009-05-23
I've just installed Ubuntu 8.10 again after having some problems with 9.04 . However, in my previous install of 8.10 this didn't occur. All three installs ran Fluxbox 1.0.0 .

Fluxbox remembers dimensions and position for Firefox and Eterm, but not for (Gnome) applications like Gedit, gnome-terminal and Totem.

I've tried deleting and editing the apps file several times, but it's always the same.
The applications of which the dimensions and position are ignored also lose the "checks" in the window menu next to "dimension", "position" and "save on close"; whereas in Firefox and Eterm these checks stays.

On gNewSense, it does a different thing... it remembers the dimensions, but not the position.
I've re-installed Fluxbox, but it acts exactly the same.

So it seems that Fluxbox's apps file is not working well with my Gnome apps.

I don't get it at all. Has anyone had similar problems, or have a solution?

---

### Post by RoboNuggie on 2009-05-24
Hmmm I haven't had this problem in all the time I have been using Fluxbox (3 years, now on version 1.1.1) but have you tried using **gnome-settings-daemon &** in your ~/.fluxbox/startup file?

I don't know if it will work, but it may make your gnome apps behave...

Or have you tried the various combinations found when right click on the window top bar, and selecting 'remember'?......

---

### Post by Imperivm on 2009-05-24
> Or have you tried the various combinations found when right click on the window top bar, and selecting 'remember'?......Yeah, I've tried several of the combinations... nothing worked (for the applications mentioned above).

The weird thing is: five minutes ago I opened Gedit, and it had the same dimensions it had when I closed it a few hours ago. Nothing's checked in the window menu's "Remember", though. I'll keep an eye on it.


I've tried running gnome-settings-daemon before, and it took over the theming/styling. I can't remember to what extent, I'll give it another go now and report back.


[edit]

When I let gnome-settings-daemon run at Fluxbox startup, it doesn't change anything. The dimension of Gedit are still magically remembered, but the position isn't. Neither is Totem's.

I downloaded the Fluxbox 1.1.1 from packages.ubuntu.com, uninstalled 1.0.0 and deleted the folders. With or without gnome-settings-daemon, the effect is the same. Gedit's dimensions are magically stored, but Totem's aren't.
Strangely enough, gnome-calculator position is remembered as it was on "close"; except when I start it from a terminal.

I'm confused. It's not the biggest issue (everything works) but part of using free software is having complete control :)

---

### Post by RoboNuggie on 2009-05-24
Yeah.... weird.....  having had a good look around, I have only one program that does this, Bluefish....  it would never start centered, always to the right.... not a problem.... I clicked on remember maximised,save on close.... and it starts up full now....

Do you have any apps in the slit at all.... I have a few, and maybe that is interfering with the apps position and size?  (purely guessing here!)

---

### Post by Imperivm on 2009-05-25
No, no applications in the slit at all.

Ah well, it's not in the end of the world. I'll keep googling it regularly, I'm sure something'll come up. Or it'll automagically sort itself out on the next install :)

---

