---
title: "two pcs acting together"
date: 2009-06-10
forum: General Help
---

### Post by 1234 on 2009-06-10
Can i make two PCs running ubuntu act like one powerful pc. (would it be possible to share their resources processor, ram etc.)

---

### Post by jacksaff on 2009-06-10
It's called clustering and it's fairly easy to do with linux (there are a few distros that exist just to do that).

It isn't worth it for a desktop system though - it will probably be slower than the faster machine alone. Some tasks will be sent to the other machine which can be MUCH slower than just queuing them up on the local box due to the slower transfer speeds over network compared to inside a cpu. 

Clustering is used for large and highly parallel programs such as video rendering or scientific simulations like protein folding.

---

### Post by 1234 on 2009-06-10
thank you.
>>slower than a single pc?
did u mean they have to be more in number.
actually I wanted them to be powerful for 3d image rendering. then would it be ideal to install windows on the clustering distros you said (like via virtual box) and use them together?

the pcs i had are 2.4 ghz 512ram

---

### Post by Commander_Keen on 2009-06-10
> **1234 said:**
> thank you.
>>slower than a single pc?
did u mean they have to be more in number.
actually I wanted them to be powerful for 3d image rendering. then would it be ideal to install windows on the clustering distros you said (like via virtual box) and use them together?

the pcs i had are 2.4 ghz 512ram

  Just increase the ram to 3 to 4 gbs that should help.

---

### Post by mixmaster on 2009-06-10
> **1234 said:**
> thank you.
>>slower than a single pc?
did u mean they have to be more in number.
actually I wanted them to be powerful for 3d image rendering. then would it be ideal to install windows on the clustering distros you said (like via virtual box) and use them together?

the pcs i had are 2.4 ghz 512ram
You can cluster linux PC's (go to [http://www.beowulf.org](http://www.beowulf.org) for possibly the most famous example).  However, clustering like this will only give you a performance boost for programs explicitly written for clustering.  Certainly you will get no help for a rendering program running under windows in VirtualBox!

---

