---
title: "Having a problem installing things..."
date: 2009-01-11
forum: General Help
---

### Post by Neptunus Maris on 2009-01-11
Hi guys I'm having a problem installing things, after I did a system update.

Here I am trying to install Anjuta (C++ IDE) and get these errors, but these errors go for anything I try to install...here it is:

```
root@lulu-desktop:/home/lulu/Desktop# apt-get install anjuta
Reading package lists... Done
Building dependency tree       
Reading state information... Done
anjuta is already the newest version.
The following packages were automatically installed and are no longer required:
  libarts1c2a kdelibs4c2a libartsc0 libcvsservice0 kdelibs-data kdebase-bin-kde3 kdevelop-data liblualib50 libavahi-qt3-1 kdebase-bin libqt3-mt liblua50
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-restricted-modules-2.6.24-23-generic (2.6.24.16-23.56) ...
ld_static: final link failed: Input/output error
ld_static: final link failed: Input/output error

Setting up linux-restricted-modules-generic (2.6.24.23.25) ...
Setting up linux-generic (2.6.24.23.25) ...
```


Thanks :)
Neptune

---

### Post by Hooya on 2009-01-11
Looks like you have it installed.  Those aren't really errors, just telling you that you have things you can clean out of your system by running

$sudo apt-get autoremove

Have you tried running that program?

---

### Post by Neptunus Maris on 2009-01-11
> **Hooya said:**
> Looks like you have it installed.  Those aren't really errors, just telling you that you have things you can clean out of your system by running

$sudo apt-get autoremove

Have you tried running that program?

What do you mean what program? Anjuta?

This happens with anything I try to install though:(

---

### Post by Hooya on 2009-01-11
Yeah, the program it looked like you were trying to install is already installed according to that.

Try this for me:

sudo aptitude update && sudo aptitude upgrade && sudo aptitude autoclean

Just paste that into your terminal window.  Maybe reboot after you do that.  I noticed some linux kernel things, so I'm trying to maybe fix a farther underlying problem you may have.

---

### Post by Neptunus Maris on 2009-01-11
> **Hooya said:**
> Yeah, the program it looked like you were trying to install is already installed according to that.

Try this for me:

sudo aptitude update && sudo aptitude upgrade && sudo aptitude autoclean

Just paste that into your terminal window.  Maybe reboot after you do that.  I noticed some linux kernel things, so I'm trying to maybe fix a farther underlying problem you may have.

Ok now restarting...will be back!

---

### Post by Neptunus Maris on 2009-01-11
ok I've restarted and have installed Anjuta.

But now the system acts weird and stuff...

This error has got me puzzled:

```

ld_static: final link failed: Input/output error
ld_static: final link failed: Input/output error

```

And it makes boot time longer.

---

### Post by Hooya on 2009-01-11
That's not a happy sign.  I found only a few references to that.  Here's the only one that had any helpful results:

[http://www.backports.ubuntuforums.org/showthread.php?t=239531](http://www.backports.ubuntuforums.org/showthread.php?t=239531)

Try what's suggested there and see if that helps at all.

Should probably ask what version of Ubuntu are you using? 8.10?

---

### Post by Neptunus Maris on 2009-01-11
> **Hooya said:**
> That's not a happy sign.  I found only a few references to that.  Here's the only one that had any helpful results:

[http://www.backports.ubuntuforums.org/showthread.php?t=239531](http://www.backports.ubuntuforums.org/showthread.php?t=239531)

Try what's suggested there and see if that helps at all.

Thanks you were of great help :D

---

