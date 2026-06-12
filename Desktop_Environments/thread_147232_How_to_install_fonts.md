---
title: "How to install fonts"
date: 2006-03-19
forum: Desktop Environments
---

### Post by dpack on 2006-03-19
I have gone to this wiki article: [https://wiki.ubuntu.com/FontInstallHowto](https://wiki.ubuntu.com/FontInstallHowto)

When I search the SPM (yes, I have Universe and Multiverse repositories enabled) for the **msttcorefonts** package, my only result is a mention of it listed under OpenOffice asking if you wish to enhance OOo to install it. Ha!

So then I tried **sudo apt-get install msttcorefonts**
But these were my results:
Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate

Anyone know how I can install msttcorefonts? What it installs are all the fonts I need.

---

### Post by tuxcantfly on 2006-03-19
you need to add additional repositories

sudo nano /etc/apt/sources.list

add this lines:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

then:

sudo apt-get update

sudo apt-get install msttcorefonts

---

### Post by dpack on 2006-03-19
This is the first time I've used nano. I can insert the specified line and I see to exit you do a ^X. But when I do that it just literally types the ^X into the window. How do I get out of that window saving the inserted line?

Also, I noticed you have dapper listed in that line. I'm running Breezy 5.10 if it makes a difference.

---

### Post by dpack on 2006-03-19
Nevermind my last post. I figured it out. I played with my keyboard and found the Ctrl key needs to be used for the ^ function. I got it saved and got my fonts installed. Thanks!

---

