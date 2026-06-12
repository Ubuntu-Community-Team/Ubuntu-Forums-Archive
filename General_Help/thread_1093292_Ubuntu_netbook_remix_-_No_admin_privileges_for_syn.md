---
title: "Ubuntu netbook remix - No admin privileges for synaptic"
date: 2009-03-11
forum: General Help
---

### Post by Dontgetit on 2009-03-11
Hello...
I've just installed ubuntu netbook remix... everytime i try to run synaptic package manager, it tells me that i don't have administrative privileges and can't make changes... can anyone please help?

I'd like to change the privileges on it permanently... not just via sudo in terminal...

---

### Post by aeiah on 2009-03-11
synaptic always requires admin privs. i assume if you run sudo synaptic it works? then its some bug in the menu rather than with synaptic i would imagine.

does this occur with other software that requires a password? (most things from the administration section of the menu really)

is this through that full-page menu that the netbook remix uses? i have a netbook but havent used the remix im afraid.

---

### Post by aeiah on 2009-03-11
posted too soon. perhaps it's because the menu uses gksudo synaptic instead of gksu synaptic to launch the package manager

---

