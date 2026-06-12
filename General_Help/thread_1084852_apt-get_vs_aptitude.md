---
title: "apt-get vs aptitude"
date: 2009-03-02
forum: General Help
---

### Post by cybergalvez on 2009-03-02
I've been trying to find out the answer to this so I hope someone can enlighten me.  I've read that you should not switch between apt-get and aptitude, but no one has ever given the reason why, only stating that you pick one and stay with it.  What is the issue with switching, I mostly use apt-get but have found aptitude occasionally very useful.  What is the reason for "sticking" with one or the other, what are the potential issues if you switch back and forth?

---

### Post by lukjad on 2009-03-02
Quote from psychocats.net:

> Both aptitude and apt-get will install kword and its dependencies (kspread, kword-data, and libwv2-1c2), but only aptitude will actually remove the dependencies when kword is removed (and only if no other packages depend on those dependencies). 

This being said, the same article seems to indecate that the newer versions of apt-get do a good job. Still, if you were to start to install something huge with lots of dependancies that you might wish to remove at some point, I would use aptitude, just to be on the safe side.

Source:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by Rallg on 2009-03-02
The deborphan package (can be obtained via Synaptic package manager) can find unused dependencies that are missed by apt-get remove. Note that deborphan merely finds them, it doesn't remove them, and you might have to go through a repeat cycle after removing some packages.

---

### Post by cybergalvez on 2009-03-03
so if I have it right aptitude is better at dealing with dependencies, both installing and removing, but in general nothing bad is going to happen if you use one or the other

---

### Post by lukjad on 2009-03-03
That's how I understand it. Unless you are short of hard drive space, I wouldn't worry about it.

---

### Post by oldos2er on 2009-03-03
I've read that it's important to stick with either one or the other, and not mix them up; which seems sensible. I'm an aptitude fan, myself.

---

### Post by Slim Odds on 2009-03-03
> **oldos2er said:**
> I've read that it's important to stick with either one or the other, and not mix them up; which seems sensible. I'm an aptitude fan, myself.

They both call dpkg under the hood, so there should not be any issues with missing the two.

---

### Post by oldos2er on 2009-03-03
Except that aptitude handles dependencies better, especially when removing a package.

---

### Post by philinux on 2009-03-03
apt now has apt-get autoremove

Check the man pages for apt-get.

---

### Post by Slim Odds on 2009-03-03
> **oldos2er said:**
> Except that aptitude handles dependencies better, especially when removing a package.

That still does not mean that there is a problem mixing the two. That's what I was commenting on.

---

### Post by unutbu on 2009-03-03
In [http://linux.derkeiler.com/Mailing-Lists/Debian/2007-11/msg00090.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2007-11/msg00090.html), 
Daniel Burrows, author of aptitude, says "aptitude shouldn't wipe out packages installed with apt-get, period full stop."

While that may be true, here are two examples

[http://ubuntuforums.org/showthread.php?t=842399](http://ubuntuforums.org/showthread.php?t=842399)
[http://ubuntuforums.org/showthread.php?t=1014938](http://ubuntuforums.org/showthread.php?t=1014938)

which show that if you use apt-get, followed by aptitude, followed by apt-get, then apt-get may get confused and think you want to remove a ton of packages. Indeed, aptitude is not wiping out the packages, but it is causing apt-get to think a whole bunch of packages are no longer required.

A good package manager should be able to remove packages that are no longer needed. Burrows' statement implies that aptitude will not remove such packages if they had been installed by apt-get. Thus, aptitude and apt-get lack compatibility.

Given these difficulties, it seems wise to choose one package manager -- apt-get or aptitude -- and stick with it exclusively.

By the way, (as mentioned by philinux) there are a lot of old pages on the web (including psychocat's) which says that apt-get is not as good as aptitude at removing unneeded dependencies. I believe, since apt-get now has the "apt-get autoremove" command, this statement is no longer true. 

In fact, aysiu, the author of psychocat's, may himself have switched back to favoring apt-get: [http://ubuntuforums.org/showpost.php?p=1992243&postcount=169](http://ubuntuforums.org/showpost.php?p=1992243&postcount=169)

---

### Post by fragos on 2009-03-03
I have found no harm in using all of the deb installing packages. They share the same data base of installed packages. I would add to the list of apt-get, aptitude and dpkg; Synaptic and Add/Remove in the Gnome environment. I've been using deb packages for many years and to be honest Synaptic.

---

### Post by Slim Odds on 2009-03-03
> **fragos said:**
> I have found no harm in using all of the deb installing packages. They share the same data base of installed packages. I would add to the list of apt-get, aptitude and dpkg; Synaptic and Add/Remove in the Gnome environment. I've been using deb packages for many years and to be honest Synaptic.

That's exactly what I was getting at. If one of them has a bug, so be it. But they all share the same foundation.

---

