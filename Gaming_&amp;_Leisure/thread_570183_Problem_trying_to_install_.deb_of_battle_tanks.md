---
title: "Problem trying to install .deb of battle tanks"
date: 2007-10-07
forum: Gaming &amp; Leisure
---

### Post by tabithaboof on 2007-10-07
I am trying to install the deb of battle tank from here

[http://www.getdeb.net/app.php?name=Battle+Tanks](http://www.getdeb.net/app.php?name=Battle+Tanks)

and I keep getting the following error message

----------
dpkg: dependency problems prevent configuration of btanks:
 btanks depends on libopena10a; however:
  package libopena10a is not configured yet.
----------

I have checked in my package menu and libopena10a is installed but i dont understand how to configue it. Any chance of some guidance?

---

### Post by DoktorSeven on 2007-10-08
Try doing from a terminal:

**sudo apt-get -f install**

---

### Post by Perfect Storm on 2007-10-08
If you want to compile it, I provided a guide: [http://gaming.gwos.org/doku.php/guides:battletanks](http://gaming.gwos.org/doku.php/guides:battletanks)

---

### Post by tabithaboof on 2007-10-08
Thanks very much this did the trick!

[/QUOTE]**sudo apt-get -f install**[/QUOTE]

Without meaning to sound too dumb, what did this command acctually do?

---

