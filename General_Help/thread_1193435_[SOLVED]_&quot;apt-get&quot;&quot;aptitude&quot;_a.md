---
title: "[SOLVED] &quot;apt-get&quot;/&quot;aptitude&quot; and other noob questions"
date: 2009-06-21
forum: General Help
---

### Post by sirwerd1 on 2009-06-21
I have been using Ubuntu for a few days and believe I have made good progress in understanding what is going on.  I would just like to understand some of the stuff I am doing, instead of just memorizing random commands. So to start out, can someone explain the difference between "apt-get" and "aptitude" in terminal commands.

---

### Post by michy99 on 2009-06-21
They basically do the same thing, but supposedly aptitude does a better job of removing unneeded packages when you uninstall stuff. That is if you used aptitude to install the package in the first place.

---

### Post by VCoolio on 2009-06-21
Or if you use apt-get (or both at random) you can run "sudo apt-get autoremove" every once and a while to get rid of dependencies you don't need anymore. The new Computer Janitor in Jaunty (System > Admin) is supposed to do also this, but I don't like the Janitor much as it also complains about manually installed .debs which you could easily delete by accident this way.

---

### Post by cmost on 2009-06-21
As a long time user of Debian, I prefer apt-get.  In my opinion it is safer than Aptitude.  I'm sure others will argue the opposite.  I can say for certain that Apt-get never screwed up my system while Aptitude did.  :P

---

### Post by CatKiller on 2009-06-21
They are both front-ends to [APT]("http://en.wikipedia.org/wiki/Advanced_Packaging_Tool"), as is Synaptic or the Add/Remove Programs tool, which in turn is a front-end (more-or-less) to dpkg.

Aptitude has an interface in the same way that Synaptic does, but you can run it from the command line (the interface is curses-based). If you run aptitude with command-line arguments then it will behave in much the same way that apt-get does. It used to be the case that by default aptitude would remove automatically-installed dependencies when they were no longer required and apt-get wouldn't. Apt-get now does so too by default. Either of them can be configured with either behaviour anyway.

---

### Post by sirwerd1 on 2009-06-21
This was all very imformative.
Thanks

---

