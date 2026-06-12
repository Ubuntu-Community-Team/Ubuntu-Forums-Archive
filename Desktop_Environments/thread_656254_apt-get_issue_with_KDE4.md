---
title: "apt-get issue with KDE4"
date: 2008-01-02
forum: Desktop Environments
---

### Post by sc0g on 2008-01-02
I recently tried to install the RC2 release of KDE4 using apt. I no longer want to try and install it. However, whenever I try to run updates, I get the following error:

[COLOR="Red"]
mascogin@sc0g:/var/cache/apt/archives$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kde4base-data
The following NEW packages will be installed:
  kde4base-data
0 upgraded, 1 newly installed, 0 to remove and 14 not upgraded.
8 not fully installed or removed.
Need to get 0B/61.3MB of archives.
After unpacking 89.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 136387 files and directories currently installed.)
Unpacking kde4base-data (from .../kde4base-data_3.94.0-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kde4base-data_3.94.0-0ubuntu1_all.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/share/kde4/services/kuiserver.desktop', which is also in package kdebase-runtime-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde4base-data_3.94.0-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

I have tried clearing the cache in /var/cache/apt but that did not fix the problem. Can someone please give me some tips as to how to fix this?

Thanks!

---

### Post by jamaisvu on 2008-01-02
[FONT=Franklin Gothic Medium]Try running K&#8594;System&#8594;Adept Manager, search for kde4 and mark any packages you have installed/broken as purge (right click and select from the drop down menu). Then ***preview the changes***. You can right click and change items in the preview too. When you are satisfied, apply the changes.

Let us know if this works/fails horribly![/FONT]

---

### Post by sc0g on 2008-01-02
Thank you so very much for your help. This seemed to have fixed the problem. It listed kde4base as "BROKEN." I simply chose "Request Remove", previewed the changes, then applied the changes. Apt-get seems to be working fine now.

FYI, I noticed you live in Birmingham, UK. That is interesting because i live in Birmingham, Alabama USA. :)

---

