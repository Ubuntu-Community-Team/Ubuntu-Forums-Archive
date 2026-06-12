---
title: "XNA Game Studio"
date: 2008-12-02
forum: General Help
---

### Post by Ranger1230 on 2008-12-02
I was wondering if there is a way to run XNA Game studio in Ubuntu? I can use windows for it but most of the windows applications hog all the ram and make it painfully slow to work with. ubuntu is much cleaner and I would prefer to use it. I'm not sure if Wine would work since its a Microsoft tool. any advice?

---

### Post by lovinglinux on 2008-12-02
You can run several Microsoft applications using Wine, but as far as I know, XNA needs  dependencies from the Visual Studio family. So you will have to install those too, if they are compatible with wine.

Check [WineHq]("http://www.winehq.org/").

---

### Post by niroshido on 2009-07-18
[http://appdb.winehq.org/votestats.php](http://appdb.winehq.org/votestats.php)

the above link leads to the vote stats for the programming language compatabilities of wine. But in order to get XNA the most recent version up and running you need the following:

**Microsoft .NET Framework 3.5**

&

**Visual Studio 2008**

whilst both do show up high on the list XNA does not exist on there list at all, thus i'd be sceptical on full compatibility through wine

UPDATE:[ http://appdb.winehq.org/objectManager.php?sClass=application&iId=8153]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=8153")

i found XNA but with 1 person after voting it work through the XNA 3.0 package, i still feel sceptical, but maybe you should give it a shot

---

