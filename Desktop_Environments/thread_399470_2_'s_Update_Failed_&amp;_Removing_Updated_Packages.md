---
title: "2 ?'s: Update Failed &amp; Removing Updated Packages"
date: 2007-04-02
forum: Desktop Environments
---

### Post by magnoliablossom on 2007-04-02
All of my updates installed with no problems except for one.  I get the error message 1, a package failed to install.  The package is the OpenOffice core and I *think* the problem is that the download was corrupted when someone (kid, cough, cough) cancelled it while it was still downloading.  How can I remove the gunked up one so that it will download again?  Also I noticed that all the packages that did install are still there.  How can I get rid of them once they are used?

Thanks in advance.

---

### Post by cyberdork33 on 2007-04-02
look in /var/cache/apt/archives

---

### Post by magnoliablossom on 2007-04-02
I have no problems finding the packages.  They just won't let me delete them.

---

### Post by bapoumba on 2007-04-02
Hello, try to reinstall openoffice.org-core. Open a terminal (> Accessories > Terminal) and run:
```
sudo aptitude reinstall openoffice.org-core
```
You may have errors, please paste them in here.

Do you want to remove unused packages ? Which ones ?

---

### Post by magnoliablossom on 2007-04-02
i figured out how to remove the office core package and it's redownloading and installing now.  the packages i want to remove are the ones that have already been installed.  there are a lot of them and i really would like to know now a way i can remove all at once and not have to do them individually.

---

### Post by bapoumba on 2007-04-02
```
sudo aptitude clean
```
[QUOTE=man aptitude] clean
          Removes all previously downloaded .deb files from the package cache
          directory (usually /var/cache/apt/archives).
[/QUOTE]
Is that what you are looking for ?

---

### Post by magnoliablossom on 2007-04-02
exactly...thank you so much...it's been almost 6 months since i've been able to use linux and i have forgotten just about everything i'd learned. lol  thanks again.

---

