---
title: "apps to cd"
date: 2006-09-11
forum: Desktop Environments
---

### Post by howardepgco on 2006-09-11
I just upgraded a computer for a friend of mine and we got rid of his Windows and installed Ubuntu (he loves it! I just have one problem,he doesn't have access to the internet.Is there a way I can download apps he may want and updates he may need and put them on a cd so he can install them on his machine?

---

### Post by ajgreeny on 2006-09-11
If you have a system running ubuntu already, you will have a lot of packages in your own  /var/cache/apt/archives folder already (everything you have installed using apt or synaptic will be there)  which you could simply burn to a CD or DVD and then copy them, as root, to the same place on your friends machine.  Be warned however there is a possibility of dependency problems if you can not get to the repos, and the packages needed are not available in the cache as well.

---

