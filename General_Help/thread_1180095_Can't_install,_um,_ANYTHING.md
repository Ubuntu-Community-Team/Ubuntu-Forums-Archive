---
title: "Can't install, um, ANYTHING"
date: 2009-06-06
forum: General Help
---

### Post by manoffeeling on 2009-06-06
If I try to install anything like this, for example:

$ sudo apt-get install hplip

I get something like this:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  hpijs-ppds hplip-doc python-qt3
Recommended packages:
  python-reportlab
The following packages will be upgraded:
  hplip
1 upgraded, 0 newly installed, 0 to remove and 269 not upgraded.
Need to get 621kB of archives.
After unpacking 0B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  hplip
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main hplip 1.7.3-0ubuntu1.1
  404 Not Found [IP: 91.189.88.140 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main hplip 1.7.3-0ubuntu1.1
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main hplip 1.7.3-0ubuntu1.1
  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_1.7.3-0ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_1.7.3-0ubuntu1.1_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I never had this problem before.  I tried doing those things it suggests and that didn't seem to work.  Sorry, I'm new to all this and I don't really know anything. :D

---

### Post by bacardiandwatermelon on 2009-06-06
You could try a different server?

---

### Post by michy99 on 2009-06-06
I don't think Fiesty is supported any longer. I believe the repositories have been moved to a back-up location, but I don't have the address handy at the moment.

---

### Post by kiridude on 2009-06-06
Since the OP said he was a beginner, that means go to System->Administration->Software Sources and in the Ubuntu software tab, hit the drop down menu from "download from" and try "main server," or any other server for that matter.

EDIT: oh, didn't notice the feisty part.  You should really upgrade to 9.04 first, Feisty is way old!

---

### Post by manoffeeling on 2009-06-06
Thank you for the help everybody!

---

### Post by michy99 on 2009-06-06
I found the feisty repositories at [http://old-releases.ubuntu.com/ubuntu/dists/feisty/](http://old-releases.ubuntu.com/ubuntu/dists/feisty/) You would have to change your sources.list to the new location. But upgrading to a newer version is probably your best bet.

---

