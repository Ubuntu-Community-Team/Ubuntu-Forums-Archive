---
title: "How do I install the latest version of firefox, and get flash working ?"
date: 2011-12-13
forum: Desktop Environments
---

### Post by bobdobbs on 2011-12-13
Hi all. 

I'm using ubuntu 10.10, 64bit.

My current version of firefox is 6.02. I'd like to update it.

I downloaded and installed version 8 in an opt directory, but it wouldn't run flash videos. One of the bits of advice I got was that firefox should be installed in a normal directory in order for flash to work.

However, it looks like the repos are out of date.
If I do 'apt-get install firefox', I get 6.02

Is there a way to install the latest version of firefox and have flash running on a 64bit platform?

---

### Post by mikewhatever on 2011-12-13
The Maverick repositories should have Firefox 3.6.24, so the fact that you see 6.02 means you've probably added PPAs. Try removing them.

/opt is a normal directory, whatever that means.

---

### Post by JasonR on 2011-12-13
You might try installing the Firefox Addon "Flash Aid".  It will install the required plugins for version 8.

---

### Post by lovinglinux on 2011-12-14
See [Firefox 8 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247)

---

