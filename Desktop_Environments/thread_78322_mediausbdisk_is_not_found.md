---
title: "media:/usbdisk is not found"
date: 2005-10-18
forum: Desktop Environments
---

### Post by mxsteini on 2005-10-18
Hi there,
When I switch on my usbdisk, konqueror opens and tells me "media:/usbdisk".
How can I tell konqueror how to mount the disk correct?
Or where is the switch to control the medias?

Greetings Michael

---

### Post by jeremy on 2005-10-18
This is a known problem, and has just been fixed, you will need to update your system:
sudo apt-update
sudo apt-upgrade

---

### Post by mxsteini on 2005-10-18
Aaaah,
I have no apt-update nor apt-apt-upgrade on my system...
kubuntu - breezy

source.list:
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) breezy main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) breezy main restricted

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) breezy-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) breezy-updates main restricted

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) breezy universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) breezy universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy multiverse


Michael

---

### Post by mxsteini on 2005-10-18
apt-update?

I have made:
apt-get update
apt-get upgrade
But all I learned is that my system is uptodate.
In which package is the bug?

Michael

---

### Post by jeremy on 2005-10-18
Sorry, my brain was going faster than my typing!
I meant
sudo apt-get update
sudo apt-get upgrade

It dl'd and installed 51 packages (about 40MB download)

My /etc/apt/sources.list is:
```
## Major bug fix updates produced after the final release of the
## distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe 

# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse 
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse
```

---

### Post by jdtanner on 2005-10-18
Does this fix address the bug at [http://bugzilla.ubuntu.com/show_bug.cgi?id=17607](http://bugzilla.ubuntu.com/show_bug.cgi?id=17607) as well?

Cheers,
JohnT

---

### Post by jeremy on 2005-10-18
I hadn't tried before, but I have just now put a commercial DVD in (The Cider House Rules, I highly recommend it!) and it mounted and opened it in Kaffeine.

---

### Post by jeremy on 2005-10-18
I have just noticed that, since the upgrade, media:/ does not show my CD's or 2nd HD (it showed them before), but they are still visible in /media

---

### Post by mxsteini on 2005-10-21
Well ...
1. thanx jeremy. After adding 
archiv.ubuntu.com and 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe 

I really found 53 pakets to download.

2. Yes media:/ doesn't show the already mounted disks, but after inserting a CD it is shown.
But a DVD (top secret with Val Kilmer) "media:/hdc not found" happend. Well and kaffeine told me the 1000 time that it couldn't play DVD.
btw. my kaffeine doesn't play anything. Does anyone konw how to replace it with mplayer?

Michael

---

### Post by Craig Prevallet on 2005-10-21
See this thread:

[http://ubuntuforums.org/showthread.php?t=79204&page=2](http://ubuntuforums.org/showthread.php?t=79204&page=2)

---

### Post by sdr_ar on 2005-11-07
To install MPlayer just add the multiverse repositories (you have to uncomment it from /etc/apt/sources.list) then write in konsole $: sudo apt-get update and the $: sudo apt-get install mplayer. That worked for me

---

### Post by sdr_ar on 2005-11-07
to install Mplayer you have to get the multiverse repositories. To do it uncoment that line in /etc/apt/sources.list
then sudo apt-get update
then sudo apt-get install mplayer

---

