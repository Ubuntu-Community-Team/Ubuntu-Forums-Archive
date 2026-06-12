---
title: "DEBIAN repositories?"
date: 2006-07-13
forum: Desktop Environments
---

### Post by kundalinikat on 2006-07-13
Looking for a convenient list of Debian repositories I might add to my sources.list. Any takers? :)

---

### Post by mmcmonster on 2006-07-13
I'm not sure what you are aiming at.  If you want to *really* add debian repositories, I guess you can ask in the [Ubuntu repository forum]("http://www.ubuntuforums.org/forumdisplay.php?f=41") for what others use.

The problem is, you shouldn't use straight debian repositories, since they are not generally synced with Ubuntu. (You may end up with version conflicts between different libraries).

That being said, if you just want to increase the number of repositories to make sure you are getting the latest versions with synaptic, this is what I use. :-)

```

# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Dapper Backports
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Canonical Commercial packages
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

# Seveas' packages (GPG key: 1135D466)
# gpg --keyserver subkeys.pgp.net --recv 1135D466
# gpg --export --armor 1135D466 | sudo apt-key add -
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas all
#deb-src [http://users.lichtsnel.nl/~seveas]("http://users.lichtsnel.nl/%7Eseveas") dapper-seveas all

# Cipherfunk multimedia packages (GPG key: 33BAC1B3)
# gpg --keyserver subkeys.pgp.net --recv 33BAC1B3
# gpg --export --armor 33BAC1B3 | sudo apt-key add -
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main
#deb-src [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) dapper main

###
# Cinelerra CV
# Only use 1 of the following 3 lines!
# i686:
#deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/]("http://www.kiberpipa.org/%7Egandalf/ubuntu/dapper/cinelerra/i686/") ./
# Athlon XP:
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/athlonxp/]("http://www.kiberpipa.org/%7Egandalf/ubuntu/dapper/cinelerra/athlonxp/") ./
# Pentium 4:
#deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/]("http://www.kiberpipa.org/%7Egandalf/ubuntu/dapper/cinelerra/pentium4/") ./
# The following line is necessary for mjpegtools
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools]("http://www.kiberpipa.org/%7Egandalf/ubuntu/dapper/mjpegtools") ./

# Jahshaka real-time video editor
deb [http://repo.jahshaka.org/ubuntu/dapper/binary-i386](http://repo.jahshaka.org/ubuntu/dapper/binary-i386) ./

# kubuntu.org packages for the latest KDE version (GPG key: DD4D5088)
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main
#deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main

# kubuntu.org packages for the latest Koffice version (GPG key: DD4D5088)
# gpg --keyserver subkeys.pgp.net --recv DD4D5088
# gpg --export --armor DD4D5088 | sudo apt-key add -
deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) dapper main
#deb-src [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) dapper main

# kubuntu.org packages for the latest amaroK version (GPG key: DD4D5088)
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -
deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main
#deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main

# Opera browser
#deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

# Wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# XGL & compiz
# [http://ubuntuforums.org/attachment.php?attachmentid=7449&d=1143067510](http://ubuntuforums.org/attachment.php?attachmentid=7449&d=1143067510)
# gunzip quinn.key.asc.gz
# cat quinn.key.asc | sudo apt-key add -
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main

```

---

