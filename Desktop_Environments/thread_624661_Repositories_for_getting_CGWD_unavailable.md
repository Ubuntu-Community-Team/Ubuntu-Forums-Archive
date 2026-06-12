---
title: "Repositories for getting CGWD unavailable"
date: 2007-11-27
forum: Desktop Environments
---

### Post by zanzer7 on 2007-11-27
I have been trying for some time to get Compiz working on Xubuntu 7.10, but I'm stuck at a seemingly dead end now: getting hold of **CGWD**.

I know I have to use third-party repositories, but all I could find that have (had?) CGWD are either down, or have removed CGWD.

I've had no luck with these repositories (of course, I've added the authentication keys, and I'm positive the repositories - the ones that are online, anyways - work well):

[list][*]**deb [http://cle.linux.org.tw/candyz/Ubuntu/edgy](http://cle.linux.org.tw/candyz/Ubuntu/edgy) i386/**
*does not have CGWD in repository*
[*]**deb [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper eyecandy**
*404: file not found*
[*]**deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main**
*site is blocked (even in firefox)*
[*]**deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main**
*apparently bought by domain name provider*
[*]**deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main**
*no longer blutkind.org*[/list]

I've tried googling for repositories containing CGWD (I can easily get hold of cgwd-themes and cgwd-themes-extras), but without luck.

If anyone has a working repository for getting cgwd, I'd be very grateful. Thanks in advance!

---

As a side node, if anyone feels up for it, I'd like to know why to stick with compiz **or** why to switch to beryl, as I don't know a lot about the two.

---

### Post by taurus on 2007-11-27
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by zanzer7 on 2007-11-27
Of course. I would've before, but I'm somewhat confident that's not where the problem lies. Anyhow, here goes;

```

**$ cat /etc/apt/sources.list**

# 

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://dk.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://dk.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse

deb http://cle.linux.org.tw/candyz/Ubuntu/dapper i386/
deb http://ubuntu.moshen.de dapper eyecandy
deb http://xgl.compiz.info/ dapper main
deb http://ubuntu.compiz.net/ dapper main
deb http://media.blutkind.org/xgl/ dapper main
```

---

### Post by taurus on 2007-11-27
I knew you would add those lines in there.  It's not a good idea to mix repos in /etc/apt/sources.list because bad things can happen and will happen.

You mean you don't have compiz (or even compiz.real) on your machine?

---

### Post by zanzer7 on 2007-11-27
I've been unclear: I have installed the entire compiz metapackage, as well as $xserver/xgl. Both seem to work 'somewhat' well, but as soon as I start compiz, I no longer have window decorations, and thus I am not able to move windows around (go figure).

I thought cgwd might help that, as it's discussed in quite a few threads involving xubuntu and compiz, but as it seems, I just can't get hold of cgwd.

This is my compiz output:

```
**$ compiz**

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format



**$ compiz.real --replace**

compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz.real (core) - Error: Failed to manage screen: 0
compiz.real (core) - Fatal: No manageable screens found on display :1.0
[compiz.real terminates] $
```

---

