---
title: "Kubuntu jaunty plasmoid-network-manager can't connect mobile broadband"
date: 2009-04-27
forum: Desktop Environments
---

### Post by earthtoclinton on 2009-04-27
Hi all,

Have recently installed Jaunty, after the final version was released a couple of days back. I'm an Xfce user primarily, but was tempted to give KDE a try, as the latest version looked pretty good. On first impressions it's great - just one major problem for me, mobile broadband. I have this as my home connection.Since Intrepid it's been a breeze in Xubuntu (and in gnome for that matter), but Kubuntu's plasmoid network manager just won't get it hooked up. I came across this bug report :

[https://bugs.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/334122]("https://bugs.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/334122")

Looks like it's a problem others are having too, and it's still there in the final release. Has anyone heard anything about when it might be fixed? Or for the meantime - how do you access gnome's network manager from within KDE? (That works just fine).

Thanks in advance!

---

### Post by earthtoclinton on 2009-04-30
A few days later and I've still had no luck - I guess a future update might fix this..anyone else have this problem? At the very least I'd like to be able to use the xfce/gnome network manager in kde to connect my mobile broadband stick, but after some searching i still can't figure out how to :( any help would be much appreciated!

---

### Post by Zorael on 2009-04-30
There's an updated package over at the kubuntu-experimentals ppa ([https://launchpad.net/~kubuntu-experimental/+archive/ppa);](https://launchpad.net/~kubuntu-experimental/+archive/ppa);) perhaps you'll have better luck with that one.
```
plasma-widget-network-manager (0.0+svn959985-0ubuntu1~ppa3) jaunty; urgency=low

  * New PPA svn snapshot
  * Manual update of kubuntu_01_place_kcm_in_network_kcm.diff
  * Add -dbg package

 -- Andreas Wenning <email address hidden>   Wed, 29 Apr 2009 18:40:45 +0200
```
As for how to run GNOME's network manager, no idea. Perhaps from a command line? gnome-network-manager?

Another alternative is to use the old KNetworkManager, I guess.

---

### Post by peterroots on 2009-06-24
rather late I know but if you are still interested you can run nm-applet from the command line or from the kde menu.  It works fine but does not start up automatically like the kde version or the plasmoid.
Alternatively you can connect with kppp which also works fine and has the advantage of logging how much traffic passes which it remembers from one day to the next so you don't overstep your limit.

---

