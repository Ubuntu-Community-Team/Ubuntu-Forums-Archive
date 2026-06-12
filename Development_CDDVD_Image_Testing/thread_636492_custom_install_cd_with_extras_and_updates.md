---
title: "custom install cd with extras and updates"
date: 2007-12-09
forum: Development CD/DVD Image Testing
---

### Post by ruibernardo on 2007-12-09
Hi,

I want to remaster the AlternateCD, but I need some help about one thing. 

I'd like to update the packages that are on the CD with the latest packages available on the repositories. That would save the download and install time of the updates when the newly installed Ubuntu is rebooted.

I've read the [Create extras component]("https://help.ubuntu.com/community/InstallCDCustomization?action=show&redirect=InstallCDCustomizationHowTo#head-a281fb90fe726169881eb2bc5b7538bd2c797894") in the Wiki to add new packages. That would add the updates to an extra directory but, correct me if I'm wrong, it wouldn't replace the outdated packages that are on the pool directory on the CD, which would be my goal - just like [using jigdo with the daily CD builds]("https://help.ubuntu.com/community/JigdoDownloadHowto") with  the development releases, but with the actual release.

Thanks.

---

### Post by ruibernardo on 2007-12-18
Bumping this with a little more info about what I got so far and what I can't get working.

I search and found that anyone can create a debian based CD with [debian-cd]("http://wiki.debian.org/DebianCustomCD"). Also found that Ubuntu CDs are created with a modified version of debian-cd: [ubuntu-cdimage]("http://codebrowse.launchpad.net/%7Ekamion/ubuntu-cdimage/mainline/files").

I found a page that described a little more about [how to get this scripts working]("http://pqxx.org/development/suriyan/wiki/MakeACD"), but can't get it to work.

I run apt-mirror to get a mirror of the i386 and installer packages, moved it to the ftp directory, then modified the etc/anonftpsync configuration file to exclude main/universe/multiverse/restricted repos so it wouldn't slowly download all the packages from archive.ubuntu.com. It still downloaded the indices, so I should (should I?) have a mirror that would work.

When I try to run "go-project ubuntu build-image-set" I don't have any results, or maybe I don't know how this really works. It just creates a www directory with some files in it.

Can any ubuntu developer or anyone that tried ubuntu-cdimage give a hand here? Just to get a normal ubuntu CD would be good for a start.

Thanks.

---

