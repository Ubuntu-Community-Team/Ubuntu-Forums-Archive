---
title: "need help making a debian package"
date: 2009-02-13
forum: General Help
---

### Post by Blackiwid on 2009-02-13
I tryed to make a debian package from a python-bib that i need.

The package is mingus:

[http://code.google.com/p/mingus/](http://code.google.com/p/mingus/)

basicly it works, litian dont complain about something and i can install it . but i cant upload it to a ppa.

i think i have 2 problems:

first, because of that i think upload to ppa dont work:
  in the control file i define architecture: all  the generated debfile ends with _all.deb, but the changes file ends with _amd64.changes

the second problem is that i make changes outside the debian folder, basicly a wrote an Makefile like described there: [http://ghantoos.org/2008/10/19/creating-a-deb-package-from-a-python-setuppy/#Makefile](http://ghantoos.org/2008/10/19/creating-a-deb-package-from-a-python-setuppy/#Makefile)

but when i generate the file with it (make builddeb) its build as native-debian file, so the changes are not saved in a seperate diff file.

If nobody helps me i think i have to start again from the beginning to get a debfile that matches the specs for ppas, so i would be pleased that someone who is more into building debian packages could help me.

Besides the Makefile i also added the CHANGELOG file from the homepage.

---

### Post by heindsight on 2009-02-13
Have you read this: [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete) ?

---

### Post by Blackiwid on 2009-02-14
K i made the package again with cdbs that was much easyer and now i could upload it:

[https://launchpad.net/~stefan-canta-game/+archive/ppa](https://launchpad.net/~stefan-canta-game/+archive/ppa)

how can i close this thread?

---

