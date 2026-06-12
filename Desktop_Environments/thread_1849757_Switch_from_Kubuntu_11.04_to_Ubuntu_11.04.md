---
title: "Switch from Kubuntu 11.04 to Ubuntu 11.04"
date: 2011-09-25
forum: Desktop Environments
---

### Post by mac67 on 2011-09-25
I would like to switch from Kubuntu to Ubuntu (without re-installation from scratch). I really mean "switch", not just see and use Gnome instead of KDE.

Why? When I upgraded from Kubuntu 10.10 to 11.04 I had several problems that I managed to fix somehow, with the help of this community. I thought (still think) the problem is some clash with hardware (laptop of 2008 ).

Today I upgraded Ubuntu 10.10 to Ubuntu 11.04 on an external HD. No problems at all, it works perfectly, no need to fix anything. So, I guess I have some problem with Kubuntu.

Any help?

---

### Post by sam_uk on 2011-09-25
I'm no expert but I would try

sudo apt-get install ubuntu-desktop

Then

sudo apt-get --purge remove kubuntu-desktop

---

### Post by Linux_junkie on 2011-09-25
simply remove all kde apps and the desktop itself after you've installed Gnome and all apps you want for that desktop.  kubuntu and ubuntu is essentially the same distro just with a different desktop.

---

### Post by mac67 on 2011-09-25
> **sam_uk said:**
> I'm no expert but I would try

sudo apt-get install ubuntu-desktop

Then

sudo apt-get --purge remove kubuntu-desktop

Hi,

this way I would just change desktop (which I already did), but it is still Kubuntu.

To make it clearer: when I boot, I see Kubuntu. I want to see Ubuntu when booting.

---

### Post by Docaltmed on 2011-09-25
I think you're looking for this:

[http://wiki.oseems.com/operatingsystem/ubuntu/switch-to-gdm](http://wiki.oseems.com/operatingsystem/ubuntu/switch-to-gdm)

---

### Post by mac67 on 2011-09-25
> **Linux_junkie said:**
> simply remove all kde apps and the desktop itself after you've installed Gnome and all apps you want for that desktop.  kubuntu and ubuntu is essentially the same distro just with a different desktop.

Are you sure that is enough? Where do I find the list of all kde apps and all gnome apps?

---

### Post by PaulW2U on 2011-09-25
> **sam_uk said:**
> sudo apt-get --purge remove kubuntu-desktop

This only removes the meta package kubuntu-desktop, not any of the packages that kubuntu-desktop would have installed.

---

### Post by ajgreeny on 2011-09-25
Install the ubuntu-desktop then run the command shown at [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Linux_junkie on 2011-09-25
> **mac67 said:**
> Are you sure that is enough? Where do I find the list of all kde apps and all gnome apps?

In package manager or software centre and display installed apps

---

### Post by mac67 on 2011-09-25
> **ajgreeny said:**
> Install the ubuntu-desktop then run the command shown at [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Hi, did you ever do what this link suggests? I see that a lot of files will be removed, are you sure Ubuntu will still work?

---

### Post by mac67 on 2011-09-25
First, I wish to thank all of you for trying to help me.

Let me explain what puzzles me. I have Kubuntu, but use Gnome. It works, but there are small graphic inconsistencies (e.g., a small part of the watch is not shown). The Ubuntu on the external HD looks clearly better without any error.

Therefore, I suspect that Kubuntu is not "simply" Ubuntu with another desktop, as many of you say.

Moreover: hasn't 11.04 moved from Gnome to Unity? So, I do not understand why I should install Gnome desktop.

---

### Post by intelligenceartificial on 2011-09-25
Follow [http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

---

### Post by sffvba[e0rt on 2011-09-25
> **mac67 said:**
> First, I wish to thank all of you for trying to help me.

Let me explain what puzzles me. I have Kubuntu, but use Gnome. It works, but there are small graphic inconsistencies (e.g., a small part of the watch is not shown). The Ubuntu on the external HD looks clearly better without any error.

Therefore, I suspect that Kubuntu is not "simply" Ubuntu with another desktop, as many of you say.

Moreover: hasn't 11.04 moved from Gnome to Unity? So, I do not understand why I should install Gnome desktop.



Ubuntu still uses Gnome, Unity is just a shell.

If Ubuntu+KDE was equal to Kubuntu then the developers of Kubuntu wouldn't spend so much time and effort creating an alternative to Ubuntu.

Kubuntu can be seen as Ubuntu **-** stuff **+** KDE **+** some stuff **+** tweaking **+** magic


404

---

### Post by mac67 on 2011-09-28
> **not found said:**
> Ubuntu still uses Gnome, Unity is just a shell.



All right.

> **not found said:**
> 

If Ubuntu+KDE was equal to Kubuntu then the developers of Kubuntu  wouldn't spend so much time and effort creating an alternative to  Ubuntu.



So, all posts that say "it's just another desktop" are wrong, as suspected.


> **not found said:**
> 

 Kubuntu can be seen as Ubuntu **-** stuff **+** KDE **+** some stuff **+** tweaking **+** magic
 
 
 
OK. What is suggested in the link provided by Artficialintelligence and Ajgreeny consists only in removing some Kubuntu stuff. Shouldn't I add some Gnome stuff too?

---

