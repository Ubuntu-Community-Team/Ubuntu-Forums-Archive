---
title: "Openoffice 3.0"
date: 2008-12-18
forum: General Help
---

### Post by oceanfirehawk on 2008-12-18
Could someone please point me in the direction of how to get openoffice 3.0 in my 8.04 repositories?

Thanks

---

### Post by gjoellee on 2008-12-18
As far I know the PPAs for this have been down quite a while now, you should try this: [http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

---

### Post by kanikilu on 2008-12-18
[https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive) ?

---

### Post by Izek on 2008-12-18
> **gjoellee said:**
> As far I know the PPAs for this have been down quite a while now, you should try this: [http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

PPAs seem to be done building. They were building for a while and thus I couldn't get OOo 3.0 in hardy. You may want to try again the PPAs now like kanikilu has pointed out.

---

### Post by stchman on 2008-12-18
> **oceanfirehawk said:**
> Could someone please point me in the direction of how to get openoffice 3.0 in my 8.04 repositories?

Thanks

I am not aware of a repository that will install OO3, but you can get the deb package for OO3 from openoffice.org.  There is also a 64 bit deb package.

---

### Post by kanikilu on 2008-12-18
> **stchman said:**
> I am not aware of a repository that will install OO3, but you can get the deb package for OO3 from openoffice.org.  There is also a 64 bit deb package.

ehh...the link is in my previous post ^ ;)

For the lazy:

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

(there are also hardy and jaunty packages, so obviously replace intrepid above with whatever you are using)

---

### Post by stchman on 2008-12-18
> **kanikilu said:**
> ehh...the link is in my previous post ^ ;)

For the lazy:

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

(there are also hardy and jaunty packages, so obviously replace intrepid above with whatever you are using)

Will the repositories also uninstall OO2.4 as well if you wish to install OO3.0?

---

### Post by fooman on 2008-12-18
> **stchman said:**
> Will the repositories also uninstall OO2.4 as well if you wish to install OO3.0?

yes, it will update all the 2.4 packages to the 3.0 versions.

just add the repos,  then run:

```
sudo apt-get update && sudo apt-get upgrade
```

...and you should be good.

---

### Post by whistlerspa on 2008-12-18
I somehow managed this without the command line stuff. I added the intrepid Openoffice repository in synaptic, marked all upgrades and then uninstalled open office 2.4.1.

Then I tried to install Openoffice 3 and was told that I couldn't due to conflicts so removed the intrepid repository and reloaded the repositories. This time the Openoffice 3 files were still there so I did an install using Synaptic and it worked.

---

### Post by markharding557 on 2008-12-18
the repo works i have used it no problems

---

