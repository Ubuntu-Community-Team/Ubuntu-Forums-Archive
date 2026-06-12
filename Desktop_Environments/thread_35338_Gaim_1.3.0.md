---
title: "Gaim 1.3.0"
date: 2005-05-18
forum: Desktop Environments
---

### Post by awilisch on 2005-05-18
I'm curious about something. I was about to install Gaim 1.3.0 (since it's still not available as an upgrade via synaptic), but when I tried to remove the old gaim, it tells me that to do so, I would have to remove the entire ubuntu-desktop section. What's up with that?! I can't believe this single application is so important to the desktop that the entire desktop has to be removed if I want to take it off. is there a way of removing it? I just have this thing about having two versions of the same program installed if I don't have to.

Thanks
Aric

---

### Post by dave9191 on 2005-05-18
Its a part of the ubuntu desktop package and removing it wld remove the desktop package too. I know, its kinda sucky. I dont know if there is a way to remove it using the package manager. But you could try and delete the gaim files on the hdd and see what consquences that would have (id do a backup first). Or you could just get over the fact that you have 2 version installed. I feel your pain, cause Im like that too.

---

### Post by GeirG on 2005-05-18
# apt-cache show ubuntu-desktop
 
Description: The Ubuntu desktop system
 This package depends on all of the packages in the Ubuntu desktop system
 .
 It is safe to remove this package if some of the desktop system
 packages are not desired.  However, it is recommended that you keep
 it installed, because it is used to carry out certain upgrade
 transitions (such as adding new packages to the system).



I think it a bit less dramatic that it seems at first glance.  :-) 
I haven't removed my ubuntu-desktop packet, but I did remove an equivalent gnome packet under Debian once. Same thing, no problem.

But, why do you have to remove the old one?
Will it not be replaced by the new packet you are to install?

Regards,

---

### Post by derrick1985 on 2005-05-18
Do you have the backports repositories added?

---

### Post by angkor on 2005-05-19
Same thing here. I just downgraded gaim by removing and reinstalling the gaim package and it wanted to remove the ubuntu-desktop as well. I just apt-get removed it and reinstalled it later...no problem. 

I think the name of the package is a bit tricky, the first time I noticed apt wanted to remove the ubuntu-desktop I thought: No way!! But you can safely remove it and reinstall later.

---

### Post by dave9191 on 2005-05-19
Yeh, thats the impression i got as well when i saw the name, but i always wondered why it was only 15mb. Might try messing about with the package at some point. 

Dave

---

