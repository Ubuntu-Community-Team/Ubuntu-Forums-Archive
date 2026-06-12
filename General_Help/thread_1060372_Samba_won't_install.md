---
title: "Samba won't install"
date: 2009-02-04
forum: General Help
---

### Post by kooldino on 2009-02-04
Setting up an ubuntu 8.04.2 LTS box.

Went to install Samba, and here's what I get...

```
sudo apt-get install samba
The following packages have unmet dependencies:
samba: Depends: samba-common (= 3.0.28a-1ubuntu4.4) but 3.0.28a1ubuntu4.7 is to be installed

E: Broken packages


```

---

### Post by kooldino on 2009-02-04
Since I currently have samba-common 4.7 installed, can I simply force samba to install somehow?

If I try to revert to 4.4, it wants to remove ubuntu-desktop. :(

---

### Post by sam1948 on 2009-02-04
try this
```
sudo aptitude install samba
```

---

### Post by kooldino on 2009-02-06
Well, that seems to have installed it, although it reverted it back to samba-common 4.4.

Can you explain how that worked?

And how aptitude differs from apt-get?

---

### Post by whitegourd on 2009-02-06
I was wondering the same thing and this is what I was able to search.

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by sam1948 on 2009-02-06
aptitude automatically resolves packages dependencies. with apt-get u must do it manually with flag "build-dep" 
which i don't exactly know how to use. 
take a look again at the error message u submitted it exactly says u missing some packages required to install the pkg u want.

---

### Post by kooldino on 2009-02-06
> **sam1948 said:**
> aptitude automatically resolves packages dependencies. with apt-get u must do it manually with flag "build-dep" 
which i don't exactly know how to use. 
take a look again at the error message u submitted it exactly says u missing some packages required to install the pkg u want.

apt-get will automatically get the same packages.  It looks like what aptitude did was automatically revert to the old version of samba-common as required by the new version of samba.

---

### Post by chrisstewart on 2009-02-06
after running apt-get samba I believe a 

apt-get install -f should fix any broken dependencies.

possible run apt-get update and apt-get upgrade to make sure your system is upto date before running samba

Hope that helps Chris

---

