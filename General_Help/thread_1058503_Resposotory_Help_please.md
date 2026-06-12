---
title: "Resposotory Help please"
date: 2009-02-02
forum: General Help
---

### Post by sports fan Matt on 2009-02-02
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  Unable to find expected entry  intrepid/source/Sources in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

How can i fix this?

---

### Post by mgol on 2009-02-02
Post Your /etc/apt/sources.list file, maybe You have sth broken there.

---

### Post by tuxxy on 2009-02-02
This post may help sir

[http://ubuntuforums.org/showthread.php?t=852947](http://ubuntuforums.org/showthread.php?t=852947)

---

### Post by mgol on 2009-02-02
> **tuxxy said:**
> This post may help sir

[http://ubuntuforums.org/showthread.php?t=852947](http://ubuntuforums.org/showthread.php?t=852947)

That's it, "sox fan Matt" just have to remember to change the entries from hardy to intrepid.

---

### Post by sports fan Matt on 2009-02-02
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates intrepid restricted * [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) universe deb main multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any    * deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse

## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates multiverse * deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) intrepid



## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse #Added by software-properties


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe #Added by software-properties

---

### Post by sports fan Matt on 2009-02-03
Arent they already posted in my previous thread?

---

### Post by sports fan Matt on 2009-02-03
So all I have to do is redit my sources list (by copying and pasting what ive got in the terminal)?

---

### Post by mgol on 2009-02-03
> **sox fan Matt said:**
> So all I have to do is redit my sources list (by copying and pasting what ive got in the terminal)?

Yes. You'll have to execute:
```
sudo apt-get update
```
after editing the file to see the results.

---

### Post by sports fan Matt on 2009-02-03
I see the issue: I only have 1 entry in software sources: archive.conical.com/ubuntu intrepid partner

What are the others I need to add?

---

### Post by sports fan Matt on 2009-02-03
after adding these as well: 
Quote:
# deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) hardy main universe
##GeeXboX package repository
# deb [http://www.geexbox.org/debian/](http://www.geexbox.org/debian/) unstable main
# deb [http://ppa.launchpad.net/bortis/ubuntu](http://ppa.launchpad.net/bortis/ubuntu) hardy main
# deb-src [http://ppa.launchpad.net/bortis/ubuntu](http://ppa.launchpad.net/bortis/ubuntu) hardy main
# deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) hardy main
# deb [http://ppa.launchpad.net/deluge-team/ubuntu](http://ppa.launchpad.net/deluge-team/ubuntu) hardy main
# deb-src [http://ppa.launchpad.net/deluge-team/ubuntu](http://ppa.launchpad.net/deluge-team/ubuntu) hardy main 

I changed those to intrepid..I got this:

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FCA4A9D8F45955CEGPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 71346C8340130828GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C5E6A5ED249AD24CFailed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  Unable to find expected entry  intrepid/source/Sources in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by zvacet on 2009-02-03
gpg --keyserver hkp://subkeys.pgp.net --recv-keys  665F9AEFE1098513
gpg --export --armor 665F9AEFE1098513 | sudo apt-key add -

Do the same with other keys.

---

### Post by sports fan Matt on 2009-02-03
In the Authenication part of the sources list, where it says "import key file" I should just then import those keys?  or what should i do?

Sorry for not knowing about this!

---

### Post by mgol on 2009-02-03
Do You really need ppa repositories? If You didn't want to add anything by Yourself, just open the proper file in the terminal:
```
gksu gedit /etc/apt/sources.list
```
remove everything from there, paste this:
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse

# deb http://pl.archive.ubuntu.com/ubuntu/ intrepid-proposed main restricted multiverse universe
# deb-src http://pl.archive.ubuntu.com/ubuntu/ intrepid-proposed main restricted multiverse universe

# deb http://pl.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://pl.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse

```
save the file and then execute:
```
sudo apt get update
sudo apt-get upgrade
```
No need to bother Software Sources window etc.

---

### Post by sports fan Matt on 2009-02-05
This thread can be closed.

---

### Post by aesis05401 on 2009-02-05
Just a note that someone keyed me into recently... There is a good reason to only launch the graphical apps like GEdit with gksudo instead of sudo.

I never bothered before, but gksudo ensures that the GUI apps are run without the potential for some unexpected behavior.

---

### Post by forger on 2009-02-07
You could also try:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)
it will fix your ppa links as well as retrieve the missing keys

---

### Post by mgol on 2009-02-19
> **aesis05401 said:**
> There is a good reason to only launch the graphical apps like GEdit with gksudo instead of sudo.

You're right. Updated (sorry that so late, but I've been lacking in time recently...)

---

### Post by kaivalagi on 2009-02-21
> **forger said:**
> You could also try:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)
it will fix your ppa links as well as retrieve the missing keys

Very nice!

It's a shame I didn't come across this until I had already manually updated all the ppas in my sources :)

Oh well...

---

