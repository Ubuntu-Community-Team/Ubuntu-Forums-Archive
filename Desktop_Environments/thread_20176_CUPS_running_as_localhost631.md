---
title: "CUPS running as localhost:631"
date: 2005-03-15
forum: Desktop Environments
---

### Post by Victor Warner on 2005-03-15
Running Ubuntu 5.04.

In web browser entered: [http://localhost:631](http://localhost:631), and the menu/graphic elements for this service appear but at top of page there is the following message:

"Administrative tasks have been disabled for security reasons. Please use Menu System > Administration > Printing."

How do I deal with this other than going through "System > Administration > Printing"?

---

### Post by m4ng0 on 2005-03-15
sudo adduser cupsys shadow
sudo /etc/init.d/cupsys restart

and now you can use your root account for [http://localhost:631](http://localhost:631).

---

### Post by puelly on 2005-03-27
[QUOTE=m4ng0]sudo adduser cupsys shadow
sudo /etc/init.d/cupsys restart

and now you can use your root account for [http://localhost:631](http://localhost:631).[/QUOTE]
 thanks for the tip. worked. what exactly did I do?  did I add a user to a group called shadow? (trying ot learn and not type commands blindly)

---

### Post by alastair lewis on 2005-04-07
[QUOTE=m4ng0]sudo adduser cupsys shadow
sudo /etc/init.d/cupsys restart

and now you can use your root account for [http://localhost:631](http://localhost:631).[/QUOTE]


Thank you. I am now looking at the test page from an HP Deskjet 720C.
A win printer working under linux. How cool is that.

---

