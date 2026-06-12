---
title: "[SOLVED] Bunch of errors when checking for updates"
date: 2009-01-05
forum: General Help
---

### Post by Haluci on 2009-01-05
When I go to Update Manager and click Check, a windows pops up with all this:

```
W: GPG error: http://archive.canonical.com intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://wine.budgetdedicated.com intrepid Release: The following signatures were invalid: BADSIG 58403026387EE263 Scott Ritchie <scott@open-vote.org>

W: GPG error: http://security.ubuntu.com intrepid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://packages.medibuntu.org intrepid Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>
W: GPG error: http://us.archive.ubuntu.com intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://us.archive.ubuntu.com intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://us.archive.ubuntu.com intrepid-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/intrepid/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

Does anybody know what this is, or how to fix it?  I'm completely lost.

Thanks! :)

---

### Post by Haluci on 2009-01-05
bumping.

Is there anything wrong that I'm doing with asking questions?  I've had zero luck getting any help for the past 6 months.

---

### Post by 2hot6ft2 on 2009-01-05
Open a terminal
Applications>Accessories>Terminal
```
sudo apt-get update
```
Hit Enter
Then your password and Enter (your password will not be displayed)

---

### Post by 2hot6ft2 on 2009-01-05
> **Haluci said:**
> bumping.

Is there anything wrong that I'm doing with asking questions?  I've had zero luck getting any help for the past 6 months.
No there's nothing wrong with what you're doing or with what you're asking. Never seen all the signatures be invalid before but I'm sure it can be fixed if I have to boot up the laptop to look at mine.

The laptop is running intrepid I'm on the desktop running Hardy right now.

---

### Post by Haluci on 2009-01-06
> **2hot6ft2 said:**
> Open a terminal
Applications>Accessories>Terminal
```
sudo apt-get update
```
Hit Enter
Then your password and Enter (your password will not be displayed)

Thanks for the help!

Running sudo apt-get update gives me what looks like the same errors:

```
W: GPG error: http://archive.canonical.com intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://wine.budgetdedicated.com intrepid Release: The following signatures were invalid: BADSIG 58403026387EE263 Scott Ritchie <scott@open-vote.org>
W: GPG error: http://security.ubuntu.com intrepid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://packages.medibuntu.org intrepid Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>
W: GPG error: http://us.archive.ubuntu.com intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://us.archive.ubuntu.com intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://us.archive.ubuntu.com intrepid-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
```

From what I've heard about GPG, it seems like I have corrupted public keys somehow.  Would downloading and reinstall them help, and if so, where can I get them and how do I reinstall them?

---

### Post by Haluci on 2009-01-07
bumping, again...

---

### Post by Haluci on 2009-01-08
bumping.

Is there a bump limit?  I don't want to get banned or anything.

---

### Post by plucky on 2009-01-08
**System > Administration > Software Sources** and try a different server.Then either reload or from a terminal window ```
sudo apt-get update
```

Also under Software Sources > Authentication  you can **Restore Defaults**. What does that do for you? Take a screenshot and post to the forums.

If that doesn't work then post your sources.list ```
cat /etc/apt/sources.list
```


Good Luck

---

### Post by Haluci on 2009-01-08
> **plucky said:**
> **System > Administration > Software Sources** and try a different server.Then either reload or from a terminal window ```
sudo apt-get update
```

I did that, and just used the "Choose Best Server" tool to get a different server (ubuntu.cs.utah.edu).  Running sudo apt-get update this time gives less errors:

```
W: GPG error: http://archive.canonical.com intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://wine.budgetdedicated.com intrepid Release: The following signatures were invalid: BADSIG 58403026387EE263 Scott Ritchie <scott@open-vote.org>
W: You may want to run apt-get update to correct these problems
```

I'm getting somewhere. :D

> **plucky said:**
> Also under Software Sources > Authentication  you can **Restore Defaults**. What does that do for you? Take a screenshot and post to the forums.

I clicked that button and it didn't appear to do anything.  Running sudo apt-get update again gives the same errors as above.

> **plucky said:**
> If that doesn't work then post your sources.list ```
cat /etc/apt/sources.list
```

Here it is:

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.cs.utah.edu/ubuntu/ intrepid main restricted
deb-src http://ubuntu.cs.utah.edu/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.cs.utah.edu/ubuntu/ intrepid-updates main restricted
deb-src http://ubuntu.cs.utah.edu/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.cs.utah.edu/ubuntu/ intrepid universe
deb-src http://ubuntu.cs.utah.edu/ubuntu/ intrepid universe
deb http://ubuntu.cs.utah.edu/ubuntu/ intrepid-updates universe
deb-src http://ubuntu.cs.utah.edu/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.cs.utah.edu/ubuntu/ intrepid multiverse
deb-src http://ubuntu.cs.utah.edu/ubuntu/ intrepid multiverse
deb http://ubuntu.cs.utah.edu/ubuntu/ intrepid-updates multiverse
deb-src http://ubuntu.cs.utah.edu/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ubuntu.cs.utah.edu/ubuntu/ intrepid-backports main restricted universe multiverse
deb-src http://ubuntu.cs.utah.edu/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://ubuntu.cs.utah.edu/ubuntu/ intrepid-security main restricted
deb-src http://ubuntu.cs.utah.edu/ubuntu/ intrepid-security main restricted
deb http://ubuntu.cs.utah.edu/ubuntu/ intrepid-security universe
deb-src http://ubuntu.cs.utah.edu/ubuntu/ intrepid-security universe
deb http://ubuntu.cs.utah.edu/ubuntu/ intrepid-security multiverse
deb-src http://ubuntu.cs.utah.edu/ubuntu/ intrepid-security multiverse
deb http://wine.budgetdedicated.com/apt intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

Thanks for the help! :)

---

### Post by Haluci on 2009-01-10
bumping, again

---

### Post by mgol on 2009-01-10
Try to remove invalid information first. Do the following:
```

