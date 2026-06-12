---
title: "How do I update The GIMP?"
date: 2009-04-04
forum: General Help
---

### Post by Connoro on 2009-04-04
Hey, everybody. I'm new to using Ubuntu, I installed 8.04 LTS yesterday, and I'm having some trouble updating The GIMP. I'm running 2.4.5, which is pretty old compared to the latest, 2.6.6. However, the package manager seems to believe I have the latest version installed.

How can I install the latest version of The GIMP?

---

### Post by 3Miro on 2009-04-04
Depends on which version they have in the repos. Ubuntu is fairly slow to add new packages to the repos, mostly because they actually test stuff. You can goto Gimp's web-page and look to see if they have a newer .deb for ubuntu. You can download and install it from there.

---

### Post by Connoro on 2009-04-04
> **3Miro said:**
> Depends on which version they have in the repos. Ubuntu is fairly slow to add new packages to the repos, mostly because they actually test stuff. You can goto Gimp's web-page and look to see if they have a newer .deb for ubuntu. You can download and install it from there.

The website is telling me to use apt-get.

---

### Post by 3Miro on 2009-04-04
Go to System -> Admin -> Synaptic and refresh the software list. Then try to update.

---

### Post by Connoro on 2009-04-04
> **3Miro said:**
> Go to System -> Admin -> Synaptic and refresh the software list. Then try to update.

Still the same problem. Might it have something to do with me using 8.04 LTS as opposed to 8.10?

---

### Post by 3Miro on 2009-04-04
Newer versions of Ubuntu have newer programs in the repos.

You can try and look for a community run repo (as opposed to the official Canonical repo). There is more risk thought that "newer" updates would always work not as supposed to.

---

### Post by lovinglinux on 2009-04-04
Donwload the deb file from [http://www.getdeb.net/app/Gimp](http://www.getdeb.net/app/Gimp) then double click it to install.

---

### Post by CatKiller on 2009-04-04
Each version of Ubuntu is frozen with the versions of packages that were current when it was released. Security patches and bugfixes are backported. New versions for new features are generally not included until the next Ubuntu release. So you won't get a new version of the GIMP unless you upgrade to a new version of Ubuntu (the version that comes with 8.10 is 2.6.1; 2.6.6 will come with 9.04 when that is released) or to find someone who will package the new version for you. 

(The Wine project does this; they host their own repository with the latest version, so if you've added their repository to your sources.list Wine will get automatically updated.)

[www.getdeb.net](www.getdeb.net) have .debs for the GIMP available for download. I've never used it, so I don't know if there are any problems you should know about.

Of course, you could always compile it from source :)

---

