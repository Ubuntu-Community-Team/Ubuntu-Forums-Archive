---
title: "Gutsy Repos turned off"
date: 2009-04-29
forum: Desktop Environments
---

### Post by mister_p_1998 on 2009-04-29
Just ran update manager yesterday, and noticed that all the Gutsy repos are off. I presumed that this was because Gutsy had had its support ended in line with Jaunty coming online. Now I only use my Gutsy laptop for copying files off my server in the loft onto my video player, and the odd bit of web browsing. I really dont need to be bang up to date, and dont want the hassle of an upgrade. I think there are archive repos of the old Gutsy files, it would be nice to still be able to apt-get install the odd program. I dont mind lack of security updates. Does anyone know the address of these archive repos?

Steve

---

### Post by ksennin on 2009-06-17
I was thinking on reinstalling gutsy on my pc as the newer versions fail to play nice with my VIA video, creating constant freezes and degraded images, but this is a bummer.

There are no archived backups anywhere?

---

### Post by Whoopie on 2009-06-17
Just replace "archive.ubuntu.com" with "old-releases.ubuntu.com" in /etc/apt/sources.list.

From [https://help.ubuntu.com/community/EOLUpgrades:](https://help.ubuntu.com/community/EOLUpgrades:)
```

sudo perl -p -i.ORIG -e 's/(?:(?:\w+.)?archive|security).(ubuntu.com)/old-releases.$1/' /etc/apt/sources.list

```

---

