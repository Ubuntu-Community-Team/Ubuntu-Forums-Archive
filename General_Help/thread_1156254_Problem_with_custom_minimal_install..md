---
title: "Problem with custom minimal install."
date: 2009-05-11
forum: General Help
---

### Post by Cheesemill on 2009-05-11
Hi there guys,

I'm trying to install a minimal Ubuntu system on my old laptop and have run across a couple of errors. Here are the installation steps I've taken so far:

Installed a basic CLI system (9.04 using PXE from my server)
Installed the following packages: gnome-core gdm ubuntu-artwork

After reboot the system comes up OK and presents me with the Jaunty logon screen. After entering my username and password the following error occurs whilst X is starting:

```
Xsession: warning: xrdb command not found;
X resources not merged.
```

Clicking on OK the system appears to continue with no problems.

I also get the following error whilst gnome is starting:

```
The panel encountered a problem while loading
"OAFIID:GNOME_FastUserSwitchApplet".
Do you want to delete the applet from your configuration?

```

I click on 'Don't Remove' and gnome finishes loading properly (but obviously without the FastUserSwitchApplet in the top panel).

Anyone know the answer to either of these?

Thanks in advance for your help,

Cheesemill

---

### Post by mali2297 on 2009-05-11
You probably need the packages **x11-xserver-utils** for xrdb and **fast-user-switch-applet** for the user switch applet.

Note that you can search packages at [http://packages.ubuntu.com/](http://packages.ubuntu.com/).

---

### Post by kerry_s on 2009-05-11
when you do a custom always make sure xorg is installed first, it will save you a lot of problems down the line.

example:
sudo apt-get install xorg
sudo apt-get install gdm gnome-core ubuntu-artwork synaptic

gnome is a desktop, no matter how you swing it, there are a lot of things needed for it.

those are just standard warnings for the stuff on the panel that is usually shown by default. you can move all the stuff visible to 1 panel, delete the empty panel and recreate it, now move everything to that panel and delete the other empty panel and recreate it. that should get rid of any errors for things that should be there but aren't.

---

### Post by Cheesemill on 2009-05-11
Thanks Martin, that worked a treat.

I've now succeeded in creating a Ubuntu install that does absolutely nothing!!
(That was the plan though :))

kerry_s - Thanks for the tip, I'll keep it in mind for next time (or if this install starts acting wonky).

Cheesemill

---

### Post by ezsit on 2009-05-11
While still being quite light compared to a full-blown Ubuntu install, this command with get you a usable system without any unnecessary bloat:

sudo apt-get install xorg gnome-core gdm gnome-media gnome-system-tools gnome-volume-manager gnome-utils synaptic firefox

If you do not want to see the boot messages, add usplash and usplash-theme-ubuntu to the list and you will have a very lean system with all the basic functionality. CD burning, printing, and very many other niceties will not be included, you will need to add those later.

---

### Post by kerry_s on 2009-05-11
> **Cheesemill said:**
> Thanks Martin, that worked a treat.

I've now succeeded in creating a Ubuntu install that does absolutely nothing!!
(That was the plan though :))

kerry_s - Thanks for the tip, I'll keep it in mind for next time (or if this install starts acting wonky).

Cheesemill

you'll still want to check the session turn off the junk you don't want/need.
if your out for speed, you can turn on reduced resources.
etc...

i'm going to do a base build up later today, right now mines a full gnome that i trimmed down to try and lose some of the bloat.
i was planning on xfce4 build though, the gnome-policy crap just bugs the hell out of me.

---

### Post by Cheesemill on 2009-05-11
kerry_s - I've taken your advice and reinstalled using your method, Xorg first (it has x11-xserver-utils as a dependency). Doing this also solved the fast user agent switcher error (it's a dependency of gdm so was being installed anyway).

PS - What's that resource monitor you're running in the terminal?

Cheesemill

---

### Post by kerry_s on 2009-05-11
thats "htop" ( sudo apt-get install htop).
i just started my install, i'm doing debian testing, i just unchecked everything for the base install, so should be up and running in 30min's give or take. :P

---

### Post by kerry_s on 2009-05-11
yeah, it lives.

---

