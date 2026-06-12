---
title: "Duplicate sources error and update notifier error"
date: 2009-04-09
forum: General Help
---

### Post by sadicote on 2009-04-09
I just did an update and got this. Haven't the faintest. Any suggestions, please?
Fetched 19.2MB in 23min 47s (13.4kB/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages (/var/lib/apt/lists/ppa.launchpad.net_thefirstm_ppa_ubuntu_dists_jaunty_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
sade@sade-desktop:~$ ** (update-notifier:27176): DEBUG: /usr/lib/update-notifier/apt-check returned 114 (security: 0)

got it: gksudo gedit /etc/apt/sources.list and comment all duplicate sources, 
        sudo apt-get clean and later sudo apt-get update

---

