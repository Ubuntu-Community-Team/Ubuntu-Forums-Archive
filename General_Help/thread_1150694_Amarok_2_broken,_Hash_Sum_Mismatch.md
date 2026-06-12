---
title: "Amarok 2 broken, Hash Sum Mismatch"
date: 2009-05-06
forum: General Help
---

### Post by Ionna on 2009-05-06
A few issues: 

Amarok 2 seems to be broken. Have tried to uninstall and remove drivers but it still gives me the same error where it will not play songs. It will skip through all the songs and then not play. 

I've also been getting the hash sum error mismatch error, mainly like this: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-amd64/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-amd64/Packages.bz2)  Hash Sum mismatch

Any ideas on how to fix the two?

---

### Post by Ionna on 2009-05-08
Gentle bump?

---

### Post by Ionna on 2009-05-08
Hash Sum Mismatch error has been solved. Running: 

sudo apt-get update -o Acquire::http::No-Cache=True

Seems to fix it. 

Now to try Amarok 2, which I doubt will succeed. :S

---

### Post by ireneshusband on 2009-05-11
Amarok 2 is a piece of **** that should never have been released. Everything that made Amarok 1.4 worth using is either broken or unimplemented. Go [here]("https://launchpad.net/~bogdanb/+archive/ppa") to roll back to 1.4.

---

### Post by Ionna on 2009-05-17
Sorry for the late reply, but that was just what I was looking for! Thank you!

---

