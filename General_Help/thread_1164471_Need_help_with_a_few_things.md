---
title: "Need help with a few things"
date: 2009-05-19
forum: General Help
---

### Post by notoriousmic24 on 2009-05-19
Sup guys, I'm using 9.04, and I have some questions/issues on a few things...

~I'm getting permission issues left and right. For example:

-when trying to blacklist pcspeaker, I get this:
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.
-when trying to install something by terminal i get this:
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

~Also, anyone know how to get ABGX working on Ubuntu? I've gone through some tutorials but no luck

~Lastly, I'm trying to get video out capabilities (getting my laptop to be viewed on my TV). Anyone point my in the right direction on that?

I'm using a Dell Inspiron E1505 Laptop
Thanks

---

### Post by SentientFluid on 2009-05-19
> **notoriousmic24 said:**
> Sup guys, I'm using 9.04, and I have some questions/issues on a few things...

~I'm getting permission issues left and right. For example:

-when trying to blacklist pcspeaker, I get this:
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.
-when trying to install something by terminal i get this:
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

How are you trying to edit the first file mentioned?  Is it a text file? Open Terminal and try ```
gksudo gedit /path/to/file.name
```

You should be able to save now though you may want to backup the file first, just to be safe.

What command(s) are you using to install files through Terminal?  Looks likew you're trying to install .deb files?  ou need to sudo that as well: ```
sudo dpkg -i /path/to/debfile.deb
```

---

