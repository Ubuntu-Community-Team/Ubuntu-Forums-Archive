---
title: "gpg error ppa.launchpad.net intrepid Release"
date: 2009-01-26
forum: General Help
---

### Post by travnewmatic on 2009-01-26
```
Fetched 310B in 1s (160B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 778978B00F7992B0
W: You may want to run apt-get update to correct these problems

```

i've been getting this for a while now and i'm not sure why...

here is my sources.list
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Beta i386 (20081001)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb http://ppa.launchpad.net/project-neon/ubuntu intrepid main
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
# deb http://deb.opera.com/opera/ stable non-free
deb http://archive.canonical.com/ intrepid partner
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
```

please let me know what else you need!  :D

---

### Post by tknarf on 2009-01-26
translation.... What dose this say????

---

### Post by travnewmatic on 2009-01-26
well its saying that some security key is missing for that repository.  at least thats what i think it says.

---

### Post by tknarf on 2009-01-26
I am getting computer programing mumbo jubmbo..... I don't know what 
"Re:gpg error ppa.launchpad.net intrepid Release" means....

---

### Post by tknarf on 2009-01-26
security key.....Like a computer part...or programing?????

---

### Post by travnewmatic on 2009-01-26
Check this out:
[How apt uses Release.gpg]("http://wiki.debian.org/SecureApt#head-9ff8bb2eb2ef11ca6cbd8f35caf1464f553655ec")

---

### Post by travnewmatic on 2009-01-27
bump

---

### Post by travnewmatic on 2009-01-27
solved, thanks guys :D

---

### Post by cmacdonell on 2009-01-28
How did you fix it?  I have the same problem.

---

### Post by stillious on 2009-01-28
Check my thread here ```
http://ubuntuforums.org/showthread.php?t=1053126
``` for a solution :)

---

### Post by ledenjes on 2009-01-31
What you need to do, is the following:

Open gnome-terminal and enter the following:

gpg --keyserver subkeys.pgp.net --recv *C71839136CF5CE97*
*(replace "C71839136CF5CE97" by the code in your error message)*

Then enter the following:

gpg --export --armor *C71839136CF5CE97* | sudo apt-key add -
*(here again, replace "C71839136CF5CE97" by the code in your error message)*

Then, to finish off, enter the following:

sudo apt-get update

---

### Post by blackgr on 2009-01-31
or just download the script and execute it :)
[http://ubuntuforums.org/showthread.php?t=1047743&page=5](http://ubuntuforums.org/showthread.php?t=1047743&page=5)
it will update all your launchpad entries

---

### Post by forger on 2009-02-06
I made one too, fixes the ppa links as well:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

