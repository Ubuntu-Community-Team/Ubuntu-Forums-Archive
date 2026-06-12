---
title: "burning multisesion dvd-r(w) in k3b - questions"
date: 2009-04-23
forum: General Help
---

### Post by logos34 on 2009-04-23
Recently I was forced to use dvd-r(w)media, having previously used only +r(w).  I prefer the latter--it supports true multisession, and for +rw you need only overwrite the disk, even to start over again (vs. the long 'blank=full' required to begin a -rw disc again in incremental sequential mode).  No need for formatting at all, except of course initially in the case of +rw.  

Using k3b is confusing: I tried dvd-rw sequential first, with all 'auto' settings, and expected it to begin writing in incremental sequential mode by default, which it did, leaving the disk 'appendable', to add more stuff later. Next, I specified 'DAO' writing mode, and as expected it asked to format, then wrote and finalized/closed the disc. (It also gave the choice of 'restricted overwrite', which unlike DAO sequential, doesn't even require a quick format  to begin the disc anew.  You simply overwrite).  

But when I inserted a dvd-r, which it correctly identified as 'dvd-r sequential', I thought that it would by default write in incremental mode, like -rw, leaving the disc open.  Again, I used 'auto' settings, the only other choice of 'writing mode' being DAO.  Instead, k3b closed the disc.  There was still ~350MB left.  Unless k3b is programmed to close a disc with that much room left, I guess it writes by default in DAO mode, because I didn't see any indication that it was writing a "multisession DVD", as it did when I did a "simulated" burn next, the only difference being that I explicitly specified "Start multisession" in the Misc tab>Multisession Mode menu .

Why, since dvd-r(w)s come factory-fresh in incremental (appendable) sequential mode, does k3b write dvd-rws by default in that mode, but writes dvd-r's by default in DAO (closed) mode?  

confusing, IMO 

I guess I should have either checked the "simulate" option the first time around, or at least tried to specify "start multisession" (but I was afraid of it throwing a "multisession streaming" support error message and defaulting to DAO mode before i could stop it).

---

