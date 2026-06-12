---
title: "unable to lock the administration directory (/var/lib/dpkg/)"
date: 2009-05-27
forum: Desktop Environments
---

### Post by gusteman on 2009-05-27
Hi there, please don't shoot the pianoplayer, especially since I am still an apprentice. This might look like a silly problem, but I'm not that good in solving PC-prolems, so here it goes:
since a few days I am getting a strange icon on the Gnome Desktop: it is triangular orange and when pointing to it I get a notification that there seams to be something wrong with my internet-connetions (I don't have any problems using Firefox and Thunderbird). When I click the icon it opens up my update manager. There I am notified that my system is up-to-date. Since the icon advised me to do a check-up, and since I am a gentle obediant person, I do a check-up which results in:

[COLOR="Blue"]Retrieving [http://be.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz](http://be.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz) 404 Not Found [IP: 195.238.1.5 80] failed

Retrieving [http://be.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz](http://be.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 195.238.1.5 80] failed

Retrieving [http://be.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz](http://be.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz) 404 Not Found [IP: 195.238.1.5 80] failed

Retrieving [http://be.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz](http://be.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 195.238.1.5 80] failed
[/COLOR]
[COLOR="Blue"]Retrieving [http://be.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.gz](http://be.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/source/Sources.gz) 404 Not Found [IP: 195.238.1.5 80] failed

Retrieving [http://be.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.gz](http://be.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/source/Sources.gz) 404 Not Found [IP: 195.238.1.5 80] failed

Retrieving [http://be.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.gz](http://be.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/source/Sources.gz) 404 Not Found [IP: 195.238.1.5 80] failed

Retrieving [http://be.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz](http://be.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/source/Sources.gz) 404 Not Found [IP: 195.238.1.5 80] failed

Retrieving some indexing files failed, these are either ignored, or older versions are installed.
[/COLOR]
After that I opened the terminal and performed:

[COLOR="Blue"]sudo apt-get -f install[/COLOR]

which resulted in:

[COLOR="Blue"]The following packages were automatically installed and are no longer needed:

  libpopt-dev libwvstreams4.3-extras libgtkhtml3.8-15 libmtp6 libgoffice-0-common libneon26 xserver-xorg-video-amd

  gnome-bin libsnmp10 libmagick++9c2a g++-4.1 libgnome32 libglew1.4 gnome-libs-data libdns32 libart2 libgnorbagtk0

  libgpod2 libstdc++6-4.1-dev libsvg1 libpcrecpp0 gnome-themes-extras mozilla-firefox-locale-nl-nl gutsy-wallpapers

  libgnomeui32 libgtkhtml2.0-cil libdb3 libgsl0 libgoffice-0-4 libwvstreams4.3-base imlib-base liborbit0 gdk-imlib11[/COLOR]

[COLOR="Blue"]  libdb4.5 libtotem-plparser7 libuniconf4.3 libgnomesupport0 libobjc1 libisc32 bacula-common gl-117-data gnustep-ppd

  libgnorba27 libntfs-3g16 librsvg2.0-cil

Use 'apt-get autoremove' to remove them.
gusteman@gusteman-desktop:~$[/COLOR] 

So I did:

[COLOR="Blue"]apt-get autoremove
[/COLOR]

And the result was:

[COLOR="Blue"]E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
[/COLOR]

Any ideas what I did wrong?
 
By the way, I am using Ubuntu 8.04.2

---

### Post by taurus on 2009-05-27
1.  If you are still running feisty, then perhaps it's time to upgrade since it's no longer supported and the repos have been moved, [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/).

2.  Don't forget to include the sudo in front of the command.

```
sudo apt-get autoremove
```

---

### Post by gusteman on 2009-05-27
>Hi there taurus.
Sorry if I did not point it out clearly enough:
I upgraded to hardy about 6 months ago because I wanted to be shur most of the bugs had been solved before I upgraded. And I did include "sudo" in front, but forgot to mention it. My main problem is that even after having upgraded to Hardy I have the impression that I still get directed to upgrades for Feisty. When I check Synaptic under Preferences I am connected to the main server and am directed to Hardy. Any reason why Update Manager still looks for Feisty updates? Thanks very much for yr quick reply.

---

### Post by taurus on 2009-05-27
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by gusteman on 2009-05-27
Hi there taurus, I entered what you suggested and this is the outcome:

gusteman@gusteman-desktop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://be.archive.ubuntu.com/ubuntu/](http://be.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed main universe multiverse

gusteman@gusteman-desktop:~$ 

I hope this will be usefull to you. Thanks allready for your help.

---

### Post by gusteman on 2009-05-27
This might help:
I made a screenshot where you can see the icon I mentioned. It appears in the main menu-bar right above the mouse pointer, just above the "F" of Firefox.
I have just one little problem: I can't seem to be able to paste the screenshot in this quick reply. In the past I allready pasted screenshots in posts, so I presume it is not possible to do the same in a quick reply?

---

