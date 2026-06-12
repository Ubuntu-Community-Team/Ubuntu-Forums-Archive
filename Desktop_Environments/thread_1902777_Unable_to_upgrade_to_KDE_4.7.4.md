---
title: "Unable to upgrade to KDE 4.7.4"
date: 2011-12-31
forum: Desktop Environments
---

### Post by grr51 on 2011-12-31
I currently have KDE 4.7.3 which crashes regularly.  I filed a crash report and was told that the problem has been fixed in version 4.7.4.
However, when I try to update, the reply is that I already have the latest version!!
Please refer to the following captures:
[INDENT]sudo apt-get update
 ...
Fetched 2,626 B in 4s (623 B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
[/INDENT]I don't know what the above error is about since I do not have this entry in the sources.list

Then, trying to update the workspace:
[INDENT]sudo apt-get install kde-workspace
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kde-workspace is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/INDENT]Then, checking the current version of the workspace:
[INDENT]apt-cache policy kde-workspace
kde-workspace:
  Installed: 4:4.7.3a-0ubuntu0.1
  Candidate: 4:4.7.3a-0ubuntu0.1
  Version table:
 *** 4:4.7.3a-0ubuntu0.1 0
        500 [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) oneiric-updates/main i386 Packages
        100 /var/lib/dpkg/status
     4:4.7.1-0ubuntu5 0
        500 [http://ubuntu.mirror.iweb.ca/](http://ubuntu.mirror.iweb.ca/) oneiric/main i386 Packages
[/INDENT]Any clue of what to do next?

Thanks,

grr

---

### Post by oldos2er on 2011-12-31
[http://www.kubuntu.org/kde-sc-474](http://www.kubuntu.org/kde-sc-474)

---

### Post by grr51 on 2011-12-31
Thank you oldos2er!

I added the ppa to the software sources and could now upgrade to 4.7.4.

On a different subject, I tried to update my profile to show that I am now using version 11.10 with Kubuntu but the reply is that I don't have access rights!  Any idea why?

Thanks,

grr51

---

### Post by PaulW2U on 2011-12-31
> **grr51 said:**
> On a different subject, I tried to update my profile to show that I am now using version 11.10 with Kubuntu but the reply is that I don't have access rights!

See here - [http://ubuntuforums.org/showthread.php?t=1836816](http://ubuntuforums.org/showthread.php?t=1836816)

---

### Post by grr51 on 2011-12-31
Thanks PaulW2U,

That explains why.  Since I do not post very often, my profile will be quite out of date as far version used.

grr51

---

