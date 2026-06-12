---
title: "Upgrading to OpenOffice 3.0"
date: 2008-12-15
forum: General Help
---

### Post by Rylin on 2008-12-15
I have a fresh copy of Ubuntu 8.10 and I noticed openoffice is currently version 2.4. I ran this command:

sudo echo 'deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main' >> /etc/apt/sources.list.d/openoffice.sources.list && sudo apt-get update

This was posted (I forgot where) that is supposed to upgrade me to the latest open office 3.0. After it finished, I ran the program but the splash screen still shows 2.4?

Any suggestions?

---

### Post by frankleeee on 2008-12-15
Go here.
[https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)

---

### Post by b0b138 on 2008-12-15
all that command does (assuming its the right syntax, im not sure) is add that ppa to your sources.list then reloads. After that update manager should tell you there are updates available.

---

### Post by Rylin on 2008-12-15
> **frankleeee said:**
> Go here.
[https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)

Thanks, that did the trick. ;)

> all that command does (assuming its the right syntax, im not sure) is add that ppa to your sources.list then reloads. After that update manager should tell you there are updates available.

Actually that's probably what it was but the other sources frankleeee directed me to did the trick. :cool:

---

### Post by frankleeee on 2008-12-15
Fortunately the ppa site seems to be working in general. There have been handfuls of threads on getting OO3 to work either downloading from OO themselves or the ppa site. I originally installed Ubuntu Tweak and used the 3rd party link for OO in it, which was the ppa link. Glad it worked for you.,

---

