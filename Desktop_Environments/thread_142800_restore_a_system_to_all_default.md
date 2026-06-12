---
title: "restore a system to all default?"
date: 2006-03-11
forum: Desktop Environments
---

### Post by no1peanut on 2006-03-11
Posted a Q earlier that my appl launcher doesnt show ... 
But now to be sure that my somewhat wacked system be restored to the state it was in just after I first installed ubuntu - how can I do this ..?
I dont have have the cd and I dont have a cd burner !
But I do have internet connection - and I apt-get works.
Is there a apt-get base-system or something like that that will restore all configuration files etc to the state of a newly installed system ?

---

### Post by jasay on 2006-03-11
This won't restore everything, but a lot of configuration files are stored in the  .gnome .gnome2 and .gnome2_private folders in your home directory.  You can rename or delete these hidden folders and log out/in to restore most settings to default.

Edit:  Oh yeah, hit ctrl+h in nautilus to see hidden files/folders.

---

### Post by aysiu on 2006-03-11
Try just creating a new user and using that instead of your original user. 

Be sure to give this new user the same privileges as your old user (this is very important!).

---

