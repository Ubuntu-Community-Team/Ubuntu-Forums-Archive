---
title: "Where to put scanner files?"
date: 2009-01-17
forum: General Help
---

### Post by Indyviews on 2009-01-17
I have come across yet more files that hopefully will help in getting my scanner. The following post was made in a thread under x86 64-bit users but is not being seen by many people:

Hello, I have the same problem...I have download the DFSG non-free iscan-plugin-gt-9400 onto desktop and have extracted the files (also in a folder on desktop) and have also placed them in: filesystem.usr.lib.

When I use sudo alien -d iscan-plugin-gt-9400-1.0.0-1.c2.i386.rpm in Terminal...I get:File "iscan-plugin-gt-9400-1.0.0-1.c2.i386.rpm" not found. I believe I am close to getting my scanner to work and this may be the one item I need.

I am a newbie at this and my question is: Where do I put these files so they may be found?

I am on Ubuntu 8.10, use a 32bit system, have an Ebson Perfection 3170 scanner, and have Alien installed. Can someone help me?

***A link to this thread if needed is: [http://ubuntuforums.org/showthread.php?p=6565053#post6565053](http://ubuntuforums.org/showthread.php?p=6565053#post6565053)  Thanks for any help.

---

### Post by taurus on 2009-01-17
If you saved it to your desktop, then you need to change to that directory first before you can run it unless you include the path to it.

```
cd ~/Desktop
sudo alien -d iscan-plugin-gt-9400-1.0.0-1.c2.i386.rpm
```

---

### Post by Indyviews on 2009-01-17
Thanks taurus, while it did something or at least tried to, at least it was someting other than...couldn't find the files.

Below is what I got:

Warning: Skipping conversion of scripts in package iscan-plugin-gt-9400: postrm
Warning: Use the --scripts parameter to include the scripts.
iscan-plugin-gt-9400_1.0.0-2_i386.deb generated

---

