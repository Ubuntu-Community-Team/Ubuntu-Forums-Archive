---
title: "E17 repo for Ubuntu 8.10"
date: 2009-01-01
forum: Desktop Environments
---

### Post by spajix on 2009-01-01
I can't find any good Enlightenment 17 repo's for Ubuntu 8.10.
The only one I found that looked promising is [http://www.ubuntugeek.com/howto-install-e17-enlightenment-desktop-in-ubuntu.html](http://www.ubuntugeek.com/howto-install-e17-enlightenment-desktop-in-ubuntu.html) but the repo key won't download...
So anyone know any good repo's?

---

### Post by spajix on 2009-01-01
I followed this [http://ubuntuforums.org/showthread.php?t=916690&highlight=install+e17](http://ubuntuforums.org/showthread.php?t=916690&highlight=install+e17) and got this ```
:~$ sudo apt-get install e17-svn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  e17-svn: Depends: giblib-dev but it is not installable
           Depends: libgtk1.2-dev but it is not installable
E: Broken packages

```
Any idea's anyone?
I don't wanna go around install a bunch of dependencies by hand, that ends in a huge mess...
Thanks in advance for any help
Cheers

---

### Post by spajix on 2009-01-01
I fixed it by the advice on this thread
[http://ubuntuforums.org/showthread.php?p=6475514#post6475514](http://ubuntuforums.org/showthread.php?p=6475514#post6475514)

---

