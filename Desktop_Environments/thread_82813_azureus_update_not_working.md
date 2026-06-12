---
title: "azureus update not working"
date: 2005-10-27
forum: Desktop Environments
---

### Post by DarkManX4lf on 2005-10-27
ok every time i start up azureus it asks me to update to v2304 and when i say yes to update it downloads the update and updates then it tells me to restart...and then when it restarts it says ihave to update again to v2304....i check the about tab and its still v2300 after updating...does this happen to anyone else?

---

### Post by faulkner132 on 2005-10-27
I get it too.  From what I can tell, this is normal.  When 2.3.0.4 is placed in the repositories, you can upgrade.

If you want to upgrade without waiting, you can compile it from source.

---

### Post by stoeptegel on 2005-10-27
The build-in updater broke my friends azureus, i wouldn't use it. I think there was an option to disable this auto update feature somewhere.

---

### Post by JLChafardet on 2005-10-28
odd. lol

go to the azureuz website, get the GTK tar.bz2

uncompress it and "close azureus if runing".

then:

sudo mv /usr/share/java/Azureus2.jar /usr/share/java/Azureus2.jar-OLD

and from the directory where you extracted the new azureus

sudo mv Azureus2.jar /usr/share/java/Azureus2.jar

and start azureus.

that way worked for me in one try.

regards.

---

### Post by jeremy on 2005-10-28
If you start azureus by typing: sudo azureus , then it will update properly, then close it and start it again as the normal user.

---

### Post by stoeptegel on 2005-10-28
Giving an internet app sudo right, isn't that kind of dangerous? Just wanna know...

---

### Post by frenkel on 2005-10-28
[QUOTE=stoeptegel]Giving an internet app sudo right, isn't that kind of dangerous? Just wanna know...[/QUOTE]
Yes, but it's the only possibility to use the auto update function. As a normal user, you can't overwrite the Azureus files, as those are owned by the root user.

---

### Post by muted on 2006-01-05
[QUOTE=jeremy]If you start azureus by typing: sudo azureus , then it will update properly, then close it and start it again as the normal user.[/QUOTE]
Hi, I have the same problem, and this doesn't work for me, the updater keeps popping up every time i start azureus ...:confused:

---

