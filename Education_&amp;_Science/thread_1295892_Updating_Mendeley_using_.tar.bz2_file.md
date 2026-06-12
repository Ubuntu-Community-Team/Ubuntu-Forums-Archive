---
title: "Updating Mendeley using .tar.bz2 file"
date: 2009-10-20
forum: Education &amp; Science
---

### Post by paulchinnz on 2009-10-20
Having one of those frustrating moments with Ubuntu. I think I'm really close to solution but at same time really far away from it! Feel my noobness. 

Installed Mendeley 0.94 couple of weeks ago via terminal and also added the relevant 3rd party software repository to package manager. Unfortunately the latter didn't update mendeley despite downloading a whole heap of files.

Anyway, decided to get the .tar.bz2 directly from the mendeley website. Now what do I do? I can get 0.94.1 running from it by running the shellscript in the bin folder, but how do I get the OS to get it installed properly i.e. update/overwrite 0.94? I can't even find the folder for 0.94 with tracker. 0.94 remains my default version because that's what I get when I run mendeleydesktop in terminal.

Thanks in advance!

---

### Post by mustaqil.ali on 2009-10-20
Hi,

Can you try running dpkg -s mendeleydesktop and paste what this outputs for you?

After running an apt-get update, and an apt-get upgrade, it should automatically upgrade the system-wide install of Mendeley Desktop for you.

Thanks.

---

### Post by paulchinnz on 2009-10-21
```
Package: mendeleydesktop
Status: install ok installed
Priority: extra
Section: science
Installed-Size: 50528
Maintainer: Fred Emmott <fred.emmott@mendeley.com>
Architecture: i386
Version: 0.9.4.1
Depends: libqt4-dbus (>= 4.5.2) | libqt4-mendeley-dbus (>= 4.5.2), libqt4-mendeley-svg (>= 4.5.2), libqt4-sql-sqlite (>= 4.5.2) | libqt4-mendeley-sql-sqlite (>= 4.5.2), libc6 (>= 2.4), libclucene0ldbl (>= 0.9.20-1), libgcc1 (>= 1:4.1.1), libqt4-mendeley-network (>= 4.5.2), libqt4-mendeley-sql (>= 4.5.2), libqt4-mendeley-xml (>= 4.5.2), libqtcore4-mendeley (>= 4.5.2), libqtgui4-mendeley (>= 4.5.2), libstdc++6 (>= 4.1.1), libx11-6
Description: Mendeley Desktop (paper management and sharing software)
 Mendeley Desktop is free academic software for managing and sharing research
 papers.
 With Mendeley Desktop, you can organise, search, and manage your documents, and
 share them with other users of Mendeley. The online features require an account
 on Mendeley Web; (http://www.mendeley.com).
Homepage: http://www.mendeley.com

```

I've run apt-get update and upgrade without anything happening - system seems to think it's all updated already.

---

### Post by mustaqil.ali on 2009-10-21
As per the terminal output you just pasted, you can see that the version being reported there is 0.9.4.1, which is correct and the latest version.

There was an error with the packages, which we're looking into fixing shortly whereby the code is the same as 0.9.4.1's, but the version number is being reported as "0.9.4". This is leading to the unnecessary auto-update message and incorrect information on the "About" dialog.

Sorry for the inconvenience. I'll post an update once the new builds are done with the correct version number.

---

### Post by paulchinnz on 2009-10-21
Thanks for the reassurance.

Anyway:
1) If I hadn't updated via terminal apt-get update etc, how would I have used the .tar.bz2 file to update? 
2) Separately, which folder is Mendeley Desktop running from?

---

### Post by mustaqil.ali on 2009-10-21
> **paulchinnz said:**
> Thanks for the reassurance.

Anyway:
1) If I hadn't updated via terminal apt-get update etc, how would I have used the .tar.bz2 file to update? 

The generic linux builds, the tarball in question, have this functionality built into them. When an update is available, they will show the changelog, and give you an option there and then to either accept or decline downloading and installing the update. When you then close and reopen the client, it will self update.

> 
2) Separately, which folder is Mendeley Desktop running from?
When you use the apt repositories, it installs to the standard system wide path, which is /usr/bin if I recall correctly.

Regarding the apt packages, we began uploading some new builds shortly before leaving the office today, so they should be ready for downloading come tomorrow. :)

---

### Post by paulchinnz on 2009-10-21
Thanks. Didn't quite understand your response to my first question but look forward to the next lot of updates.

---

### Post by mustaqil.ali on 2009-10-22
Okay, if you re-run apt-get update, and apt-get install mendeleydesktop (or apt-get upgrade) a new version of Mendeley Desktop should be installed.

This new package is 0.9.4.1-1, which is identical to 0.9.4.1 but it reports the correct version number. :)

---

### Post by skadevil on 2009-10-22
How about the repositories for Karmic Koala?

---

### Post by mustaqil.ali on 2009-10-22
> **skadevil said:**
> How about the repositories for Karmic Koala?

Well, Karmic hasn't been released yet. ;)

But these are planned to be introduced shortly after Karmic has been officially released. During the interim period of not having a Karmic specific repository, you can just use the Jaunty repo.

---

### Post by paulchinnz on 2009-12-18
Hi got a note about 0.9.5.2. Unfortunately, despite trying the October instructions above I can't get Mendeley updated from 0.9.4.1-1 in Terminal. Help!

This time dkpg confirms I've still got 0.9.4.1-1 so incorrect naming is not the issue. By the way, how do I get the Karmic repo?

---

### Post by paulchinnz on 2009-12-18
Sorted myself out partially.

[http://www.mendeley.com/download-mendeley-desktop/ubuntu](http://www.mendeley.com/download-mendeley-desktop/ubuntu)

Added the repo to my source list. I'm now stuck on 0.9.5.1. Can't seem to get it updated to 0.9.5.2 in terminal. Any ideas?

(dkpg confirms it's 0.9.5.1)

---

### Post by mustaqil.ali on 2009-12-20
Our 0.9.5.2 debian packages are currently in a state of internal testing. Once they've been deemed as passing by our QA team, we'll update the apt repo. This should be done in the early-office hours of Monday. :) (We're in London, UK)

---

### Post by paulchinnz on 2009-12-20
Thanks for that. 

Perhaps it was premature for my Mendeley, last week, to tell me that 0.9.5.2 was available for updating then?!

---

### Post by mustaqil.ali on 2009-12-20
> **paulchinnz said:**
> Thanks for that. 

Perhaps it was premature for my Mendeley, last week, to tell me that 0.9.5.2 was available for updating then?!

This is a bit of a flaw in our update announcements. The way that this currently works is that is that both our generic Linux builds and Debian/Ubuntu builds usethe same version number and check the same part of Mendeley Web for updates.

The 0.9.5.2 update is indeed available for the generic packages, but not for the .debs, this'll come shortly. I have made a note of this though, and we'll look into better distinguishing updates in a future to avoid confusion like this.

---

### Post by paulchinnz on 2009-12-20
Ah I see thanks for that.

---

