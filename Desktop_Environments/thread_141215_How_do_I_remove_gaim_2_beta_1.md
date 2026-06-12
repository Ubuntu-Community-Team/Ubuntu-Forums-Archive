---
title: "How do I remove gaim 2 beta 1 ?"
date: 2006-03-07
forum: Desktop Environments
---

### Post by mithion on 2006-03-07
A few weeks ago, I installed gaim 2.0.  Recently, i wanted to switch back to gnome 1.5.  Naturally, to avoid duplications, I want to remove gaim 2 beta1.  So I open synaptic and search for gaim packages.  Strangely, synaptic didn't register any gaim 2 packages, only the default 1.5.  Where did they put all the stuff when i installed gaim 2?  And how do I make a clean removal so I can put back gaim 1.5?

---

### Post by Stealth on 2006-03-08
Did you install a GAIM deb or did you compile it yourself?

---

### Post by mithion on 2006-03-09
I compiled it myself.  But i have no idea where all the stuff goes.  And how do you compile something such that it is registered in synaptics?

---

### Post by Stealth on 2006-03-10
Install "checkinstall" (sudo apt-get install checkinstall). 
Then, when you compile something you do:

./configure
make
**checkinstall**

This'll create a deb package that'll it will install for you, and you can easily remove em from Synaptic. :) Now...as for your current compilation, I don't know how to remove that one :(

---

### Post by mithion on 2006-03-11
Oh ok, i'll remember the checkinstall thing.  Thanks for the tip.  At least it will help with future installs.  They should really redesign the file system to be tighter in linux.  This is not just a problem with ubuntu, but with linux in general.  But thanks again for the tip :)

---

### Post by OffHand on 2006-03-11
What's the reason the checkinstall isn't standard?
Seems like a very useful/needed/handy tool to keep your system clean.

---

