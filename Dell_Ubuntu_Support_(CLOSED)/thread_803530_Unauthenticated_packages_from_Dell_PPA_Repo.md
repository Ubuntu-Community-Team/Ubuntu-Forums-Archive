---
title: "Unauthenticated packages from Dell PPA Repo?"
date: 2008-05-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sassinak on 2008-05-22
Should the packages from the Dell PPA repo be signed with a GPG key?  I pulled down the linux-ubuntu-modules-2.6.24 - 2.6.24-16.23Dell1 package in Synaptic and it shows as not authenticated.  

Am I missing a way to download the signing key for the repo, or is there just not one available?

---

### Post by ethanay on 2008-06-05
I don't have a key either...it's not a huge deal, imo, as long as you are aware of what you are installing/what is being installed.

My question about all this is:  What's the difference between
1)linux-ubuntu-modules-2.6.24-x-generic (in Ubuntu repos) and
2)ubuntu-modules-2.6.24-x-generic-di (in Dell PPA repos)

????

You obviously can't have both installed:
```
E: /var/cache/apt/archives/ubuntu-modules-2.6.24-18-generic-di_2.6.24-18.26Dell2_i386.udeb: trying to overwrite `/lib/modules/2.6.24-18-generic/ubuntu/net/igb/igb.ko', which is also in package linux-ubuntu-modules-2.6.24-18-generic
```

which means it's one or the other...I haven't changed to the Dell-supplied ones yet because the std Ubuntu ones seem to work OK, and I'm not sure what the difference is...

...anyone??

---

### Post by thorcik on 2008-06-06
funny thing is that in my case everything works fine on the standard, ubuntu package while on the dell one my wireless stops connecting to networks. so I keep using the "normal" one ;o)
anyway, this means that there surely is some difference between those two ;oP

---

### Post by ethanay on 2008-06-10
hmm, after hearing that my curiosity has dropped some... :)

what wireless do you use?  with iwlwifi and Intel Pro 3945abg I have to disable hardware scanning in order to get connections and it also solves a few other bugs.

---

