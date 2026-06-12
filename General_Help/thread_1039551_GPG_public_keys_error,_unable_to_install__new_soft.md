---
title: "GPG public keys error, unable to install  new software"
date: 2009-01-14
forum: General Help
---

### Post by cityismine on 2009-01-14
I just installed ubuntu, and started adding some repositories in software sources. But I can't get the entries to load, whenever I hit the reload button, I get following error.

I'm getting this error for every repository entry I put into synaptic. I'd really like to get this fixed, so I can try some new software.


W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by avtolle on 2009-01-14
That medibuntu key problem seems to be persistent; it, however, in and of itself, does not prevent me from adding repositories (added one yesterday without moment) or downloading updates, new software packages. Would you please post your /etc/apt/sources.list? Thank you.

---

### Post by cityismine on 2009-01-14
I'm adding the repositories through the software sources gui. The same problem occurs when I add the repository for the opera browser.

[SIZE="1"]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) intrepid partner
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free[/SIZE]

---

### Post by spiderbatdad on 2009-01-14
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
or
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

---

### Post by cityismine on 2009-01-14
That didn't work either. Got this error in terminal

[SIZE="1"]E: Couldn't find package medibuntu-keyring[/SIZE]

---

### Post by adult swim on 2009-01-14
sometimes whenever you enable third party repositories, like you have with medibuntu and opera, you need to get the gpg key.  spiderbatdads suggestion should work for medibuntu, to get the key for opera, you need to run this from  a terminal
```
sudo wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```

---

### Post by spiderbatdad on 2009-01-14
sorry editted post

---

### Post by bodhi.zazen on 2009-01-14
> **cityismine said:**
> I just installed ubuntu, and started adding some repositories in software sources. But I can't get the entries to load, whenever I hit the reload button, I get following error.

I'm getting this error for every repository entry I put into synaptic. I'd really like to get this fixed, so I can try some new software.


W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Just for the record, that message does not prevent you from installing applications.

Import the key, as outlined, to resolve that message if you wish.

---

### Post by cityismine on 2009-01-14
[SIZE="1"]wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
sudo wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -[/SIZE]

In software sources, I don't see any new entries in the third party tab, although there are new entries in the Aucthentication tab.

I still don't see opera when I search for it in synaptic. Is there a way to fetch the keys automatically whenever a new repository entry is made in software sources?

---

### Post by adult swim on 2009-01-14
the keys go to the authentication tab
what happens when you run from a terminal
```
sudo apt-get update
sudo apt-get install opera
```

---

### Post by cityismine on 2009-01-14
> **adult swim said:**
> the keys go to the authentication tab
what happens when you run from a terminal
```
sudo apt-get update
sudo apt-get install opera
```

Okay that worked, but why isn't opera showing up in synaptic when I search for "opera"?

---

### Post by zvacet on 2009-01-15
You can add gpg key with this commands

```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys  2EBC26B60C5A2783
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -
```

Why don't you download Opera from [here]("http://www.opera.com/download/index.dml?platform=linux")?

---

