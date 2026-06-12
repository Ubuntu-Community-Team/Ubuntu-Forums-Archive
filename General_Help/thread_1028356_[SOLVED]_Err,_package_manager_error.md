---
title: "[SOLVED] Err, package manager error?"
date: 2009-01-02
forum: General Help
---

### Post by Xafira on 2009-01-02
Hey guys, I've been getting a error message when I log onto my system, I don't have any experience with this sort of thing in Linux, so I hope that some of you might be able to help. and please note that I'm a noob with this sytem.

This is what the error message is saying:
[[IMG]http://img147.imageshack.us/img147/804/help1mk7.png[/IMG]](http://imageshack.us)

When I try to open the package manager I get this error:
[[IMG]http://img508.imageshack.us/img508/9341/help2qp4.png[/IMG]](http://imageshack.us)

And when I type in apt-get in the terminal this comes up, and I get a list of available commands and options. But I think those are unnecessary to show: 
```
apt 0.7.14ubuntu6 for amd64 compiled on Aug 14 2008 16:55:52
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

```

I hope that you guys can give me a helping hand on this, and sorry for the big screenshots, I was in a hurry.

---

### Post by taurus on 2009-01-02
There is something wrong with line 48 in your /etc/apt/sources.list.  Did you try to add something in there?

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Xafira on 2009-01-02
Bump and to the poster above, all I got when I typed that was

```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080701)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://no.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://no.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://no.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://no.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://no.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://no.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://no.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://no.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://no.archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://no.archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://no.archive.ubuntu.com/ubuntu/ intrepid-security multiverse

sudo apt-get update


sudo apt-get update

```

:/, and as I previously stated; I'm a noob when it comes to this :(

---

### Post by taurus on 2009-01-02
> **Xafira said:**
> Bump.

Have you even looked at my previous post?

If you are not sure what to edit, just post your /etc/apt/sources.list then.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by notquiterite on 2009-01-02
if i'm not mistaken you're going to want to remove the two lines that say 

```
sudo apt-get update
```

EDIT: I'm guessing you probably followed directions at some point to add additional repos to sources.list and when you did you accidently skipped a step.  Instead of saving and closing sources.list and then running ```
sudo apt-get update
``` you saved it into the file, therefore causing the error.  ^_^

---

### Post by Xafira on 2009-01-02
Using the command given by taurus and the instructions by notquiterite I was able to fix the problem as my package manager seems to be fully operational again.

And:

> 
Have you even looked at my previous post?


No I didn't see it before after I bumped my post, as it was on page 3(iirc), I assumed nobody had responded, my apologies:(

And thanks again you two:)

---

