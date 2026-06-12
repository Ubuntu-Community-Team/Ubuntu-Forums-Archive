---
title: "How do I get rid of IBUS"
date: 2014-04-21
forum: Desktop Environments
---

### Post by vrghost on 2014-04-21
Have just installed lubuntu on a laptop to be used for general surfing, and having a nightmare with the IBUS application. 
Basically, it breakes the input stream for applications such as Chromium, and considering that its job is to allow me to change input channel, the fact that it breaks it probably means that it is a bit of a waste of an application. 

Any way, had to get that of my chest.

My problem is, how do I either uninstall it or remove it from auto start, because I have absolutely no use for the application, but it is stopping the user from being able to write.
If I try to uninstall it, it wants to uninstall Ubuntu-desktop at the same time, and kind of need the desktop I reckon.

---

### Post by kevjonesin on 2014-06-02
I also would like to remove ibus from lubuntu 14.04 (without breaking lubuntu-desktop). Ibus interferes with the chromium web-browser.

NOTE: The lubuntu 14.04 docs reccommend removal of ibus as a bug fix but do not provide information as to how to do so.
> **Known Issues**

  
**Installation**

 Some  keyboard layouts may have problems (such as UK ones). You can  workaround the problem by removing all the ibus-* packages (see [1284635]("https://bugs.launchpad.net/bugs/1284635")))

 quote via: [https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/Lubuntu](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/Lubuntu)

---

### Post by vasa1 on 2014-06-02
Go to **Preferences > Language Support** and change **Keyboard input method system** from **ibus** to **none**. Then log out and log in again.

---

### Post by vasa1 on 2014-06-02
> **kevjonesin said:**
> I also would like to remove ibus from lubuntu 14.04 (without breaking lubuntu-desktop). ...
BTW, "lubuntu-desktop" is only a metapackage and is not essential; if you get a notice it will be removed, all the applications will remain intact. "lubuntu-desktop" may be required only if you want to upgrade from 14.04 to 14.10 when the next version of Lubuntu becomes available. If you prefer to do a clean install, as many of us do, then it doesn't matter.

Some reading:
help.ubuntu.com/community/MetaPackages
ubuntuforums.org/showpost.php?p=12389408&postcount=5
[www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html](www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html)
askubuntu.com/q/233662

---

### Post by kevjonesin on 2014-06-02
Ah, turns out that as lubuntu-desktop is a just meta-package I was able to remove it without affecting other packages. I was then able to remove ibus packages. (thanks to a tip on lubuntu's freenode IRC)

---

### Post by TheFu on 2015-02-25
Just wanted to add that removing ibus and the ibus libs fixed an issue with keepassx autotype where it shoved garbage into the 2nd field. So far, I haven't seen any bad results elsewhere, but my desktop is a pure WM, no DE, setup.  X/Windows as it was meant to be 15 yrs ago. ;)

---

