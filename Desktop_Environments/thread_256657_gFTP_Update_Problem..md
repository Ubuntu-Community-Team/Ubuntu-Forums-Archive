---
title: "gFTP Update Problem."
date: 2006-09-13
forum: Desktop Environments
---

### Post by Megatog615 on 2006-09-13
I have all the Ubuntu repos enabled, and there seems to be an update to "gftp" and "gftp-text", both upgrade to the latest version of 2.0.18-14.
However, "gftp" depends on "gftp-gtk" 2.0.18-14, which is not even in the repos, thus not allowing me to install it.

I have the packages "gftp", "gftp-common", "gftp-gtk", and "gftp-text" installed. Should I remove one?

---

### Post by spockrock on 2006-09-13
I also have this problem......

---

### Post by Megatog615 on 2006-09-13
It seems one of the backports is down. Check to see if it's not just me by doing a quick apt-get update.

---

### Post by wog on 2006-09-13
The initial update thingie (the little symbol which appears in the upper right hand corner) says "sudo apt-get upgrade" will work or that I can use Synaptic with Mark All Upgrades, but the truth is, neither one works due to this deps problem:

gftp:
  Depends: gftp-gtk (=2.0.18-14ubuntu1~dapper1) but 2.0.18-11ubuntu1 is to be installed
  Depends: gftp-text (=2.0.18-14ubuntu1~dapper1) but 2.0.18-11ubuntu1 is to be installed

I have no idea how to resolve this. I'm guessing I could
```
sudo apt-get -f install gftp
```
and then
```
sudo apt-get -f install
```
but I have no idea whether that would actually work. Frankly it sounds like a recipe for disaster. Opinions?

---

### Post by wog on 2006-09-13
> **Megatog615 said:**
> I have all the Ubuntu repos enabled, and there seems to be an update to "gftp" and "gftp-text", both upgrade to the latest version of 2.0.18-14.
However, "gftp" depends on "gftp-gtk" 2.0.18-14, which is not even in the repos, thus not allowing me to install it.

I have the packages "gftp", "gftp-common", "gftp-gtk", and "gftp-text" installed. Should I remove one?

Actually, if you go through the big "all" list in Synaptic you will see clustered around gftp is gftp-common and gftp-gtk. 

The weird part is, even though I've marked all upgrades, gftp-common and gftp-gtk aren't marked for upgrade even though the version number on both shows a discrepancy between the old version and the newest version.

When I right-click on gftp-common the option for upgrade is greyed out, and there's an option "mark for reinstallation".

The trouble is, I'm not sure of myself enough to know I'm supposed to choose "mark for reinstallation".

Has anyone tried that option? Did it work to resolve all the deps issues?

---

### Post by mitch.c on 2006-09-13
> **wog said:**
> 
I have no idea how to resolve this. I'm guessing I could
```
sudo apt-get -f install gftp
```
and then
```
sudo apt-get -f install
```
but I have no idea whether that would actually work. Frankly it sounds like a recipe for disaster. Opinions?
Neither worked for me. After breaking gfp, I finally did:
```

sudo aptitude install gftp=2.0.18-11ubuntu1 gftp-common=2.0.18-11ubuntu1 gftp-gtk=2.0.18-11ubuntu1 gftp-text=2.0.18-11ubuntu1
sudo aptitude hold gftp gftp-text
```

---

### Post by wog on 2006-09-13
This is looking more and more like someone didn't make two of the gftp packages available for upgrade, although to upgrade you need all four packages.

According to the Debian repos, 2.0.18-5 is the stable version, and 2.0.18-15 is the version being tested right now. This assumes our version numbers have anything to do with the Debian version numbers, of course. :)

---

### Post by justinjstark on 2006-09-13
I too have this problem.  Definitely just a dependency problem and yes, one of the backport repositories is down for me also.  I will look into this more when I get back home tonight if it isn't fixed by then.

---

### Post by Megatog615 on 2006-09-13
The issue seems to have gone away, since the backport repository has come back up. Anyone still having this problem, doing an apt-get update will fix the problem for you.

---

