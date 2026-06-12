---
title: "Expocity"
date: 2005-01-12
forum: Desktop Environments
---

### Post by lizardking on 2005-01-12
I have found this deb package in the net to transform metacity simple task swithcer to a task switcher similar to Exposè di apple.
This si the software [EXPOCITY](http://www.pycage.de/software_expocity.html) .

I have found this debian package if some one would like to try it.
[Debian package for Expocity](http://acm2.ustc.edu.cn/~roger/debian/) 
**I invite the developer of Horthy to intall into it by deafult.** 
I have installed the package by **dpkg**  beacuse apt-get doen't work.
This is the result:
[click here to see](http://iack.altervista.org/expocity.jpg) 

**I have only a problem and if someone knows how to solve I'm glade with him. When I Go  to update package with synaptic I take an error to upgrade the system.The error is beacuse synaptic try to upgrade the library libmetacity0-exp that is the library of Expocity.So if I do this upgrade expocity go away :(. Some one have any solution?** 

thanks

---

### Post by dude2425 on 2005-01-12
I've tryed Expocity in Fedora, and all it does is change the alt-tab keybind from a simple little window to show off everything running ATM. I personaly hated it, I use alt-tab for everything I do, mostly just tapping it to switch from one to the other. I would hate it if Exposity was default because then I would lose the ability to switch between multiple windows as fast as I normaly do. Expocity isn't default for the simple fact that it would hinder productivity of all the other user's of Ubuntu who prefer the regular alt-tab to Apple's idea of an alt-tab.

It's a great feature though for all the people who would like to emulate the look of a mac, but for the regular joe, it just isn't very usefull.

As to your problem, I'm sorry but I can't help you with it.

---

### Post by ulrich on 2005-01-13
> 
I have only a problem and if someone knows how to solve I'm glade with him. When I Go to update package with synaptic I take an error to upgrade the system.The error is beacuse synaptic try to upgrade the library libmetacity0-exp that is the library of Expocity.So if I do this upgrade expocity go away . Some one have any solution?

thats normal.
while running expocity you also need a patched metacity.
since that version isnt in buntu it will overwrite your old (patched expocity) version.

to prevent this, open synaptic, search for your packages, select a package, and then in the menu 'package' theres an option for pinning this package. 
i run a german ubuntu, so i dont know how this is in the english version...
(means hold this version even if newer versions come out)

hope this helps

ulrich

---

