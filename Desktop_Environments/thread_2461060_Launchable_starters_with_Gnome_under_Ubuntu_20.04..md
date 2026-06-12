---
title: "Launchable starters with Gnome under Ubuntu 20.04.x"
date: 2021-04-23
forum: Desktop Environments
---

### Post by fnuxfl on 2021-04-23
Hi all,

With the last Ubuntu 20.04.x versions, the Gnome UI has introduced a new security feature that requires any new starter located on the Desktop to be set as "launchable".

In order to do so, just right click on the starter icon and select the option "Allow launching" 

[http://www.as2.com/qb64/pictures/png/capture-1.png](http://www.as2.com/qb64/pictures/png/capture-1.png)

and voila.

OK.

However, when doing so, I suspect that the Gnome UI executes a linux command similar to the one that the dialog panel "Permissions" of the dialog panel "propreties" of that starter executes when you select the option "Allow executing file as a program" (the relative command being chmod +x).

[http://www.as2.com/qb64/pictures/png/capture-2.png](http://www.as2.com/qb64/pictures/png/capture-2.png)[URL="http://www.as2.com/qb64/pictures/png/capture-1.png"]
[/URL]
So my question is quite simple: 

what is the linux command that I can use in a terminal (or in a script) to make a desktop starter "launchable" (i.e. without being obliged to do this manipulation using the UI?

Thank you in advance for your help since I can't find any documentation on this subject yet.

Best regards.

---

