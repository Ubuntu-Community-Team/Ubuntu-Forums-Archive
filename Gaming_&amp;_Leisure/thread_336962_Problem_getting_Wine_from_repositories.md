---
title: "Problem getting Wine from repositories"
date: 2007-01-12
forum: Gaming &amp; Leisure
---

### Post by GeoPirate on 2007-01-12
I am trying to install Wine.  I have an AMD 64x2 3800, radeon 9200, 1gb ram desktop.  I am encountering a problem getting the repository to work.  I go in synaptic, and add the respository for wine from the how to:
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

It prompts me to reload and it starts looking/downloading it, then it gives me the error :
An error occured

The following details are provided:

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

I have uncommented the reopsitories, and I can't seem to find anyone else who has had this problem.  Any help would be appreciated.

---

### Post by Ferrat on 2007-01-12
you get better results compling it yourself

---

### Post by hikaricore on 2007-01-12
> **Ferrat said:**
> you get better results compling it yourself

what ???   what are you talking about he has an apt-get key error, good christ.  This is not fatal and unless a specific patched version of wine is needed the budget repos are the best place to get the bleeding edge wine versions.  Usually 1-2 days after they're released.  :)

---

### Post by hikaricore on 2007-01-12
> **GeoPirate said:**
> I am trying to install Wine.  I have an AMD 64x2 3800, radeon 9200, 1gb ram desktop.  I am encountering a problem getting the repository to work.  I go in synaptic, and add the respository for wine from the how to:
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

It prompts me to reload and it starts looking/downloading it, then it gives me the error :
An error occured

The following details are provided:

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

I have uncommented the reopsitories, and I can't seem to find anyone else who has had this problem.  Any help would be appreciated.

It is safe for you to ignore that error.  There was a key solution posted around here somewhere, but I can't find it at the moment.  Just do update again once you add the line for wine to your sources again.  Then do:

```
sudo apt-get install wine
```

It's that simple.

---

### Post by hikaricore on 2007-01-12
Found it:

```
gpg --keyserver subkeys.pgp.net --recv 387EE263 && gpg --export --armor 387EE263 | sudo apt-key add -
```

If for any reason this gives you an error, run it after typing:  **sudo -s**  and entering your password.  After make sure you type exit to close your sudo root login. :)

---

