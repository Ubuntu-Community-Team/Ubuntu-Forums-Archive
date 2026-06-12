---
title: "firefox 1.0.3 extension"
date: 2005-04-27
forum: Desktop Environments
---

### Post by Jad on 2005-04-27
Can anyone install themes with Firefox 1.0.3?
i'm not getting any errors, but nothing being installed.
I have tried to run firefox from bash to see if any error comes up, but nothing

any idea?

---

### Post by bored2k on 2005-04-27
I'm using saferfox xpanded from mozilla.org.

You need to see if they are compatible, they usually say [.99 - 1.0 <-- that means it probably won't run on 1.0.3]

---

### Post by Chayyiel on 2005-04-27
Download the .jar file (theme) and open it with any compression utility.

Extract install.rdf > open in a text editor

Change <em:maxVersion>1.0</em:maxVersion> to

<em:maxVersion>2.0</em:maxVersion>

Repack the install.rdf file and install. Should work with your version.

---

### Post by Jad on 2005-04-27
[QUOTE=Chayyiel]Download the .jar file (theme) and open it with any compression utility.

Extract install.rdf > open in a text editor

Change <em:maxVersion>1.0</em:maxVersion> to

<em:maxVersion>2.0</em:maxVersion>

Repack the install.rdf file and install. Should work with your version.[/QUOTE]
 the problem is not with the compatability, else I would get alert about X or Y extension wont work with x.xx version.
the installation is not working at all. and no errors

---

### Post by mdm4301 on 2005-04-27
I am having this problem to.  I click on the install link and it just does nothing.  Not sure how to fix it though.  Any suggestions would be good.

---

