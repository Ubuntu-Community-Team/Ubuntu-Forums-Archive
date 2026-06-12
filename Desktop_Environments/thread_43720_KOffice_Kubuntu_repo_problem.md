---
title: "KOffice Kubuntu repo problem?"
date: 2005-06-23
forum: Desktop Environments
---

### Post by Bob D. on 2005-06-23
Getting the following error for some packages when trying to install KOffice 1.4.0 from the Kubuntu repo:

 ```
Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?

W: Failed to fetch http://kubuntu.org/hoary-koffice14/pool/koffice/koffice-data_1.4.0-0ubuntu0hoary2_all.deb
  Size mismatch


W: Failed to fetch http://kubuntu.org/hoary-koffice14/pool/koffice/kivio-data_1.4.0-0ubuntu0hoary2_all.deb
  Size mismatch


W: Failed to fetch http://kubuntu.org/hoary-koffice14/pool/koffice/koffice_1.4.0-0ubuntu0hoary2_all.deb
  Size mismatch
``` 


All the other packages seem to download fine. I cancel the install since these packages would be missing.

Any ideas or thoughts on what is going on?

Bob

---

### Post by chandra on 2005-06-23
Have you filed a bug report at Bugzilla?

---

### Post by z_pod on 2005-06-23
[QUOTE=Bob D.]Getting the following error for some packages when trying to install KOffice 1.4.0 from the Kubuntu repo:

 ```
Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?

W: Failed to fetch http://kubuntu.org/hoary-koffice14/pool/koffice/koffice-data_1.4.0-0ubuntu0hoary2_all.deb
  Size mismatch


W: Failed to fetch http://kubuntu.org/hoary-koffice14/pool/koffice/kivio-data_1.4.0-0ubuntu0hoary2_all.deb
  Size mismatch


W: Failed to fetch http://kubuntu.org/hoary-koffice14/pool/koffice/koffice_1.4.0-0ubuntu0hoary2_all.deb
  Size mismatch
``` 


All the other packages seem to download fine. I cancel the install since these packages would be missing.

Any ideas or thoughts on what is going on?

Bob[/QUOTE]
 Hi,

Just downloaded .deb from [http://ftp.mirror.ac.uk/mirror/ftp.kde.org/pub/kde/stable/koffice-1.4/kubuntu/pool/koffice/](http://ftp.mirror.ac.uk/mirror/ftp.kde.org/pub/kde/stable/koffice-1.4/kubuntu/pool/koffice/).

I had to apt-get libwv2 from reps to solve a dependency.

Made a sudo dpkg -i *.

Koffice is working really fine... It's fast fast fast... OMG it's fast !!

bye

---

### Post by Bob D. on 2005-06-23
[QUOTE=chandra]Have you filed a bug report at Bugzilla?[/QUOTE]
Just filed [https://bugzilla.ubuntu.com/show_bug.cgi?id=12116](https://bugzilla.ubuntu.com/show_bug.cgi?id=12116)

Hopefully this gets resolved soon.

Thanks!

Bob

---

### Post by !nkubus on 2005-06-23
I have the same error ant the second repo does not work either.

keep us informed if youresolve the issue in the meantime i will try the manual way.

I can't wait to try krita :) bye bye gimp :) on a kde computer

---

### Post by Bob D. on 2005-06-23
Just talked to Jonathan Riddell on IRC and he fixed the repo problem. Just installed KOffice and it seems to be working fine. KWord is FAST! :)

Bob

---

### Post by !nkubus on 2005-06-23
Awesome thanks for the update :D

---

