---
title: "Upgrade from 5.04 to 5.10"
date: 2005-12-06
forum: Desktop Environments
---

### Post by CYHPT.net on 2005-12-06
Hi all,

Just a simple little question. 

Is there a way to upgrade from 5.04 to 5.10? I searched and looked everywhere, but cant seem to find it.

Please let me know if there is a way.

Thanks.

---

### Post by Ampersand on 2005-12-06
If you edit your /etc/apt/sources.list using the command
```
sudo gedit /etc/apt/sources.list
```
and change every mention of hoary to breezy, then 
```
sudo apt-get update
sudo apt-get dist-upgrade

```

then you'll be upgraded to Breezy.

However, this might cause a few problems, since there have been quite a few changes between versions, so if possible I'd recommend downloading the 5.10 cd a doing a clean install. If you've got your /home directory on a different partition to the / directory, you'll be able to do this without loosing any settings &c, otherwise you'd have to back up everything in your home folder.

---

### Post by Irony on 2005-12-06
See;

[https://wiki.ubuntu.com/BreezyUpgradeNotes?](https://wiki.ubuntu.com/BreezyUpgradeNotes?)

There are several ways. I just downloaded the Breezy .iso burnt it to cd, booted up Hoary then inserted the Breezy cd and applied all upgrades via synaptic - this is rather like doing the upgrades you receive regularly via the repositories.

On my laptop the cd on being inserted asked me whether I wanted to upgrade.

You can instead change your hoary references to breezy in your */etc/apt/sources.list*, this will upgrade via the repositories if you don't want to do it via cd.

This question should be in the install section.

---

### Post by CYHPT.net on 2005-12-06
Thanks heaps.

---

