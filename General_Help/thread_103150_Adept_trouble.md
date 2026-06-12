---
title: "Adept trouble"
date: 2005-12-13
forum: General Help
---

### Post by freedom on 2005-12-13
I have a really hard time with this Adept thing.
Every day or two I get like there is no package available from repositories, just the ones from CDs. Even if I have internet connection when starting Adept he won't fetch updates so I need to manually start it and every time it's like I've started it for the first time... Adept take the package infos from repositories and that is few Megabyte of data instead of just update existing (previous) data on HDD.

Is this normal or I need to setup something... or just stick with terminal and apt-get? :confused:

---

### Post by My8os on 2005-12-13
[QUOTE=freedom]...
I've started it for the first time... Adept take the package infos from repositories and that is few Megabyte of data instead of just update existing (previous) data on HDD.
...[/QUOTE]

Dont worry...this is how it works.
Every time that you run a "Fetch Updates" it hits all the repositiries in the */etc/apt/sources.list* from the start and when its done you'll see in the bottom-bar of the program if there are any upgradable programs for you to download.
Then you choose a "Full upgrade" and a "Commit Changes" and you are set to go ;) .

---

### Post by freedom on 2005-12-14
I know that and that is not a problem. Problem is that Adept is always fetching complete packages info instead of update existing. :rolleyes:

---

