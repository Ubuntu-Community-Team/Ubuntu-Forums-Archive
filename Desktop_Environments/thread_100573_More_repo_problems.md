---
title: "More repo problems"
date: 2005-12-07
forum: Desktop Environments
---

### Post by greymoose58 on 2005-12-07
I hope this is the right forum for this. I've been trying to reload Gnucash after reinstalling Breezy. As far as I can remember it is in the Universe repository. My machine has been telling me there are no such thing 'stat (2 No such file or directory)'. 

I have tried accessing the repos using synaptic and apt-get. I replaced the whole sources.list with the one suggested in these forums (by PoofyHairedGuy, I think). Then I found source-o-matic and replaced sources.list with one from there. I went through and added in the sources line by line - some worked one time but not the next.

I see that several people have said that the repositories go down now and then so wait a few hours. I've been at this for about 6 hours give or take. I figure that is probably long enough to wait. Correct me if I'm being impatient.

So I have two questions: Is there any way to know the repos are down other than not being able to acess them? Does anyone have any idea what I have done to cause this to happen?

This is my sources.list in case it helps:

# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

# Ubuntu supported packages (packages)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu supported packages (sources)
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu community supported packages (packages)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Ubuntu community supported packages (sources)
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Seveas' packages (packages)
deb [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas all

# Seveas' packages (sources)
# deb-src [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas all

# Ubuntu backports project (packages)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# Ubuntu backports project (sources)
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# Cipherfunk multimedia packages (packages)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) breezy main

# Cipherfunk multimedia packages (sources)
# deb-src [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) breezy main

# Bleeding edge wine packages (packages)
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

# Bleeding edge wine packages (sources)
# deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

# OpenOffice.org 2 final packages (packages)
deb [http://people.ubuntu.com/~doko/OOo2/](http://people.ubuntu.com/~doko/OOo2/) ./


Thanks in advance.

---

### Post by aysiu on 2005-12-07
It's here:

[http://archive.ubuntu.com/ubuntu/pool/universe/g/gnucash/](http://archive.ubuntu.com/ubuntu/pool/universe/g/gnucash/)

I know you've already changed up your sources.list a few times, but try the first link in my sig. I'm 100% sure it works... because that's my sources.list, and I have Gnucash in my repositories.

---

### Post by greymoose58 on 2005-12-08
Thanks aysiu,

I had already tried your sources.list but I tried it again and when I ran sudo apt-get update I got this:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  MD5Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  MD5Sum mismatch
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
 
Thanks for the directory too but I'm really lost as to how to get gnucash up an running from there. I've always used apt-get to install things.

---

### Post by Joeak on 2005-12-08
I have a default Breezy install.  I used Synaptic to add the universe and multiverse repositories as I found I needed them for a variety of programs.  I just installed gnucash with:

$ sudo apt-get install gnucash

It did complain that it couldn't verify about 15 of the packages, but I answered Y to install anyway and it worked.

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe main restricted multiverse
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

---

### Post by greymoose58 on 2005-12-08
Thanks Joeak,

That did the trick. It should be easier to invoice my customers now.

Now if I had only thought to back up the cahnges I made to the invoice format.......

I appreciate the help from both of you.

---