sudo rm /var/lib/apt/lists/partial/*
sudo rm /var/lib/apt/lists/*
sudo apt-get update

```

There will be some (at list one, for 'partial' directory) warnigs saying that rm command cannot remove something because it's a directory - don't worry, it's normal.

Are these apt-get update errors still appearing?

---

### Post by namdung on 2009-01-10
Change the Software Sources to Main Server.

Comment out the line with wine and canonical (and any line with issues)
[I][http://archive.canonical.com](http://archive.canonical.com) intrepid
[http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid[/I]

Post output of
```
sudo apt-get update
cat /etc/apt/sources.list
```

---

### Post by Haluci on 2009-01-13
> **mgol said:**
> Try to remove invalid information first. Do the following:
```

sudo rm /var/lib/apt/lists/partial/*
sudo rm /var/lib/apt/lists/*
sudo apt-get update

```

There will be some (at list one, for 'partial' directory) warnigs saying that rm command cannot remove something because it's a directory - don't worry, it's normal.

Are these apt-get update errors still appearing?

Nope.  That fixed it.  Thanks! :D

---

### Post by Kamilion on 2009-01-14
Had the same problem myself, but I located the source:

My company runs a squid caching proxy in transparent mode that we all have to go through to get out to the internet.

Something about it was causing problem with verifying the keys.

Added ubuntu.com and ubuntu.org to the "Do not cache these domains (one per line)" in Endian's config, and the errors went away.

Synopsis: Don't cache apt indexes, only .deb packages.

I've yet to delve into squid's config files as we use Endian Firewall community edition, but I bet it's possible to blacklist caching only the index paths while still caching the package paths.
(Only cache ubuntu/pool/* )

---

### Post by chilker on 2009-01-21
Hey, man!
Thanks for this! I was having the same problem you had, and changing my server to the one it deemed the best one (also the one in Utah, coincidentally) worked for me! Thanks! I hope you can get the last few errors squared away, and I'm sorry I'm not much help...
-chilker

---

