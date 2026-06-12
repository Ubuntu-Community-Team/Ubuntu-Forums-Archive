---
title: "Lyx is not installable via sources"
date: 2007-03-26
forum: Education &amp; Science
---

### Post by timmie on 2007-03-26
Hi,
this thread is not too *scientific*. But maybe other scientists are also affected...

I tried to install **lyx-qt** via the sources (aptitude / apt-get). But the message by the installer was that
> 
there's no install candidate for lyx-qt

When I opened Synaptic there was no version listed for **lyx-qt** in the column *latest version*.
I am only able to install *lyx-xfroms* which is not as nice as the QT version.


In the end I had to download it and install it by hand via Gdebi.

Can someone help me to correct this problem with the apt-get based installer?


***my sources.list:

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) edgy main restricted
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) edgy universe multiverse
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse

deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) edgy universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

# Medibuntu multimedia packages
# GPG key: 0C5A2783
# deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free

# deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free non-free

# Canonical Commercial packages
# GPG key: 437D05B5
deb [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe
deb-src [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial main

---

### Post by kleeman on 2007-03-26
That is a weird error. The xforms and qt versions have the same repo origin. If you look at the properties for lyx-qt in synaptic what versions are listed (there is a versions tab)?

---

### Post by timmie on 2007-03-26
Thanks kleeman,
I was hoping for you since you seem to be one of the most Lyx savvies around here ;-)

In the versions tab are there are the follwing versions listed:

[I]1.4.3-2~edgy1 (edgy-backports)
1.4.2-4 (edgy)[/I]

Please see the small screenshot attached.

Thank you very much for lokking at this!

---

### Post by kleeman on 2007-03-26
Well you have the backports enabled in your sources.list file and lyx-qt is in the repository you listed so I am very puzzled as to why it was not visible. Sounds like your database was corrupted in some way. Try

sudo apt-get update
to refresh it.

---

### Post by chirix on 2010-07-31
What do you need the lyx-qt for? can't you use just lyx? that might help until you figure out how to install lyx with qt. I am a newbie in this matter, but i think that may be a good idea. Good luck!

---

