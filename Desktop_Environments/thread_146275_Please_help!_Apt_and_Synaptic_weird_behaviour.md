---
title: "Please help! Apt and Synaptic weird behaviour"
date: 2006-03-18
forum: Desktop Environments
---

### Post by tfwo on 2006-03-18
Hi folks! Since I've installed breezy several months ago, I'm getting a strange  problem with synaptic (most likely caused by apt):

Sometimes (but not always) upon loading Synaptic brings a dialog box with messages like this:

====================
...
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
...
====================

I think it clears all the downloaded package lists for universe, multiverse, etc., leaving only the Ubuntu CD in the package cache. All internet packages are then listed in local/obsolete, etc...

After that, I only can perform an "apt-get update" (from Synaptic) to get lists of packages again which is rather annoying (universe cache is more than 2MB, and I'm on a dial-up) :(

What could force apt to clear it's package caches?

Also, sometimes when I run Synaptic, I have new ubuntu-updates in the "available updates" list. Which means, apt somehow "apt-get-updated" itself without notifying me! How's that? Could this be the reason for the problem above??

By the way, I only do apt-get-update from Synaptic, and I've disabled the gnome "available updates" tray icon immediately after installing.

Thank you for your help. --tfwo

---

### Post by Blairboy on 2006-03-18
what's your sources.list look like?

---

### Post by tfwo on 2006-03-19
It is not in the sources.list!!! The problem description is here:

[https://launchpad.net/distros/ubuntu/+source/apt/+bug/30215](https://launchpad.net/distros/ubuntu/+source/apt/+bug/30215)

If I don't connect to the internet early on startup, I get my package caches removed!

---

