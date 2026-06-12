---
title: "Is there a command to list all programs installed?"
date: 2009-04-26
forum: General Help
---

### Post by Roasted on 2009-04-26
I'm preparing to do a fresh install of 9.04 on my system. I'm thinking this time instead of trying to guess which programs I had installed before that I would create a single text document on my flash drive, like a master install script.

So it would just go sudo apt-get install k3b amarok audacious audacity vlc... etc... and just install everything I have at once.

Trick is, I'm curious if there's a command to just list all apps I installed.

Does such a thing exist? If not I'll just sort through the menus, but I figured I'd ask for reference.

---

### Post by Sub101 on 2009-04-26
There is a better way to do it.

If you go to System==>Admin==>Synaptic Package Manager

Then select file and save markings. You can then read the markings on your new install which will install them itself.

---

### Post by Uzi304 on 2009-04-26
Well you can go into Synaptic, make sure that the category is all, and click on the the the little box above the check mark boxes for the packages. Sorry its hard to explain. Like where it says Package|Installed Version|Latest Version|Description, click on the one all the way on the left until the green check boxes are on top and you could look through those.

Edit: Or you could do what Sub101 said.

---

### Post by Roasted on 2009-04-26
Wow. That's pretty friggen intelligent... I'm impressed, even as a long time Ubuntu user that's one of those little things that kinda wow's ya.

Thanks a lot!

---

### Post by Sub101 on 2009-04-26
Before you continue i suggest you check it first.

---

### Post by blackgr on 2009-04-26
dpkg -l '*'

edited...

---

### Post by jdackle on 2009-04-26
I would say that's the best way (actually, it can get even better, you can save it as a .sh script to download the whole list of packages! ;) )
Ther is an IMPORTANT NOTE however: some packages may have hada altered dependencies and names and stuff... Also, you many end up installing packages you no longer need.
This should pose no major problems as most of that will be taken care of by the upgrade-process itself. But you might want to keep an eye on that. ;)

---

### Post by binbash on 2009-04-26
try this : 

dpkg -l > asd.txt

---

