---
title: "ubuntu 8.01 update manager error"
date: 2009-05-08
forum: General Help
---

### Post by rdema19403 on 2009-05-08
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 084AF32EC2A6B0B1
have any idea how to correct this 
thanks in advance

---

### Post by Kareeser on 2009-05-08
Did you recently add a PPA to your Software sources?

That error comes up if you did not import the PGP key correctly, in order to verify the PPA's authenticity.

---

### Post by maheshasolkar on 2009-05-08
Following should help:

[https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%27s%20keys%20to%20your%20system](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%27s%20keys%20to%20your%20system)

---

### Post by zvacet on 2009-05-08
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
gpg --export --armor KEY | sudo apt-key add -[/B]

Replace **KEY **with number  084AF32EC2A6B0B1 .

---

### Post by rdema19403 on 2009-05-09
iam new to ubuntu 8.10 so i am not sure what you mean by ppa to your software sources

---

### Post by zvacet on 2009-05-09
> i am not sure what you mean by ppa to your software sources

you somehow add ppa repo t oyour source list but you didn´t authenticate it.That is why you are getting error.Type in terminal commands I posted to you and you should be fine.

---

