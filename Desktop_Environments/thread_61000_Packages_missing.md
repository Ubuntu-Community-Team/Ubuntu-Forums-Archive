---
title: "Packages missing?"
date: 2005-08-30
forum: Desktop Environments
---

### Post by spedsta on 2005-08-30
Hi, I have installed ubuntu and using my 52k Modem(don't laugh) i have installed and tailored my system. So now I have full multimedia support and all apps I need installed. I used the Unofficial Ubuntu Guide to do this.

So when i wanted to now make a backup of .debs I checked a How To and went to all the directories where the downloaded .debs are supposed to be, except there are only 3 deb packages there !(Apache related)

Where have my packages all gone ? I went to Synaptic and checked options, there was one option to keep all downloaded packages, then there was another to only delete when the pakages are no longer available. My one had the " when the packages are no longer available' option.

Does this mean all my packages are deleted? I did change my sources list twice because a newer version of the guide had changed repositories listing.  If my packages are deleted, please tell me its still recoverable.

Its not a lot of packages but it took a hell of a long time to download the whole lot and i won't be doing that again anytime soon.

---

### Post by heimo on 2005-08-30
You looked into /var/cache/apt/archive ?
 ```
ls /var/cache/apt/archive
``` 

That's where .deb files that are automatically downloaded, will go, but as you've noticed, it's common to cleanup this directory every now and then. :( If those files are gone, it could be possible to recover using some tools, but it would probably be tedious and uncertain task.

EDIT: Links:
[http://packages.ubuntu.com/hoary/admin/tct](http://packages.ubuntu.com/hoary/admin/tct)
[http://www.stud.tu-ilmenau.de/~mojo/undelete.html](http://www.stud.tu-ilmenau.de/~mojo/undelete.html)
[http://home.fnal.gov/~muzaffar/undelete/README.html](http://home.fnal.gov/~muzaffar/undelete/README.html)
[http://recover.sourceforge.net/linux/](http://recover.sourceforge.net/linux/)

---

### Post by spedsta on 2005-08-30
I looked in that directory, thats the where i found the apche related .debs. I used  locate and that too only found those ones :(

Damn , all that time, anyway perhaps i can request a cd from one of the local ubuntu users, Lucky i am on the list.

Thanks

---

