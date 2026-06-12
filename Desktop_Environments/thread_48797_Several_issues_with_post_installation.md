---
title: "Several issues with post installation"
date: 2005-07-13
forum: Desktop Environments
---

### Post by illynova on 2005-07-13
Hey all,

I just installed my first Ubuntu linux on my laptop, and I'm really enjoying it. I've used many distros in the past couple o' years (redhat -> debian -> gentoo -> now ubuntu)

A few things that came up that I'm not sure of how to fix:

- The installer apparently automatically configured power saing (PCMIA I think?) into the kernel, and I have a battery monitor in the top right of my screen. It shows the correct value upon startup, but doesn't change after that. The battery might be half drained, but it'll still be showing 89% or 3:12. Any ideas on whats causing this?

- How do I change the layout of the applications drop down menu in gnome? Lets say I want to add a new category called "Development", and then add links to Mono-Develop, Kedit, etc. How would I go about doing this?

- I installed several KDE applications (KMail, and the rest of the PIM suite) The fonts are rather large on my laptop's 1024 x 768 res screen. I was able to configure gnome to use smaller fonts... but the kde apps do not reflect this change. I'm guessing the KDE apps are reading from a kde config file... where would this be located?

Thanks!! :)

---

### Post by ubuntp on 2005-07-13
[QUOTE=illynova]
- How do I change the layout of the applications drop down menu in gnome? Lets say I want to add a new category called "Development", and then add links to Mono-Develop, Kedit, etc. How would I go about doing this?[/QUOTE]
Install SMEG.

---

### Post by illynova on 2005-07-14
[QUOTE=ubuntp]Install SMEG.[/QUOTE]

Cool, that works. Does anybody know the solution to the other issues? Especially the font one?

---

### Post by varunus on 2005-07-14
Ah, I remember the KDE font issues, and to fix those, I think you need to set KDE's DPI or font size lower.  Try getting kcontrol, the KDE control center, so you can adjust your fonrts there...I remember just getting it to fix my problem.  I'm not sure where they are in a conf file...so if you can spare the disk space, kcontrol might be the best solution.

You could also try adjusting your X DPI (Gnome has its own DPI setting.).

---

