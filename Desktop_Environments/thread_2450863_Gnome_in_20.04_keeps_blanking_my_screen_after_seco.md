---
title: "Gnome in 20.04 keeps blanking my screen after seconds"
date: 2020-09-22
forum: Desktop Environments
---

### Post by ray field on 2020-09-22
Installed 20.04 last week, and been experiencing strangeness with the display -- most notably now, that my screenlock times out seconds after I stop typing/mousing, whatever I set the timeout to. Using the box at home, I don't password protect the lock.

It's a new GeForce1030 card with the Nvidia drivers, but I really don't think it's a driver issue, had similar issues with the Nouveau drivers. 

Other information:

1) I keep root on a separate partition from /home, but for reasons not worth going into, instead of installing 20.04 over 16.04, I reformatted and repartitioned and copied a /home backup -- only reason I bring it up is because I wonder if something left there is messing with my configuration?

2) syslog shows countless instances on the order of every 3-4 seconds of "ep 22 08:05:14 Xxxxx gnome-shell[14113]: Object .Gjs_ui_pointerA11yTimeout_PieTimer (0x5566dc58fc20), has been already deallocated — impossible to access it. This might be caused by the object having been destroyed from C code using something such as destroy(), dispose(), or remove() vfuncs."

---

### Post by CelticWarrior on 2020-09-22
#1 is plausible cause indeed, given the huge differences between those releases regarding the desktop environment.

---

### Post by ray field on 2020-09-22
> **CelticWarrior said:**
> #1 is plausible cause indeed, given the huge differences between those releases regarding the desktop environment.

especially since I was (happily) using Unity. what I'm hoping is that there's a simple dconf (gconf?) setting I can disable, because after two days customizing to where I like things, I sure don't want to have to reinstall.

---

### Post by ray field on 2020-09-23
I wound up just resetting with [FONT=Courier New]dconf reset -f /org/gnome/[/FONT]

---

### Post by ActionParsnip on 2020-09-23
If you make a new user and log in as that is it OK? If so then old configs will be the culprit as the new user will get vanilla settings

---

