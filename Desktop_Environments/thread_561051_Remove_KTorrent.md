---
title: "Remove KTorrent"
date: 2007-09-27
forum: Desktop Environments
---

### Post by tpg on 2007-09-27
I'm running Kubuntu Feisty, and am about to go to University. One of the regulations on computers connected to their network is that all torrent software be completely removed from the computer. 

However, kubuntu-desktop depends on ktorrent, so removing ktorrent will effectively break my system (I do not particularly want to remove kubuntu-desktop, as I think it will give me a headache when I wish to upgrade). Does anyone have any suggestions? Thanks in advance.

---

### Post by F for Fragging on 2007-09-27
It seems ridiculous to me that your university demands that you remove your Bittorrent software, instead of demanding that it simply is not used.

Simply don't use it, without removing it. Did you really expect that they are going to inspect every students PC or notebook and punish them if they have Bittorrent software installed? That's practically (and probably legally as well) impossible. Not sure what the privacy law is over where you live, but as long as they don't see any Bittorrent traffic travelling over their network to your PC, there's nothing they can do to you, right?

---

### Post by tpg on 2007-09-27
> **F for Fragging said:**
> It seems ridiculous to me that your university demands that you remove your Bittorrent software, instead of demanding that it simply is not used.

Simply don't use it, without removing it. Did you really expect that they are going to inspect every students PC or notebook and punish them if they have Bittorrent software installed? That's practically (and probably legally as well) impossible. Not sure what the privacy law is over where you live, but as long as they don't see any Bittorrent traffic travelling over their network to your PC, there's nothing they can do to you, right?

I agree that there is possibly a legal grey area, however I have little use for the software anyway, and so would still like to remove it. I do wonder why the ktorrent package is deemed important enough to be a dependency of kubuntu-desktop (I don't think ubuntu-desktop depends on any torrent software). If anybody does know how to work around this, I would be most grateful.

---

### Post by Incursis on 2007-09-27
I have removed KTorrent using either Adept or apt-get and I did see the kubuntu-desktop dependency. I took a chance and removed KTorrent anyway and my system is still running with no problems at all.

---

### Post by F for Fragging on 2007-09-27
KTorrent probably is a dependency because that's the only application which can be used to download torrents on Kubuntu out of the box AFAIK. Because the *buntu family of distro's itself is distributed through Bittorrent and considering the popularity of Bittorrent downloads nowadays, it makes sense that developers see a Bittorrent package as essential. Ubuntu also included Bittorrent in ubuntu-desktop, but as of Gutsy it seems only a command line application is included, without a GUI.

kubuntu-desktop is just a meta package which exists for quickly installing an entire Kubuntu desktop system through APT and for doing distribution upgrades AFAIK. If you remove KTorrent you will have to remove kubuntu-desktop as well. However, as soon as you wish to download a distribution upgrade, you can choose to download kubuntu-desktop again, which also downloads KTorrent again. After the update you can then remove them again. It's an inconvenient workaround, but it should work if you only do a distribution upgrade every six months. Best would probably be to just leave KTorrent be even if you don't use it, that way the problem won't bother you.

---

### Post by kugn on 2007-09-27
I think kubuntu-desktop is a meta package that pulls all the default KDE apps to form the kubuntu OS. this should be why it is a dependency. As for removing ktorrent, i'd agree with Incursis that there shouldn't be any problem. but you must be careful NOT to run sudo apt-get auto-remove, which might remove every other app that kubuntu-desktop brings

---

### Post by tpg on 2007-09-27
> **kugn said:**
> I think kubuntu-desktop is a meta package that pulls all the default KDE apps to form the kubuntu OS. this should be why it is a dependency. As for removing ktorrent, i'd agree with Incursis that there shouldn't be any problem. but you must be careful NOT to run sudo apt-get auto-remove, which might remove every other app that kubuntu-desktop brings
Which is one reason why I don't want to remove kubuntu-desktop - apt-get autoremove is very useful when installing/uninstalling software, and then removing unnecessary libraries etc. Is there any way of forcing apt to ignore this particular dependency?

---

### Post by Incursis on 2007-09-27
I removed KTorrent and ran autoremove autoclean and clean many times and nothing has gone wrong.

---

### Post by pbcartwright on 2007-09-27
you could always rename /usr/bin/ktorrent to /usr/bin/ktorrent.bad or something else..

---

### Post by maybeway36 on 2007-09-27
Set all the other kubuntu-desktop apps as manually installed, I suppose.

---

### Post by tpg on 2007-09-29
Solved by upgrading to gutsy beta - subsequent attempt to remove ktorrent does not try and remove kubuntu-desktop.

---

