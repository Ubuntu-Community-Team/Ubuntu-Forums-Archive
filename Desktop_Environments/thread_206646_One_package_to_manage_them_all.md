---
title: "One package to manage them all"
date: 2006-06-30
forum: Desktop Environments
---

### Post by StylusPilot on 2006-06-30
[FONT=Verdana][COLOR=Navy]Ok so this is probably been asked before, but I have look and searched and get plenty of possibilities but not exactly what I want.

Being a new user to Ubuntu I tend to install and uninstall a few packages quite regulary,

Is there a package available which can see what other packages I actually need and reccommend what ones I can get rid of? There is alot of them in there which I'm sure I probably don't need and never use, Is there any easy way to manage them all?

Oh and when you remove a package via the add/remove (not the advanced synaptic package manager) does it automatically remove any dependencies that they may have installed if they are no longer needed?

Thanks in advance.
[/COLOR][/FONT]

---

### Post by nanotube on 2006-06-30
if you want automatic removal of unused dependencies, you should look at "aptitude" instead of synaptic/apt-get. aptitude keeps track of dependencies, so when you remove something and it has unused deps, it will remove them too. synaptic or apt-get don't do that.

you could also use aptitude to analyze your system and givey ou a list of all "unused dependencies", but you might want to be careful and figure out what they are before you start removing them all :)

---

