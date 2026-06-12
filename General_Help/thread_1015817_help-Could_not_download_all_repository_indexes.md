---
title: "help-Could not download all repository indexes"
date: 2008-12-19
forum: General Help
---

### Post by eworman on 2008-12-19
Hi there. I am facing error message like following when I click upload from Synaptic in version 8.10. 

IMHO that must be something with repositories so first of all I tried other's sources.list. The URLs from those files are proved to be valid by connecting them with Firefox. However, I used apt-get update and got error message as following 

 Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages
  403 Forbidden
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  403 Forbidden

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
cheng@cheng-laptop:/etc/apt$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory


Then I resorted to Synaptic. No problem for upload if I untick everything in Settings->Repositories. Then I tick 'Canonical supported Open Source software(main)' and reload. Again I got

 'Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  403 Forbidden
Some index files failed to download, they have been ignored, or old ones used instead.' 

However the URL mentioned here is accessible from my Firefox.


BTW, i had another machine on the same network with 8.04 and never had this kind of problem.


Can anyone kindly give me some suggestion? Many thanks

---

### Post by ajcham on 2008-12-19
Could you post your sources.list so I can have a look?

---

### Post by eworman on 2008-12-19
Thanks man. It's quite simple.

## See sources.list(5) for more information, especialy
# Remember that you can only use http, ftp or file URIs
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main
# CDROMs are managed through the apt-cdrom tool.


I got following error is I run 

sudo apt-get update


Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages
  403 Forbidden
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  403 Forbidden

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by geoffree on 2009-04-27
Similar problem. Help would be appreciated.

I am running Hardy Heron.  A triangle icon with an exclamation mark appeared on my tool bar. I clicked on the 'check' icon and got the following message:


**[SIZE="3"][CENTER]Could not download all repository indexes[/CENTER][/SIZE]**

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.46 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz)  404 Not Found

---

