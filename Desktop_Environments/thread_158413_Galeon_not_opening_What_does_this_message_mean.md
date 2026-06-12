---
title: "Galeon not opening: What does this message mean?"
date: 2006-04-11
forum: Desktop Environments
---

### Post by Sef on 2006-04-11
I installed Galeon and it didn't work, so I installed mozilla-bonobo and still didn't work.  I uninstalled Galeon and then reinstalled it.  In the terminal, I typed Galeon and got this message:

> sef@jokat1:~$ galeon

** (galeon:25449): WARNING **: I could not load the bookmarks file, will load the default bookmarks from /usr/share/galeon/default-bookmarks.xbel.
INTERNAL ERROR on Browser End: JavaPluginFactory5 init - no agent?

System error?:: No such file or directory


What does it mean and how can I get Galeon up and running?

---

### Post by minisori on 2006-04-11
I think you need java.

---

### Post by Sef on 2006-04-11
>  I think you need java.

I have blackstone java downloaded already, so it is not that.

Update: It's a bug.  Doing some googling, I found this:

> 

Ok, I've tracked it down. Add this line to the ~/.galeon/mozilla/galeon/prefs.js file:

user_pref("general.useragent.vendorSub", "1.3.21");


I can get to the directory, but how do I get to the prefs.js file?

[https://launchpad.net/distros/ubuntu/+source/galeon/+bug/3747]("https://launchpad.net/distros/ubuntu/+source/galeon/+bug/3747")

---

