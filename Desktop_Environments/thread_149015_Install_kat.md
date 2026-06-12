---
title: "Install kat"
date: 2006-03-23
forum: Desktop Environments
---

### Post by adamkane on 2006-03-23
Since Beagle still has a way to go before it is usable, and stops eating files, I installed kat inside Gnome2, and just wanted to list the installation steps for everybody:

```

sudo apt-get install antiword dvi2tty man2html mhonarc xpdf-utils ppthtml  pstotext unrtf untex xlhtml
wget http://www.netmeister.org/apps/lyx2html-0.2.tar.gz
tar xzvf lyx2html-0.2.tar.gz
cd lyx2html-0.2
make
kat

```

Configure kat, and start adding catalogs.

More info:
[http://kat.mandriva.org/](http://kat.mandriva.org/)

---

