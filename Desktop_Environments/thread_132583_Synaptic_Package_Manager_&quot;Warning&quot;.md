---
title: "Synaptic Package Manager &quot;Warning&quot;"
date: 2006-02-18
forum: Desktop Environments
---

### Post by ragjaws on 2006-02-18
I am gettin these messages whenever I open Synaptic Package Manager....any advice on how to stop it?

[b][i]W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)[/b][/i]

---

### Post by 5-HT on 2006-02-18
Looks like it's trying to read the package list from the intall CD.

There are some extra packages on the CD that are not installed with a default installation.

If you want to get rid of the warning, simply back up your current sources.list (just if anything goes wrong) 

```
 cp /etc/apt/sources.list /etc/apt/sources.list.backup 
```

open up your sources.list, 

```
 sudo nano -w /etc/apt/sources.list 
```

Find this line at the top:
```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 
```

and put a pound sign in front of it like so

```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 
```

Save your changes and exit nano by pressing control + x and saying "y" to save changes.

If you want to get packages from the CD later on, simply remove the pound sign.


*EDIT:

Another way to do it via synaptic would be to open up synaptic, click on settings > repositories, find the CD entry, and click remove.

You an add it again by clicking edit > add CD-ROM.

HTH

---

### Post by ragjaws on 2006-02-19
Thanks a lot this worked.

---

