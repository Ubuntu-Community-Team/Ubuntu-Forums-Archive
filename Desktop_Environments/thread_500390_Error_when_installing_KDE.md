---
title: "Error when installing KDE"
date: 2007-07-13
forum: Desktop Environments
---

### Post by denny14 on 2007-07-13
Hi.
1) I downloaded the separate files for KDE rather than installing it straight from the internet. I went to [www.kde.org/download](www.kde.org/download) and downloaded about 19 files from that site. I've extracted the .tar.bz2 files and now I'm up to the ./configure stage. When I go ./configure, it comes up with an error after about 1 minute of configuring it. The error says: 
checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!
What on earth does that mean???
2) Once I do the ./configure stage, I have to type 'make' in the Terminal. Do I type make for each separate package or do I do them all at once?
3) Do I need to use Konstruct or not?
Thanks :)

---

### Post by Happy_Man on 2007-07-13
> **denny14 said:**
> Hi.
1) I downloaded the separate files for KDE rather than installing it straight from the internet. I went to [www.kde.org/download](www.kde.org/download) and downloaded about 19 files from that site. I've extracted the .tar.bz2 files and now I'm up to the ./configure stage. When I go ./configure, it comes up with an error after about 1 minute of configuring it. The error says: 
checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!
What on earth does that mean???
2) Once I do the ./configure stage, I have to type 'make' in the Terminal. Do I type make for each separate package or do I do them all at once?
3) Do I need to use Konstruct or not?
Thanks :)
Are you using a commandline install of ubuntu? If so, you will need to install X11 before trying to compile KDE. If not, it would be *far* easier to install the 'kde-core' package, which is basically like those packages you're trying to install right now, only easier and quicker to install. Hope this helps!

---

