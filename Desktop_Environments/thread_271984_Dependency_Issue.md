---
title: "Dependency Issue"
date: 2006-10-05
forum: Desktop Environments
---

### Post by AT-AT on 2006-10-05
Okay so I got a deb package (specifically mplayer since Im having no luck doing it the 'complining' way) and Im manually installing dep's since my ubuntu comp is not connected to the net. I got to the point where I have to install the libggi2 dep. It requires libggi0 which requires libggi0-target-x. But libggi0-target-x requires libggi0. How am I supposed to install either of the last two when they require **each other, **it creates an infinite circle of dependence, so I cant install either package because it complains I dont have the other. Is there a way to force install, or am I out of luck?

---

### Post by DirtDawg on 2006-10-05
Boy have I been on this boat.

You need to install like this:
```
 sudo dpkg -i package1.deb package2.deb 
```
They will feed off each other that way. Stuff like Mplayer is a real pain without the Net. 

BTW, you probably know about the [Ubuntu Package website]("http://packages.ubuntu.com/dapper/"), but if you didn't, you do now! An invaluable tool to those without a readily available connection.

---

### Post by AT-AT on 2006-10-05
So I subsitute the package names for package1.deb and package2.deb? Just to make sure, I've got to put the directory they're in before the names correct? Thanks.

---

### Post by Kateikyoushi on 2006-10-05
You can cd to the directory of the debs and substitute the package names with the real ones.

---

### Post by DirtDawg on 2006-10-05
> **AT-AT said:**
> So I subsitute the package names for package1.deb and package2.deb? Just to make sure, I've got to put the directory they're in before the names correct? Thanks.
Yes that's correct. Sorry I didn't make that clear.

---

