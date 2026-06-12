---
title: "Plasma doesn't start after update 4.4 -&gt; 4.5"
date: 2010-08-11
forum: Desktop Environments
---

### Post by digulla on 2010-08-11
Hello,

I updated to KDE 4.5.0 by adding the repo with "add-apt-repository ppa:kubuntu-ppa/backports" and then upgrading with "aptitude dist-upgrade". I had to manually fix a conflict and install "kdebase-workspace-data" afterwards.

When I start kdm, I get a black screen. Only the processes kwin, knotify4 and kdeinit4 are running. When I manually start "plasma-desktop", the desktop appears.

What could be wrong?

[Update] I'm missing ksmserver and the startkde skript. In which package are they?

---

### Post by digulla on 2010-08-11
Here is the solution for my problem: The files "ksmserver" and "startkde" were missing.

Googling for "debian lucid kde package ksmserver" returned this page: [http://packages.ubuntu.com/hu/lucid/kdebase-workspace-bin](http://packages.ubuntu.com/hu/lucid/kdebase-workspace-bin)

So I ran aptitude which told me "c kdebase-workspace-bin"

Installing the package with "aptitude install kdebase-workspace-bin" solved my problem.

---

