---
title: "Can't install amarok after previously removing"
date: 2006-10-03
forum: Desktop Environments
---

### Post by yeehawjared on 2006-10-03
So I just re-installed a fresh copy of ubuntu

sudo apt-get install amarok.  

It downloaded 1.3.  I wanted the latest version so  I typed:

sudo apt-get remove amarok.

then I added some repositories so I can get the latest amarok.  After that I typed:

sudo apt-get update
sudo apt-get install amarok

The following packages have unmet dependencies:
  amarok: Depends: libtunepimp3 (>= 0.4.2) but it is not installable
          Depends: libvisual-0.4-0 (>= 0.4.0) but it is not installable
E: Broken packages

I can't install them individually - I get errors.  I try to download and install the deb files, but I get errors.  How can I get amarok working?

btw, I use gnome.  I had 1.4 working flawlessly just a few hours ago on gnome... please help.  thanks guys.  ;)

---

### Post by jISh on 2006-10-03
It's better to use the current version of Amarok in the Ubuntu repos, and wait for Edgy so you can have the newer libraries which will probably run the latest build of Amarok.

---

### Post by yeehawjared on 2006-10-03
got it working... here's how:

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)    - got a new sources.list

added this to sources.list
#Amarok 1.4.3
deb [http://kubuntu.org/packages/amarok-143](http://kubuntu.org/packages/amarok-143) dapper main


sudo apt-get update
sudo apt-get install amarok

done and done.

---

### Post by mitch.c on 2006-10-03
> **yeehawjared said:**
> added this to sources.list
#Amarok 1.4.3
deb [http://kubuntu.org/packages/amarok-143](http://kubuntu.org/packages/amarok-143) dapper main

Amarok 1.4.3 is also in the ubuntu backports repository.

---

