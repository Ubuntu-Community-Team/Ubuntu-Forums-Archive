---
title: "system totally messed up, in need of dire help"
date: 2006-06-10
forum: Desktop Environments
---

### Post by truenemesis on 2006-06-10
hello,
i got three major issues.

first off, I cant view https sites with Firefox. Im missing a package called nss3. Actually, aptitude is telling me its broken. And synaptic cant find it anywhere and cant fix it. Any idea how to fix this? Maybe I should switch to the original source.list? Does anyone have a copy of the original dapper souce.list?

None of my gnome-panel applets are working anymore. When everything boots up, I get an error message.

The panel encountered a problem while loading "OAFIID:GNOME_ClockApplet".
Do you want to delete the applet from your configuration?

I tried to reinstall gnome-panel. I get dependency problems with the gnome-panel packages.

And finally, I cant play any music. I keep getting internal data flow error. I uninstalled all gstreamer 8 files and only have gstreamer 10 files.

im also missing a file called libgstcontroller when I try to use listen player. And I cant find this package anywhere on the net.

SOMEONE PLEASE HELP ME.

---

### Post by Ramses de Norre on 2006-06-10
For your first issue: sudo aptitude install libnss3, or sudo apt-get install -f to fix broken packages.
This is my sources.list: ```
ramses@icarus:~$ cat /etc/apt/sources.list
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -
##deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

# Penguin Liberation Front (PLF)
deb http://theli.free.fr/packages/dapper/ ./

# Dapper PLF repository (not yet available)
# deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
# deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

# Skype
deb http://download.skype.com/linux/repos/debian/ stable non-free

## wine
deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main

## opera web browser
##deb http://deb.opera.com/opera/ etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
##deb http://people.ubuntu.com/~doko/OOo2 ./

## kubuntu.org packages for the latest KDE version (GPG key: DD4D5088)
##deb http://kubuntu.org/packages/kde-latest dapper main

## kubuntu.org packages for the latest Koffice version (GPG key: DD4D5088)
##deb http://kubuntu.org/packages/koffice-latest dapper main

## kubuntu.org packages for the latest amaroK version (GPG key: DD4D5088)
##deb http://kubuntu.org/packages/amarok-14 dapper main

# Cipherfunk multimedia (GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main
deb-src ftp://cipherfunk.org/pub/packages/ubuntu dapper main

```

I don't know about the other issues..

---

### Post by az on 2006-06-10
You probably have a bunch of broken packages.  Just fix them.

You may have a perfectly fine sources.list, but may have interrupted an update or something.


sudo apt-get update

sudo apt-get dist-upgrade

if you get any errors, run

sudo apt-get -f install
and then try again.

You may also just run synaptic and tell it to fix any broken packages.

Then come back and report any residual problems.

---

### Post by mdurham on 2006-06-10
I think what truenemesis meant was "in dire need of help" who would want "dire help"? 
:)

---

