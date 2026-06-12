---
title: "Package Index Broken?!?"
date: 2006-06-12
forum: Desktop Environments
---

### Post by codypumper on 2006-06-12
The update (package) manager had the little icon for new updates, I clicked on it and  said the package index was program. I seriously need help!

---

### Post by codypumper on 2006-06-12
Never mind, I just replaced my sources list!

---

### Post by HeavyAl on 2006-06-12
well, first check to see if you have an actual package list somewhere like this:

open a terminal, then:

$ cd /etc/apt
$ ls

look for anything labeled sources.xxxxx

preferably you want something that says sources.list, but I'm thinking it likely got futzed somehow so look for one that has a 'backup' in its name.

If you dont have sources.list then copy one of your recent backup lists to a new sources.list by doing this:

$sudo cp sources.list_backup_2006xxxxxxxx sources.list

where xxxxxxxxx is the date of the most recent backup.

the do:

$ sudo apt-get update

that should fix it.

---

### Post by codypumper on 2006-06-12
THanks for the support, that is pretty much what I did.

---

