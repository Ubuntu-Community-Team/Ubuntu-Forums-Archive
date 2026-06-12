---
title: "How do you install Yoda Soccer?"
date: 2006-08-28
forum: Gaming &amp; Leisure
---

### Post by MacDonagh on 2006-08-28
I've got it extracted and all, but I can't install it. I've double clicked install but it won't work.

Help!

---

### Post by mlind on 2006-08-28
> **MacDonagh said:**
> I've got it extracted and all, but I can't install it. I've double clicked install but it won't work.

Help!

Did you download the linux version?

---

### Post by MacDonagh on 2006-08-28
Yep.

---

### Post by MacDonagh on 2006-08-28
Anyone help me out dead quick? Do I have to type something into the terminal?

---

### Post by MacDonagh on 2006-08-28
ach, im clutching at straws. Anyone know what I've messed up?

---

### Post by slugkilla on 2006-08-28
Hmmmm so it looks like you really want to play this thing and you are getting little help. I hate that. I'll try and help. Where can I find this "yoda soccer" so I can help you with it?

---

### Post by MacDonagh on 2006-08-28
[http://yodasoccer.sourceforge.net/](http://yodasoccer.sourceforge.net/)
Do you have to have windows on your system to install it?

---

### Post by mlind on 2006-08-29
> **MacDonagh said:**
> [http://yodasoccer.sourceforge.net/](http://yodasoccer.sourceforge.net/)
Do you have to have windows on your system to install it?

Download linux archive from the site, extract it and run yoda_soccer binary.
You need to have **libxxf86vm1**, **libglu1-mesa** and **libstdc++5** packages installed.

Then you probably need to symlink /usr/lib/libXxf86vm.so.1.0.0 to /usr/lib/libXxf86vm.so to get yoda soccer running

---

### Post by Perfect Storm on 2006-08-29
I don't think the symblink is needed though.


To MacDonagh:
When the requirements a met (check mlind post). You can double click the **yoda_soccer** file to launch the game. If it fail to start drag **yoda_soccer** file to the terminal and launch it from there so you can see if any error(s) happens.

---

### Post by mlind on 2006-08-29
> **Artificial Intelligence said:**
> I don't think the symblink is needed though.


To MacDonagh:
When the requirements a met (check mlind post). You can double click the **yoda_soccer** file to launch the game. If it fail to start drag **yoda_soccer** file to the terminal and launch it from there so you can see if any error(s) happens.

symlink is needed unless you want to install libxxf86vm1-dev package and bunch of useless development headers.

---

### Post by Perfect Storm on 2006-08-29
Hmmmm.....I have a whole bunch of devs packages installed (love to compile) , then it explains it then.

---

### Post by mlind on 2006-08-29
> **Artificial Intelligence said:**
> Hmmmm.....I have a whole bunch of devs packages installed (love to compile) , then it explains it then.

It's very useful to build and test out packages on a minimal chroot (+ build-essential). You'll catch issues like that.
One ways to accomplish these are pbuilder (tarred chroots) or using LVM snapshots.

I don't keep any -dev package installed on my actual system.

---

### Post by Perfect Storm on 2006-08-29
I'm to lazy to remove the -dev packages afterwards :mrgreen: ...due to the reason I compile everyday :KS

---

