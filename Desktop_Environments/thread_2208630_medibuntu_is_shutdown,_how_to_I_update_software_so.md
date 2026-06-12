---
title: "medibuntu is shutdown, how to I update software sources &amp; installed packages?"
date: 2014-03-01
forum: Desktop Environments
---

### Post by nosmadar on 2014-03-01
[HTML]https://help.ubuntu.com/community/Medibuntu[/HTML]

This might be easier than I think, but I don't want hose my system.
I've been unable to get a complete package update list for about 150 days now.
The problem is that I installed a number of multi-media packages from the 'medibuntu' repository, 
[HTML]http://packages.medibuntu.org/precise free non-free[/HTML]
which can no longer be located. 
Because apparantly it's been shut down (see link at top of this post).

How can I update my software sources and installed packages to reflect the new location of the repository and get a complete package list.

---

### Post by nosmadar on 2014-03-01
Sorry for the Duplicate!  Didn't realize that editing the Title to fix 'to" to be "do"  would create an entirely new post.
Hopefully a Moderator can get rid of this one please?

---

### Post by Frogs Hair on 2014-03-01
In order to remove the source open the update manger and proceed to settings other software and remove all instances of medibuntu. many of the codecs are obsolete or now included with the ubuntu-restricted-extras package which is updated via the update manager.

---

### Post by oldfred on 2014-03-01
Some more links:

 Media howto: 
[http://ubuntuforums.org/showthread.php?t=2179777](http://ubuntuforums.org/showthread.php?t=2179777)
Older Ubuntu versions may not have new install-css.sh
[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)
(make sure to install/upgrade the libdvdread4 package first)
sudo apt-get install libdvdread4
new libdvdread 4 is already in 13.10
The new libdvdread4 has an updated install-css.sh that will install libdvdcss2 from a videolan repo
[https://launchpad.net/ubuntu/+source/libdvdread](https://launchpad.net/ubuntu/+source/libdvdread)
Medibuntu discontinued April 2013
[https://launchpad.net/medibuntu/+announcement/11219](https://launchpad.net/medibuntu/+announcement/11219)
[http://gauvain.pocentek.net/node/61](http://gauvain.pocentek.net/node/61)

---

### Post by monkeybrain20122 on 2014-03-01
After installing ubuntu-restricted-extras the only additional thing that you would need is libdvdcss2 for playing dvds. Run in the terminal

```
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by nosmadar on 2014-03-01
Thanks everyone!

---

