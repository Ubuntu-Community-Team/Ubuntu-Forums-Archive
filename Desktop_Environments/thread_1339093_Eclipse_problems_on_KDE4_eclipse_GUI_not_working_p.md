---
title: "Eclipse problems on KDE4: eclipse GUI not working properly"
date: 2009-11-27
forum: Desktop Environments
---

### Post by gmatt on 2009-11-27
Hi,

I am trying out kubunutu and so far its great. I tried installing the latest eclipse-cdt (for c/c++) off the website. When I attempt to run it in kde the buttons labeled "Next" or "Finish" in the new "C Project" wizard are unresponsive, I can click them multiple times and nothing happens.


I suspect this is because the jvm is somehow screwing up interpreting the GUI (which is probbaly implemented as gtk2) under KDE. This problem is not visible run eclipse from the version installed via apt-get. The problem is the eclipse in apt-get is outdated, also, it uses gcj and it is the java version of eclipse.


Has anyone had these troubles on KDE before?

---

### Post by gmatt on 2009-11-28
solved by [http://mou.me.uk/2009/10/31/fixing-eclipse-in-ubuntu-9-10-karmic-koala/](http://mou.me.uk/2009/10/31/fixing-eclipse-in-ubuntu-9-10-karmic-koala/)


man things just keep breaking.

---

### Post by cbonar on 2009-12-14
Thanks for the pointer, I had this strange behavior too with eclipse and another SWT application (mytourbook)...

---

### Post by hernan_ on 2009-12-30
I noticed that this solution doesn't resolve this problem completely.
Combo-box input fields are disabled so can't use them.

Actually I'm not so sure if this is just mine problem or still the Eclipse GUI vs KDE4

Does anyone have this same problem?

---

