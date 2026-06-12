---
title: "Aptitude gone nuts?"
date: 2005-12-14
forum: Desktop Environments
---

### Post by sudharshan on 2005-12-14
hi,
heres something weird...i have to reload the package list everytime i restart the program leave alone restarting the system..now that is very irritating..i just cant go on paying my internet bills for aptitude alone ;) ..jus kidding
i m getting some 'cannot stat' errors..any help as usual will be highly appreciated

cheers
Sudharshan S

---

### Post by Zelut on 2005-12-14
Well anytime you use Synaptic, apt-get or related it will need to refresh to the latest information from the list.  This shouldn't take long though... 

sounds like your 'cannot stat' errors are related to your sources.list &/or invalid, outdated entries.  Take a look at the [SourcesList]("http://wiki.ubuntu.com/SourcesList") entry on wiki to see that you have the correct entries.

---

### Post by sudharshan on 2005-12-15
Yes I get it..but updating my source.list every 5 minutes is bit too much..heres the exact error

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by sudharshan on 2005-12-15
On closer inspection...somehow my box is deleting the sources list by itself...checked out  whether any cron job is the culprit..but its not..

brrr....theres a ghost in my pc

---

