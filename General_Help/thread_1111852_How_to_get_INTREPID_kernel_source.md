---
title: "How to get INTREPID kernel source?"
date: 2009-03-31
forum: General Help
---

### Post by pgmer6809 on 2009-03-31
HI:
I am running Gutsy and I want to get the source code for the version of the kernel used in intrepid.
I dont know what version that is.
I have added the intrepid source code repository to my Synaptic configuration, but a search for linux-image only returns the  Gutsy versions.

So how do I DL the intrepid kernel source code?

Thanks,
pgmer6809

---

### Post by klemes on 2009-03-31
You can try this:

apt-get update
apt-cache search kernel-source

and then look for the highest version ie for Hardy repositories this would be kernel-source-2.6.24,
then use apt-get install kernel-source-x.x.xx
to install kernel source.
Note this will be done under /usr/src.Then of course you 'll have to compile the kernel yourself to have a working kernel.
Why not install the binary image instead this should also retrieve all relative dependencies ,namely kernel modules and headers for your kernel.

---

### Post by Spaarkplug on 2009-03-31
have you visited kernel.org? They have it downloadable in txt format.Its about 21,000 lines.

---

### Post by pgmer6809 on 2009-03-31
> **Spaarkplug said:**
> have you visited kernel.org? They have it downloadable in txt format.Its about 21,000 lines.

OK I will try that.
I am not certain which version of the kernel I should be looking for, but any recent one will probably be OK?

Thanks, pgmer6809

---

### Post by pgmer6809 on 2009-03-31
> **klemes said:**
> You can try this:

apt-get update
apt-cache search kernel-source

and then look for the highest version ie for Hardy repositories this would be kernel-source-2.6.24,
then use apt-get install kernel-source-x.x.xx
to install kernel source.
Note this will be done under /usr/src.Then of course you 'll have to compile the kernel yourself to have a working kernel.
Why not install the binary image instead this should also retrieve all relative dependencies ,namely kernel modules and headers for your kernel.

The point is I dont want to install Intrepid. I tried it and it does not work. (Hardy does not work either. Same problem.) It has some sort of bug in the wired LAN code. I want to compare the source for intrepid with the source for Gutsy to see if I can figure out where the difference is.
That is why I need to be able to get the source without screwing up my current install.
pgmer6809

---

