---
title: "error installing wine"
date: 2009-03-30
forum: General Help
---

### Post by 2roombas on 2009-03-30
Recently I tried installing wine on my dell mini 9 (need to load Bookworm,  I'm addicted!) and the checkbox next to it "would not" check, hmmm?! So I then go over to Update Manager and notice it has been about 3 weeks since last checking.... so I check and see thid....
[B]
W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/intrepid/Release.gpg](http://wine.budgetdedicated.com/apt/dists/intrepid/Release.gpg)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/intrepid/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
[/B]
What does that mean?  And how do I fix it?

---

### Post by ibuclaw on 2009-03-30
It means that the host server is down for the time being.
Nothing you can do really...

See it for yourself: [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)

Regards
Iain

---

### Post by 2roombas on 2009-03-30
What about that last one?

**W: Some index files failed to download, they have been ignored, or old ones used instead.**

---

### Post by ibuclaw on 2009-03-30
Pretty self explanitory ...

apt-get failed to get the index files from the wine.budgetdedicated.com host server, so it will use the ones already present on your machine, if they exist.

These are stored here, respectively:
```
ls **/var/lib/apt/lists/**wine.budgetdedicated.com*
```

If they aren't there, then it will not be included when you list all available packages through synaptic or add/remove programs (hence *ignored*).

Regards
Iain

---

