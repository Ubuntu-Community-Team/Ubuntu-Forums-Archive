---
title: "Curious about 'error' when doing updates."
date: 2009-02-23
forum: General Help
---

### Post by DougieFresh4U on 2009-02-23
I have seen this 'output from terminal' during updates many times. No matter what version of Ubuntu I am using. I have seen it in Dapper, Edgy, Gutsy,etc.
Is there a way to change it, or am I missing something, or is it 'normal'?
I am just curious.

```
[B]Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'
[/B]
```

---

### Post by DougieFresh4U on 2009-02-24
Any one, please?

---

### Post by Peter09 on 2009-02-24
Can you post the contents of the file /etc/apt/sources.list

---

### Post by snova on 2009-02-24
> **DougieFresh4U said:**
> Is there a way to change it, or am I missing something, or is it 'normal'?

I've seen something like that a few times as well. I don't think you can do much about it, but it seems harmless.

Also, I found a bug on it: [https://bugs.launchpad.net/ubuntu/+bug/193325](https://bugs.launchpad.net/ubuntu/+bug/193325)

---

### Post by DougieFresh4U on 2009-02-24
> **Peter09 said:**
> Can you post the contents of the file /etc/apt/sources.list

Here you go, and this has nothing to do with using Jaunty, as I have seen it in EVERY Ubuntu version over the last 3 years!

```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Alpha i386 (20090204)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports restricted main multiverse universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
```

---

