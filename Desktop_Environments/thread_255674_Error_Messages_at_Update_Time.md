---
title: "Error Messages at Update Time"
date: 2006-09-11
forum: Desktop Environments
---

### Post by Mookawaka on 2006-09-11
I am running Ubuntu 5.10.
Upon beginning the process of downloading updates with Synaptic I am getting these error messages of late.

W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)

Other than that my operating system is plugging along without noticeable difficulties.
Under the impression this may have something to do with the Ubuntu gang upgrading everything to the "fancy dragon" I decided to try it out as well.
It would appear that these error issues are hampering my ability to do so.

I have not been spending a large amount of my time at the computer this summer and have not looked at these forums much until this evening.  Pardon me if these issues have been gone over numerous times elsewhere.  I just am not sure what to be looking for.

---

### Post by croak77 on 2006-09-12
I think your /etc/apt/sources.list need to be updated. 

[http://koti.mbnet.fi](http://koti.mbnet.fi)  is not a repo. Maybe it was at one time. But not anymore.

[http://theli.free.fr](http://theli.free.fr) is for Listen but I don't think there is a breezy repo just dapper. 

The others appear to be plf repo's. I've never used those so I don't know if they are still around.

---

### Post by Mookawaka on 2006-09-12
I have deleted those repositories from my sources list and this seems to have solved the recurring error messages. Thank you for the tip.

Is there a way from the command line or otherwise to keep this file updated on a regular basis or do you just need to go in every once in a while and take out repositories that are no linger being maintained?

Onward to more stumbling through my operating system!

---

### Post by croak77 on 2006-09-12
Just be careful with non-official repo's. Most of the time they are for the current release only.

---

