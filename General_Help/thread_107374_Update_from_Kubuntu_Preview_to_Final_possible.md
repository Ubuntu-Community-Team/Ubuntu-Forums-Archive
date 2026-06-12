---
title: "Update from Kubuntu Preview to Final possible?"
date: 2005-12-22
forum: General Help
---

### Post by jodef on 2005-12-22
I have a preview release of Kubuntu Breezy would it be possible to upgrade to the final release?

If this is possible about what size of updates am I looking at?

---

### Post by asimon on 2005-12-23
See [Kubuntu Wiki: Breezy Upgrade](http://wiki.kubuntu.org/BreezyUpgrade) for instructions.

Just make sure that your sources.list is setup and points too breezy. Then opening a terminal and running 'sudo apt-get update' followed by 'sudo apt-get dist-upgrade' should be enough.

I don't know how big the updates are but before upgrading apt-get will tell you how much it needs to download. Synaptic will probably tell you that too, but I don't use synaptics and can tell for sure.

---

### Post by infoseeker on 2005-12-26
Upgraded to KDE 3.5 last night...took close to 100MB of d/l's to do and I am impressed with it!

Did :
> kdesu kwrite /etc/apt/sources.list
and added:
> deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main
and then:
> sudo apt-get update
sudo apt-get dist-upgrade
A reboot was then necessary.

---

