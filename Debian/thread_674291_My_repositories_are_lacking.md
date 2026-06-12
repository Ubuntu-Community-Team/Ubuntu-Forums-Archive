---
title: "My repositories are lacking"
date: 2008-01-21
forum: Debian
---

### Post by 449 on 2008-01-21
I recently switched from Ubuntu to Debian in an attempt to force myself to learn Linux more and for hardware reasons. In Ubuntu I had a lot more software sources listed in the Synaptic repositories. Where can I get more urls to add to my list? Here's my current list:

[http://img181.imageshack.us/img181/6963/screenshotrn1.png](http://img181.imageshack.us/img181/6963/screenshotrn1.png)

Thanks for your help.

---

### Post by kellemes on 2008-01-21
[http://www.apt-get.org/](http://www.apt-get.org/)

Here is my /etc/apt/sources.list
A lot of non working and old links, but a lot are pretty cool.
```

# /etc/apt/sources.list

# Meer repo's --> http://www.apt-get.org
# Alle officiele mirrors uit NL--> http://www.debian.org/mirror/mirrors_full#NL
#
# APT HOWTO:
# http://www.debian.org/doc/manuals/apt-howto/index.en.html
# Debian Package Management Quick-Start Guide
# http://sgeiger.mine.nu/docs/pkgmgmt.html
# Debian Tutorial - Removing and installing software
# http://www.debian.org/doc/manuals/debian-tutorial/ch-dpkg.html
# Using Debian Linux Software Packages and APT dselect and dpkg Package 
# Utilities http://www.aboutdebian.com/packages.htm
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -


#xgl - xserver-xgl
#deb http://www.prato.linux.it/~mnencia/debian xgl/
#deb-src http://www.prato.linux.it/~mnencia/debian xgl/

#############
### cdrom ###
#############
# deb cdrom:[Debian GNU/Linux testing _Lenny_ - Official Snapshot i386 NETINST Binary-1 20070801-09:28]/ lenny contrib main
# deb cdrom:[Debian GNU/Linux testing _Lenny_ - Official Snapshot i386 NETINST Binary-1 20070801-09:28]/ lenny contrib main

######################
### Stable - Etch  ###
######################
# deb http://http.nl.debian.org/debian/ stable main contrib non-free
# deb-src http://http.nl.debian.org/debian/ stable main contrib non-free
# deb http://security.debian.org/ stable/updates main contrib non-free
# deb http://ftp.debian-unofficial.org/debian/ sarge main contrib non-free restricted
# deb-src http://ftp.debian-unofficial.org/debian/ sarge main contrib non-free restricted

#######################
### Testing - Lenny ###
#######################
deb http://ftp.nl.debian.org/debian/ lenny main
deb-src http://ftp.nl.debian.org/debian/ lenny main
deb http://security.debian.org/ lenny/updates main contrib
deb-src http://security.debian.org/ lenny/updates main contrib
deb http://ftp.nl.debian.org/debian lenny main non-free contrib
# deb http://non-us.debian.org/debian-non-US lenny/non-US main contrib non-free

######################
### Unstable - Sid ###
######################
deb http://ftp.nl.debian.org/debian unstable main non-free contrib
deb-src http://ftp.nl.debian.org/debian unstable main non-free contrib
#deb http://non-us.debian.org/debian-non-US unstable/non-US main contrib non-free

####################
### Experimental ###
####################
#deb http://ftp.debian.org/debian/ experimental main non-free contrib
#deb-src http://ftp.debian.org/debian/ experimental main non-free contrib
#deb http://ftp.nl.debian.org/debian/ experimental main
#deb-src http://ftp.nl.debian.org/debian/ experimental main
#deb http://security.debian.org/ experimental/updates main contrib
#deb-src http://security.debian.org/ experimental/updates main contrib

############################################## 3d party ############################################

#######################
##       Gambas      ##
#######################
#deb http://apt.linex.org/linex/gambas/stable/ ./


#######################
##   Looking Glass   ##
#######################
#deb http://javadesktop.org/lg3d/debian stable contrib

#######################
## Multi-media Repos ##
#######################
# Marillat For info visit http://www.debian-multimedia.org
# Unstable
# deb http://www.debian-multimedia.org sid main
# deb-src http://www.debian-multimedia.org sid main
# Experimental
# deb http://www.debian-multimedia.org experimental main

# RareWares/Debian Multi-Media Repository for Unstable
# Info http://www.rarewares.org/debian.html
# deb http://www.rarewares.org/debian/packages/unstable/ ./
# RareWares/Debian Multi-Media Repository for Unstable - Experimental Staging
# deb http://www.rarewares.org/debian/packages/experimental/ ./

#################
##   Google    ##
#################
# Google testing repository
deb http://dl.google.com/linux/deb/ testing non-free
# Google software repository http://www.google.com/linuxrepositories/apt.html
# deb http://dl.google.com/linux/deb/ stable non-free

#################
##  ROX-filer  ##
#################
# deb ftp://ftp.berlios.de/pub/rox4debian binary/

###########
## Beryl ##
###########
# deb http://debian.beryl-project.org/ etch main
# deb-src http://debian.beryl-project.org/ etch main

###########
## GNOME ##     is dit wel waar?
###########
# deb http://bok.fas.harvard.edu/debian/ ./
# deb-src http://bok.fas.harvard.edu/debian/ ./
# deb-src http://ftp.acc.umu.se/mirror/mirrors.evilgeniuses.org.uk/debian/backports/woody gnome2.2/

##########
## Xfce ##
##########
# If you want Xfce packages more current than those in the official Debian
# repositories, you can get them here. XFCE 4.2.2 is now in Testing/Etch
# For more info see:
# http://www.os-works.com/view/debian/

# Testing (can be used on unstable as well):
# deb http://www.os-works.com/debian testing main
# deb-src http://www.os-works.com/debian testing main

#########
## KDE ##
#########
# Debian KDE 3.4 Team updates (3.42 is in unstable)
# For more information see: http://pkg-kde.alioth.debian.org/docs/
# deb http://pkg-kde.alioth.debian.org/kde-3.4.1/ ./

############################
## Enlightenment DR17/E17 ##
############################
# voor instaleren van 'enlightenment' heb ik eerst de standaard repo's uitgeschakeld, maar pinning kan ook als ik weet hoe dat werkt.
# deb http://soulmachine.net/debian unstable/
# deb http://people.debian.org/~amaya/debian ./
# deb-src http://people.debian.org/~amaya/debian ./

# deb http://gefechtsdienst.de/uman/files/ unstable main
# deb http://people.debian.org/~ljlane/downloads/ e17/

# Official Repository
# deb http://edevelop.org/debian/ unstable main
# mirror ->
# deb http://debian.uman.gefechtsdienst.de/debian/ unstable main

########################
# Beryl SVN Repository #
########################
# deb http://download.tuxfamily.org/3v1deb/ debian-unstable beryl-svn

#################
# Opera Browser #
#################
#deb http://deb.opera.com/opera/ sid non-free

##################################################################
# Swiftfox, a Mozilla Firefox i686 Optimized Official Repository #
##################################################################
deb http://getswiftfox.com/builds/debian unstable non-free

##############
# Claws Mail #
##############
# deb http://people.debian.org/~mones/claws-mail/i386/ ./
# deb-src http://people.debian.org/~mones/claws-mail/i386/ ./

####################
# Maxer Multimedia #
###################
# deb http://repos.knio.it/ testing main contrib non-free
# deb-src http://repos.knio.it/ testing main contrib non-free

#########
# Skype #
#########
# deb http://download.skype.com/linux/repos/debian/ stable non-free

#################################################
# InitNG- Next Generation Init Start Repository #
#################################################
# deb http://debian.mawk.org/debian/ binary/
# deb-src http://debian.mawk.org/debian/ source/

##################
# Blackdown Java #
##################
# Java can also be installed from the Unofficial repository listed above.

# For more info see:
# http://www.blackdown.org/java-linux/java2-status/index.html
# http://www.blackdown.org/java-linux/java2-status/jdk1.4-status.html#debs
# Testing:
# deb ftp://ftp.tux.org/java/debian/ testing non-free
# deb ftp://sunsite.dk/mirrors/java-linux/debian/ testing non-free
# Unstable:
# deb ftp://metalab.unc.edu/pub/linux/devel/lang/java/blackdown.org/debian unstable non-free
# deb ftp://ftp.tux.org/java/debian/ unstable non-free

############
# Marillat #
############
# deb http://debian.three-dimensional.net/debian-multimedia/ unstable main
# deb-src http://debian.three-dimensional.net/debian-multimedia/ unstable main

# This is Christian Marillat's package tree.  Very high-quality packages.
# Primarily audio/video related, including ffmpeg, libdvdcss, mplayer,
# pymusique, w32codecs, RealPlayer, and Adobe Acrobat. 
# For more info see: http://hpisi.nerim.net/  
#  or ftp://ftp.nerim.net/debian-marillat/index.html

# Stable:
# deb ftp://ftp.nerim.net/debian-marillat/ stable main
# Testing:
# deb ftp://ftp.nerim.net/debian-marillat/ etch main
# Unstable:
# deb ftp://ftp.nerim.net/debian-marillat/ sid main
# deb-src ftp://ftp.nerim.net/debian-marillat/ sid main

######################################
## VLC media player, libdvdcss, vlc ##
######################################
# VLC media player for Debian GNU/Linux, libdvdcss, vlc
# deb http://download.videolan.org/pub/videolan/debian/ sarge main
# deb-src http://download.videolan.org/pub/videolan/debian/ sarge main

#############
## MPlayer ##
#############
# deb ftp://ftp.nerim.net/debian-marillat/ etch main
# deb ftp://ftp.nerim.net/debian-marillat/ sid main
# deb ftp://ftp.nerim.net/debian-marillat/ unstable main

##########
## Wine ##
##########
# deb http://wine.sourceforge.net/apt/ binary/
# deb-src http://wine.sourceforge.net/apt/ source/

##########################################################
## Steve Kemp's -  Debian Sarge apt-get'able repository ##
##########################################################
# For more info visit: http://www.steve.org.uk/apt/
# deb http://www.steve.org.uk/apt sarge main contrib non-free
# deb-src http://www.steve.org.uk/apt sarge main contrib non-free

###########
## JEdit ##
###########
# deb http://dl.sourceforge.net/sourceforge/jedit ./
# deb-src http://dl.sourceforge.net/sourceforge/jedit ./

#############
## MySQL 5 ##
#############
# deb http://packages.dotdeb.org stable all
# deb-src http://packages.dotdeb.org stable all

############
## Gambas ##
############
# deb http://www.linex.org/sources/linex/debian/ cl gambas

###########################################
## Yzis editor / Debian Sid (i386/amd64) ##
###########################################
# deb ftp://download.yzis.org/yzis ./

################################
## ndsiwraper wireless driver ##
################################
# deb http://ndiswrapper.sourceforge.net/debian/ ./

#################################
## CLAMAV testing/sarge (i386) ##
#################################
# deb http://people.debian.org/~sgran/debian/ sarge main
# deb-src http://people.debian.org/~sgran/debian/ sarge main

##########################
## kpkgmanager, kio-apt ##
##########################
# deb http://lpnotfr.free.fr/debian/ ./
# deb-src http://lpnotfr.free.fr/debian/ ./

####################################################
## SE Linux (2.6 kernel) Debian/unstable packages ##
####################################################
# deb http://www.coker.com.au/newselinux/ ./

###################################
## div4linux, lame, win32-codecs ##
###################################
# deb ftp://ftp.mowgli.ch/pub/debian/ sid unofficial

###################################################################################
## games, xmms plugins, X on screen display, Flightgear, Fortunes,Quake,     ##
## Acroread, flashplayer-mozilla, KDE applets, KDE themes, A/V codecs and tools, ##
## Mencoder, Mplayer, OGMtools, WINE and others                     ##
## For more info visit: http://jeroen.coekaerts.be/debian/             ##
###################################################################################
# deb http://jeroen.coekaerts.be/debian/ unstable main contrib non-free
# deb-src http://jeroen.coekaerts.be/debian/ unstable main contrib non-free


```

---

### Post by fatality_uk on 2008-01-21
Was just going to post mine, but after seeing that kellemes, it's slightly embarassing. I have about 15 sources lol

---

### Post by 449 on 2008-01-21
> **kellemes said:**
> [http://www.apt-get.org/](http://www.apt-get.org/)

Here is my /etc/apt/sources.list
A lot of non working and old links, but a lot are pretty cool.
```

# /etc/apt/sources.list

# Meer repo's --> http://www.apt-get.org
# Alle officiele mirrors uit NL--> http://www.debian.org/mirror/mirrors_full#NL
#
# APT HOWTO:
# http://www.debian.org/doc/manuals/apt-howto/index.en.html
# Debian Package Management Quick-Start Guide
# http://sgeiger.mine.nu/docs/pkgmgmt.html
# Debian Tutorial - Removing and installing software
# http://www.debian.org/doc/manuals/debian-tutorial/ch-dpkg.html
# Using Debian Linux Software Packages and APT dselect and dpkg Package 
# Utilities http://www.aboutdebian.com/packages.htm
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -


#xgl - xserver-xgl
#deb http://www.prato.linux.it/~mnencia/debian xgl/
#deb-src http://www.prato.linux.it/~mnencia/debian xgl/

#############
### cdrom ###
#############
# deb cdrom:[Debian GNU/Linux testing _Lenny_ - Official Snapshot i386 NETINST Binary-1 20070801-09:28]/ lenny contrib main
# deb cdrom:[Debian GNU/Linux testing _Lenny_ - Official Snapshot i386 NETINST Binary-1 20070801-09:28]/ lenny contrib main

######################
### Stable - Etch  ###
######################
# deb http://http.nl.debian.org/debian/ stable main contrib non-free
# deb-src http://http.nl.debian.org/debian/ stable main contrib non-free
# deb http://security.debian.org/ stable/updates main contrib non-free
# deb http://ftp.debian-unofficial.org/debian/ sarge main contrib non-free restricted
# deb-src http://ftp.debian-unofficial.org/debian/ sarge main contrib non-free restricted

#######################
### Testing - Lenny ###
#######################
deb http://ftp.nl.debian.org/debian/ lenny main
deb-src http://ftp.nl.debian.org/debian/ lenny main
deb http://security.debian.org/ lenny/updates main contrib
deb-src http://security.debian.org/ lenny/updates main contrib
deb http://ftp.nl.debian.org/debian lenny main non-free contrib
# deb http://non-us.debian.org/debian-non-US lenny/non-US main contrib non-free

######################
### Unstable - Sid ###
######################
deb http://ftp.nl.debian.org/debian unstable main non-free contrib
deb-src http://ftp.nl.debian.org/debian unstable main non-free contrib
#deb http://non-us.debian.org/debian-non-US unstable/non-US main contrib non-free

####################
### Experimental ###
####################
#deb http://ftp.debian.org/debian/ experimental main non-free contrib
#deb-src http://ftp.debian.org/debian/ experimental main non-free contrib
#deb http://ftp.nl.debian.org/debian/ experimental main
#deb-src http://ftp.nl.debian.org/debian/ experimental main
#deb http://security.debian.org/ experimental/updates main contrib
#deb-src http://security.debian.org/ experimental/updates main contrib

############################################## 3d party ############################################

#######################
##       Gambas      ##
#######################
#deb http://apt.linex.org/linex/gambas/stable/ ./


#######################
##   Looking Glass   ##
#######################
#deb http://javadesktop.org/lg3d/debian stable contrib

#######################
## Multi-media Repos ##
#######################
# Marillat For info visit http://www.debian-multimedia.org
# Unstable
# deb http://www.debian-multimedia.org sid main
# deb-src http://www.debian-multimedia.org sid main
# Experimental
# deb http://www.debian-multimedia.org experimental main

# RareWares/Debian Multi-Media Repository for Unstable
# Info http://www.rarewares.org/debian.html
# deb http://www.rarewares.org/debian/packages/unstable/ ./
# RareWares/Debian Multi-Media Repository for Unstable - Experimental Staging
# deb http://www.rarewares.org/debian/packages/experimental/ ./

#################
##   Google    ##
#################
# Google testing repository
deb http://dl.google.com/linux/deb/ testing non-free
# Google software repository http://www.google.com/linuxrepositories/apt.html
# deb http://dl.google.com/linux/deb/ stable non-free

#################
##  ROX-filer  ##
#################
# deb ftp://ftp.berlios.de/pub/rox4debian binary/

###########
## Beryl ##
###########
# deb http://debian.beryl-project.org/ etch main
# deb-src http://debian.beryl-project.org/ etch main

###########
## GNOME ##     is dit wel waar?
###########
# deb http://bok.fas.harvard.edu/debian/ ./
# deb-src http://bok.fas.harvard.edu/debian/ ./
# deb-src http://ftp.acc.umu.se/mirror/mirrors.evilgeniuses.org.uk/debian/backports/woody gnome2.2/

##########
## Xfce ##
##########
# If you want Xfce packages more current than those in the official Debian
# repositories, you can get them here. XFCE 4.2.2 is now in Testing/Etch
# For more info see:
# http://www.os-works.com/view/debian/

# Testing (can be used on unstable as well):
# deb http://www.os-works.com/debian testing main
# deb-src http://www.os-works.com/debian testing main

#########
## KDE ##
#########
# Debian KDE 3.4 Team updates (3.42 is in unstable)
# For more information see: http://pkg-kde.alioth.debian.org/docs/
# deb http://pkg-kde.alioth.debian.org/kde-3.4.1/ ./

############################
## Enlightenment DR17/E17 ##
############################
# voor instaleren van 'enlightenment' heb ik eerst de standaard repo's uitgeschakeld, maar pinning kan ook als ik weet hoe dat werkt.
# deb http://soulmachine.net/debian unstable/
# deb http://people.debian.org/~amaya/debian ./
# deb-src http://people.debian.org/~amaya/debian ./

# deb http://gefechtsdienst.de/uman/files/ unstable main
# deb http://people.debian.org/~ljlane/downloads/ e17/

# Official Repository
# deb http://edevelop.org/debian/ unstable main
# mirror ->
# deb http://debian.uman.gefechtsdienst.de/debian/ unstable main

########################
# Beryl SVN Repository #
########################
# deb http://download.tuxfamily.org/3v1deb/ debian-unstable beryl-svn

#################
# Opera Browser #
#################
#deb http://deb.opera.com/opera/ sid non-free

##################################################################
# Swiftfox, a Mozilla Firefox i686 Optimized Official Repository #
##################################################################
deb http://getswiftfox.com/builds/debian unstable non-free

##############
# Claws Mail #
##############
# deb http://people.debian.org/~mones/claws-mail/i386/ ./
# deb-src http://people.debian.org/~mones/claws-mail/i386/ ./

####################
# Maxer Multimedia #
###################
# deb http://repos.knio.it/ testing main contrib non-free
# deb-src http://repos.knio.it/ testing main contrib non-free

#########
# Skype #
#########
# deb http://download.skype.com/linux/repos/debian/ stable non-free

#################################################
# InitNG- Next Generation Init Start Repository #
#################################################
# deb http://debian.mawk.org/debian/ binary/
# deb-src http://debian.mawk.org/debian/ source/

##################
# Blackdown Java #
##################
# Java can also be installed from the Unofficial repository listed above.

# For more info see:
# http://www.blackdown.org/java-linux/java2-status/index.html
# http://www.blackdown.org/java-linux/java2-status/jdk1.4-status.html#debs
# Testing:
# deb ftp://ftp.tux.org/java/debian/ testing non-free
# deb ftp://sunsite.dk/mirrors/java-linux/debian/ testing non-free
# Unstable:
# deb ftp://metalab.unc.edu/pub/linux/devel/lang/java/blackdown.org/debian unstable non-free
# deb ftp://ftp.tux.org/java/debian/ unstable non-free

############
# Marillat #
############
# deb http://debian.three-dimensional.net/debian-multimedia/ unstable main
# deb-src http://debian.three-dimensional.net/debian-multimedia/ unstable main

# This is Christian Marillat's package tree.  Very high-quality packages.
# Primarily audio/video related, including ffmpeg, libdvdcss, mplayer,
# pymusique, w32codecs, RealPlayer, and Adobe Acrobat. 
# For more info see: http://hpisi.nerim.net/  
#  or ftp://ftp.nerim.net/debian-marillat/index.html

# Stable:
# deb ftp://ftp.nerim.net/debian-marillat/ stable main
# Testing:
# deb ftp://ftp.nerim.net/debian-marillat/ etch main
# Unstable:
# deb ftp://ftp.nerim.net/debian-marillat/ sid main
# deb-src ftp://ftp.nerim.net/debian-marillat/ sid main

######################################
## VLC media player, libdvdcss, vlc ##
######################################
# VLC media player for Debian GNU/Linux, libdvdcss, vlc
# deb http://download.videolan.org/pub/videolan/debian/ sarge main
# deb-src http://download.videolan.org/pub/videolan/debian/ sarge main

#############
## MPlayer ##
#############
# deb ftp://ftp.nerim.net/debian-marillat/ etch main
# deb ftp://ftp.nerim.net/debian-marillat/ sid main
# deb ftp://ftp.nerim.net/debian-marillat/ unstable main

##########
## Wine ##
##########
# deb http://wine.sourceforge.net/apt/ binary/
# deb-src http://wine.sourceforge.net/apt/ source/

##########################################################
## Steve Kemp's -  Debian Sarge apt-get'able repository ##
##########################################################
# For more info visit: http://www.steve.org.uk/apt/
# deb http://www.steve.org.uk/apt sarge main contrib non-free
# deb-src http://www.steve.org.uk/apt sarge main contrib non-free

###########
## JEdit ##
###########
# deb http://dl.sourceforge.net/sourceforge/jedit ./
# deb-src http://dl.sourceforge.net/sourceforge/jedit ./

#############
## MySQL 5 ##
#############
# deb http://packages.dotdeb.org stable all
# deb-src http://packages.dotdeb.org stable all

############
## Gambas ##
############
# deb http://www.linex.org/sources/linex/debian/ cl gambas

###########################################
## Yzis editor / Debian Sid (i386/amd64) ##
###########################################
# deb ftp://download.yzis.org/yzis ./

################################
## ndsiwraper wireless driver ##
################################
# deb http://ndiswrapper.sourceforge.net/debian/ ./

#################################
## CLAMAV testing/sarge (i386) ##
#################################
# deb http://people.debian.org/~sgran/debian/ sarge main
# deb-src http://people.debian.org/~sgran/debian/ sarge main

##########################
## kpkgmanager, kio-apt ##
##########################
# deb http://lpnotfr.free.fr/debian/ ./
# deb-src http://lpnotfr.free.fr/debian/ ./

####################################################
## SE Linux (2.6 kernel) Debian/unstable packages ##
####################################################
# deb http://www.coker.com.au/newselinux/ ./

###################################
## div4linux, lame, win32-codecs ##
###################################
# deb ftp://ftp.mowgli.ch/pub/debian/ sid unofficial

###################################################################################
## games, xmms plugins, X on screen display, Flightgear, Fortunes,Quake,     ##
## Acroread, flashplayer-mozilla, KDE applets, KDE themes, A/V codecs and tools, ##
## Mencoder, Mplayer, OGMtools, WINE and others                     ##
## For more info visit: http://jeroen.coekaerts.be/debian/             ##
###################################################################################
# deb http://jeroen.coekaerts.be/debian/ unstable main contrib non-free
# deb-src http://jeroen.coekaerts.be/debian/ unstable main contrib non-free


```

WOW, great list thanks!

---

### Post by 449 on 2008-01-21
What do I need to be able to get this package in Synaptics?

[http://packages.debian.org/stable/gnome/](http://packages.debian.org/stable/gnome/)

---

### Post by smartboyathome on 2008-01-21
It should be in there by default if you are using debian etch.

---

### Post by 449 on 2008-01-21
> **smartboyathome said:**
> It should be in there by default if you are using debian etch.

It's not. :(

---

### Post by 449 on 2008-01-21
I might of removed it on accident could someone give me theirs? 

](*,)

---

### Post by Casual Fan on 2008-01-21
> **fatality_uk said:**
> Was just going to post mine, but after seeing that kellemes, it's slightly embarassing. I have about 15 sources lol

Wow, repository envy! :)

---

### Post by 449 on 2008-01-21
Could someone help me out here...

```
http://http.nl.debian.org/debian/dists/stable/main/binary-i386/Packages.gz: 404 Not Found [IP: 8.15.7.117 80]
http://http.nl.debian.org/debian/dists/stable/contrib/binary-i386/Packages.gz: 404 Not Found [IP: 8.15.7.117 80]
http://http.nl.debian.org/debian/dists/stable/non-free/binary-i386/Packages.gz: 404 Not Found [IP: 8.15.7.117 80]
http://http.nl.debian.org/debian/dists/stable/main/source/Sources.gz: 404 Not Found [IP: 8.15.7.117 80]
http://http.nl.debian.org/debian/dists/stable/contrib/source/Sources.gz: 404 Not Found [IP: 8.15.7.117 80]
http://http.nl.debian.org/debian/dists/stable/non-free/source/Sources.gz: 404 Not Found [IP: 8.15.7.117 80]

```

```
W: GPG error: http://ftp.debian-unofficial.org sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 394D199524C52AC3

```

```
W: Couldn't stat source package list http://http.nl.debian.org stable/main Packages (/var/lib/apt/lists/http.nl.debian.org_debian_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://http.nl.debian.org stable/contrib Packages (/var/lib/apt/lists/http.nl.debian.org_debian_dists_stable_contrib_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://http.nl.debian.org stable/non-free Packages (/var/lib/apt/lists/http.nl.debian.org_debian_dists_stable_non-free_binary-i386_Packages) - stat (2 No such file or directory)
```

---

### Post by 449 on 2008-01-21
anyone :confused:

---

### Post by kellemes on 2008-01-22
I gave you my list and told you a lot of links are old.
Don't copy-past links!

As you can see most are commented-out, often for a reason..
You're trying to use "nl.debian.org/debian/dists/stable".. stable is **not** what you want.. I guess.
What version of Debian are you using?
Testing? Sid? You're selection of repositories should depend on well thought out choices. You can't simply point to every Debian-branch available, this is going to give you a lot of crap.
As you can see I have uncommented the repositories I use, I have a mixed system. Using /etc/apt/preferences to set priorities..

```

Package: *
Pin: release a=testing
Pin-Priority: 650

Package: *
Pin: release a=unstable
Pin-Priority: 600

Package: *
Pin: release a=experimental
Pin-Priority: 550

```Edit: the sources.list includes an explanation of how to handle gpg-keys.

Pretty good and essential read-material. [http://www.debian.org/doc/manuals/apt-howto/index.en.html#contents](http://www.debian.org/doc/manuals/apt-howto/index.en.html#contents)

---

