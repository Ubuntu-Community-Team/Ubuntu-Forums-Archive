---
title: "Problem with Kontact and sync"
date: 2005-12-13
forum: Desktop Environments
---

### Post by MHD on 2005-12-13
when I click on sync on kontact I get the following error message
> Cannot load part for Synchronization.
Library files for "libmultisynkpart.la" not found in paths.

I am using breezy...

And has anyone had any luck syncing kontact with a pocket pc type device?

---

### Post by MHD on 2005-12-14
Anyone?

---

### Post by wjb on 2005-12-17
[QUOTE=MHD]when I click on sync on kontact I get the following error message


I am using breezy...

And has anyone had any luck syncing kontact with a pocket pc type device?[/QUOTE]
I have had the same problem and cannot find an answer on any board.  The sync button does not work in contact, and neither does the news button.  They both respond that a file is missing.

---

### Post by Sokraates on 2005-12-18
Unfortunately I don't know if the file is included in one of the kdepim-, mulisync- or kitchensync-packages You can find them in synaptic. Check, if any of them is missing.

I've got them all installed, so they at least don't conflict. On the other hand I sincerely don't know if I really need them all.

---

### Post by KermitJr on 2006-01-11
I had the same problem.

sudo apt-get install kdepim fixed it right up.

---

### Post by Divan Santana on 2006-01-12
[QUOTE=KermitJr]I had the same problem.

sudo apt-get install kdepim fixed it right up.[/QUOTE]
Does that mean you have yr pocket pc device syncing with kontact?

Cause I would love to know if its possible? Then please post about it! I would love to know! have been trying and will continue to try get it to work!

---

### Post by MHD on 2006-01-12
no I dont.... like many people here I am *that* close!!!!!!!!

Its all a matter of getting syncekonnector working...

Its not in the CVS, and I cant find a binary and I can not get it to compile....

---

