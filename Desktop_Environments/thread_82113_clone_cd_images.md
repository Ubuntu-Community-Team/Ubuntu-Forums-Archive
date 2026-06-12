---
title: "clone cd images?"
date: 2005-10-25
forum: Desktop Environments
---

### Post by DarkManX4lf on 2005-10-25
is there a way i can burn clone cd images in linux?

---

### Post by stoeptegel on 2005-10-25
oeps my bad, all my info applies to nero nrg images! I am so sorry! (i'll leave it as it might come in handy for nrg images) 
For clonecd i have no idea.

[size=1]
You can convert it to iso with isodump. I think this is already installed by ubuntu. (and if not it's in synaptic) 

When the nrg image is created with "Track-at-once" instead of "Disc-at-one"(could be the opposite, i am not sure) you can rename it to iso and mount it with loopdevice. Isodump will also tell you if it's already in iso format or not, if so, $mv image.nrg image.iso get it done.[/size]

---

### Post by DarkManX4lf on 2005-10-25
[QUOTE=stoeptegel]oeps my bad, all my info applies to nero nrg images! I am so sorry! (i'll leave it as it might come in handy for nrg images) 
For clonecd i have no idea.

[size=1]
You can convert it to iso with isodump. I think this is already installed by ubuntu. (and if not it's in synaptic) 

When the nrg image is created with "Track-at-once" instead of "Disc-at-one"(could be the opposite, i am not sure) you can rename it to iso and mount it with loopdevice. Isodump will also tell you if it's already in iso format or not, if so, $mv image.nrg image.iso get it done.[/size][/QUOTE]

np its ok :), but hopefully someone can help me out :)

---

### Post by buildid on 2005-10-26
[http://linuxreviews.org/howtos/cdrecording/#toc15]("http://linuxreviews.org/howtos/cdrecording/#toc15")

---

### Post by DarkManX4lf on 2005-10-26
thanks.

---

