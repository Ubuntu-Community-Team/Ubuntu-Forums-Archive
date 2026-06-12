---
title: "gdk-imlib1 and libopenal0 'held back'"
date: 2006-06-15
forum: Desktop Environments
---

### Post by InsanePenguin08 on 2006-06-15
Lately (not sure when it began,) I noticed that when I tried to update Dapper, an error would pop up that said  gdk-imlib1 and libopenal0 were being held back and would not be updated.  How can I fix this?  

Also, can anyone give me what they consider an excellent sources.list?  The one I have now isn't too bad, but the keys for some of the repositories don't work.  This is mine currently:

```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu backports
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde-latest dapper main

# Penguin Liberation Front (PLF)
deb http://theli.free.fr/packages/dapper/ ./

# Dapper PLF repository (not yet available)
# deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
# deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

# Compiz (packages, GPG key: 31A5F97FED8A569E)
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main aiglx
deb http://compiztools.free.fr/debian unstable main

# Gaim 2 Beta 3
deb http://people.ubuntu.com/~seb128/deb ./

# Skype
deb http://download.skype.com/linux/repos/debian/ stable non-free

# Official Wine
# deb http://wine.sourceforge.net/apt/ binary/

# Wine Dapper
deb http://wine.lowvoice.nl/apt dapper main

deb http://www.getautomatix.com/apt dapper main

# PLF - Collection of Non-Free Proprietary Codecs & Applications
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free
```

Thanks alot!

---

