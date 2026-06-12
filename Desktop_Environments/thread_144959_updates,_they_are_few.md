---
title: "updates, they are few"
date: 2006-03-15
forum: Desktop Environments
---

### Post by Azrael on 2006-03-15
Maybe a silly question, but I have been using Breezy since November and everytime I do a "sudo apt-get update" I notice that I only ever get updates from breezy-security and never (or almost never?) any 'ordinary' breezy main/restricted/universe/multiverse updates, even though I have "apt-get install"ed a lot of progams (and my /etc/apt/sources.list contains the neccessary line: deb [ftp://nl.archive.ubuntu.com/ubuntu/]("ftp://nl.archive.ubuntu.com/ubuntu/") breezy main restricted universe multiverse).

Everyone else notice this? How actively are the Ubuntu repositories maintained (apart from the bi-anual distro upgrade changes)? Not so much I guess...:???:

Just wondering. I'm enjoying Ubuntu nonetheless.

---

### Post by Xian on 2006-03-15
[QUOTE=Azrael]Everyone else notice this? How actively are the Ubuntu repositories maintained (apart from the bi-anual distro upgrade changes)? Not so much I guess...:???:[/QUOTE]

You generally will not get officially supported version upgrades between major Ubuntu releases for installed packages unless they are security related. This is as planned and is normal with any distribution that supports particular stable builds.

---

### Post by engla on 2006-03-15
A very weak remedy for this is Ubuntu Backports
More info at their forum section: [http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47)

Basically some, selected "easy" upgrades are backported and included in breezy.

You can also add completely 3rd-party repositories if you want, but that can be unreliable. Backports make an effort to 1. test their upgrades against breezy and 2. as I said, only make "easy"/safe upgrades

---

### Post by Azrael on 2006-03-15
Thanks guys. I guess infrequent updates are necessary sacrifices to keep things stable...

I think a 6 month cycle is OK with me if I'll be able to smoothly upgrade to next releases (which would be somewhat in contrary to previous releases). If upgrading to Dapper will break a lot, then I'll probably decide I'm better off with Debian Sid.

I'll also have a look at what backports can do for me.

---

