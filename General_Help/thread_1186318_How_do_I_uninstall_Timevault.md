---
title: "How do I uninstall Timevault?"
date: 2009-06-13
forum: General Help
---

### Post by crash369 on 2009-06-13
A few months ago, I decided to try Timevault for snapshot backups.  Well, it has not been working correctly or at all, so I am going back to sbackup.

My problem is that I cannot figure out how to uninstall/remove timevault.  Synaptic can not find the package `timevault` and neither can apt-get.

I remember that I had a hard time installing it on my 64-bit system and that might have something to do with it.  Either way, I want timevault gone.

Any ideas?

Thanks.

---

### Post by khelben1979 on 2009-06-13
Have you tried [dselect]("http://en.wikipedia.org/wiki/Dselect")? It's good at identifying all types of packages, including broken ones.

(Don't forget to check out the wiki link.)

---

### Post by crash369 on 2009-06-14
The package was fine when I installed, it is the program that is not functioning well.  From reading the wiki, it seems that apt should be better than dselect.

---

### Post by khelben1979 on 2009-06-14
> **crash369 said:**
> From reading the wiki, it seems that apt should be better than dselect.

That's probably true, however dselect has always worked good for my needs.

---

### Post by Soul-Sing on 2009-06-14
So it wasn't is .deb you installed. Try to find the folder in which you installed it, maybe there a "readme" with a uninstall howto.

edit: 
> As soon as the database file is opened up by TimeVault it is not closed until the server exits (in particular when the Database class is destroyed). This makes it impossible to remove the drive or unmount the filesystem that TimeVault is storing backups on without first shutting down TimeVault. This is a problem because normal users shouldn't have to drop into the command line to execute something like sudo /etc/init.d/timevault stop just to unplug their drive. This problem is made worse because timevault is started at boot by default.

---

### Post by crash369 on 2009-06-14
Thanks khelben, I found it with dselect.  I ended up doing a remove with dpkg.


After some reading, this is what I learned:
- Downloaded .deb packages are not picked up by apt, since it only deals with packages in repositories.  Because synaptic and aptitude are apt front-ends, they could not find this package.

- dpkg knows about all packages, including downloaded .deb.  Since dselect is sort of a dpkg front-end, it listed the package.

[Solution]
sudo dpkg --remove timevault

---

