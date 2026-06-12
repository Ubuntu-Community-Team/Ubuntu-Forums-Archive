---
title: "apt-get update"
date: 2005-07-29
forum: Desktop Environments
---

### Post by meeekael on 2005-07-29
having trouble with something.

```
meeekael@meeekael:~$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  mozilla-firefox mozilla-firefox-gnome-support
The following packages will be upgraded:
  binutils bzip2 dpkg dpkg-dev dselect fetchmail file-roller foomatic-db-hpijs
  foomatic-filters-ppds gaim gaim-data gdb gedit gedit-common gimp gimp-data
  gimp-python gnome-btdownload gnome-menus gtk2-engines-clearlooks gzip hpijs
  libbz2-1.0 libgcc1 libgimp2.0 libgnome-menu0 libgnutls11 libldap2 libmagick6
  libnspr4 libnss3 libpq3 libsmbclient libtiff4 linux-image-2.6.10-5-386
  mozilla-firefox-locale-en-gb openoffice.org openoffice.org-bin
  openoffice.org-gtk-gnome openoffice.org-l10n-en
  openoffice.org-thesaurus-en-us powernowd python-xdg python2.4-samba
  samba-common smbclient sudo synaptic tcpdump totem totem-gstreamer
  ttf-opensymbol vim vim-common wget xchat xchat-common zlib1g
58 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 1139kB/124MB of archives.
After unpacking 4396kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  dpkg gzip libbz2-1.0 zlib1g libtiff4 libmagick6 vim-common vim libgcc1
  dselect libgnutls11 libldap2 binutils dpkg-dev gdb sudo bzip2 fetchmail
  file-roller hpijs foomatic-db-hpijs gaim gaim-data libgnome-menu0 gedit
  gedit-common wget gimp gimp-data libgimp2.0 gimp-python gnome-btdownload
  gnome-menus gtk2-engines-clearlooks libnspr4 libnss3 libpq3
  linux-image-2.6.10-5-386 openoffice.org-bin openoffice.org-l10n-en
  ttf-opensymbol openoffice.org openoffice.org-gtk-gnome
  openoffice.org-thesaurus-en-us powernowd python-xdg python2.4-samba
  smbclient samba-common synaptic tcpdump totem totem-gstreamer xchat
  xchat-common foomatic-filters-ppds libsmbclient
Install these packages without verification [y/N]? y
0% [Waiting for headers]
```

Then it just sits there and does nothing.  The internet is active for about 20 seconds after hitting the final Y but then it goes back to idle and does nothing.

I am using the sources.list that was defined in the ubunutu starter guide.

I have used sudo apt-get update also, and that seems to run through fine...

```
meeekael@meeekael:~$ sudo apt-get update
Get:1 http://us.archive.ubuntu.com hoary Release.gpg [189B]
Get:2 http://security.ubuntu.com hoary-security Release.gpg [189B]
Get:3 http://archive.ubuntu.com hoary Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release.gpg
Get:4 http://us.archive.ubuntu.com hoary-updates Release.gpg [189B]
Get:5 http://security.ubuntu.com hoary-security Release [16.9kB]
Hit http://archive.ubuntu.com hoary Release
Hit http://us.archive.ubuntu.com hoary Release
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release
Hit http://archive.ubuntu.com hoary/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release
Hit http://us.archive.ubuntu.com hoary-updates Release
Hit http://archive.ubuntu.com hoary/multiverse Sources
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Hit http://us.archive.ubuntu.com hoary/main Sources
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Hit http://us.archive.ubuntu.com hoary/universe Packages
Hit http://us.archive.ubuntu.com hoary/universe Sources
Hit http://security.ubuntu.com hoary-security/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Ign http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Get:6 http://security.ubuntu.com hoary-security/main Sources [8814B]
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Ign http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Fetched 25.9kB in 15s (1647B/s)
Reading package lists... Done
```

Any help?  is the source down or something?

---

### Post by Phixion on 2005-07-29
I suggest you revert to default repositories (with universe etc enabled)

Here it is incase you haven't got a backup, I removed the cd rom source though.

```

## deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb http://gb.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu hoary universe
deb-src http://gb.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

```

See if this helps.

---

### Post by hod139 on 2005-07-29
Hoary backports is now an "official" repository 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

I have not had any problems with the hoary-extra repository though 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

As for why they aren't upgrading, I don't know what to say, especially since the update works.  Maybe with the "official" repository it will work?

---

### Post by Benchrest on 2005-07-29
I just tried it and upgrade went fine. I noticed you have us.----- at the start of your repository names. There were several post about problems with having US.  front of the repository name. I had the problem too ( but forget what it was  :wink:  ). 
Here is my sources.list:
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

How can I display my log to show you the entries I had from upgrade to show you. Might give a clue. Rich

---

