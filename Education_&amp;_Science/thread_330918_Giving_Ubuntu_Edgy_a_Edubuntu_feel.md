---
title: "Giving Ubuntu Edgy a Edubuntu feel"
date: 2007-01-03
forum: Education &amp; Science
---

### Post by kcallis on 2007-01-03
I installed Ubuntu 6.10 on my daughter's PC. At that point, I started adding all sorts of apps, etc. including the stuff placed by Automatix. In retrospect, I should have installed Edubuntu instead of the standard Ubuntu, but a little too late for that... So, is there anyway to take a standard Ubuntu installation, and give it the look and feel of having a Edubuntu distribution? It would be nice if there were a simple script that would do a massive apt-get and do the job, but I could only wish! :)

---

### Post by Steveire on 2007-01-03
```

sudo aptitude install edubuntu-desktop

```
```

stephen@deepthought:~/.kde$ aptitude search edubuntu
p   edubuntu-artwork                - edubuntu themes and artwork
p   edubuntu-artwork-usplash        - edubuntu artwork for usplash
p   edubuntu-desktop                - edubuntu desktop system
p   edubuntu-docs                   - documentation for edubuntu systems
p   edubuntu-menus                  - group-driven menus for Edubuntu
p   edubuntu-server                 - edubuntu servers

```
I guess you should get the edubuntu-artwork package as well in that case.

---

### Post by highvoltage on 2007-01-04
You can also install edubuntu-desktop from Synaptic if you want to do it via a GUI :)

---

