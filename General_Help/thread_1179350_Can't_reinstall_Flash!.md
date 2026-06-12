---
title: "Can't reinstall Flash!"
date: 2009-06-05
forum: General Help
---

### Post by Saruman_W on 2009-06-05
Recently my browser was crashing for some reason every time I tried to view a YouTube video, so I decided I'd try to remove Flash Player 10 and reinstall the other one, so I followed some uninstall instructions:

sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

Then I tried to go to the terminal and reinstall it

sudo apt-get install flashplugin-nonfree

And I get this error at the end:

The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: nspluginwrapper (>= 0.9.91.4-2ubuntu1) but it is not going to be installed
E: Broken packages

So I figured maybe I need to reinstall nspluginwrapper:

sudo apt-get install nspluginwrapper

But nope, all I get is this:

The following packages have unmet dependencies:
  nspluginwrapper: Depends: ia32-libs (>= 1.6) but it is not going to be installed
E: Broken packages

So, I try to install THAT:

sudo apt-get install ia32-libs

Still no, I get more errors:

The following packages have unmet dependencies:
  ia32-libs: Depends: lib32asound2 but it is not going to be installed
E: Broken packages

And of course when I try to get that one on there it fails too:

sudo apt-get install lib32asound2

The following packages have unmet dependencies:
  lib32asound2: Depends: libasound2 (= 1.0.15-3ubuntu4) but 1.0.16-2 is to be installed
E: Broken packages

And libasound2 is already installed,  yet it says I don't have it. What the heck??

I'm not sure what I screwed up with. How do I fix this? Any help is appreciated. Also to add, my Ubuntu is 64 bit.

---

### Post by Yellow Pasque on 2009-06-05
It sounds like you have mixed repositories from different versions of Ubuntu. Post the contents of your /etc/apt/sources.list

---

### Post by philinux on 2009-06-05
Use synaptic to check for Broken Packages.

Then

```
sudo updatedb
then
locate libflashplayer.so
```
Ensure all flash gone from system.

Download the 64 bit flash from adobe labs to your desktop.
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
Double click to extract libflashplayer.so

Copy it or move to to ~/.mozilla/plugins

Thats all there is to it.

---

### Post by Saruman_W on 2009-06-05
> **philinux said:**
> Use synaptic to check for Broken Packages.

Then

```
sudo updatedb
then
locate libflashplayer.so
```Ensure all flash gone from system.

Download the 64 bit flash from adobe labs to your desktop.
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
Double click to extract libflashplayer.so

Copy it or move to to ~/.mozilla/plugins

Thats all there is to it.

I tried that before, didn't work. 

Anyway, here's the contents of my sources.list:
```

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse


```

---

### Post by hyperdude111 on 2009-06-05
The adobe 64bit plugin is the bets option, the one in the ubuntu repos is VERY buggy (grey boxes). Before you use the adobe plugin make sure you remove all other traces of libflashpayer.so and nspluginwrapper.so

---

### Post by Yellow Pasque on 2009-06-05
So how did you get libasound2 1.0.16-2 installed if you're running Hardy with the official repos? Look at that package's properties in Synaptic and see where that version came from.

---

