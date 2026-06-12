---
title: "Upgrading Samba / Debian Repositories?"
date: 2006-02-14
forum: Desktop Environments
---

### Post by rolfotto on 2006-02-14
Ubuntu's version of Samba doesn't play nice with my OSX laptops (Why they don't have a newer version in the bug-fix this is beyond me :( )

I read on another thread that someone upgradet via debian repository to a newer samba without these problems.  Can someone point me how this is done?  All the repositories I add (in Synaptic) give error messages and I keep getting only Ubuntu's old Samba in the list....

---

### Post by queenorych on 2006-02-15
Using debian repositories is a bad idea.  you could use them to just get samba, but thats only a few files.  Just download the samba .deb files yourself with you handy browser, and type:

sudo dpkg -i (package to install)

---

