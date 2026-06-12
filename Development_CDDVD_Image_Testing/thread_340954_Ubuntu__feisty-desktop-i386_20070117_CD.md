---
title: "Ubuntu  feisty-desktop-i386 20070117 CD"
date: 2007-01-17
forum: Development CD/DVD Image Testing
---

### Post by bigern75 on 2007-01-17
When you hit install it does nothing.
This is the output after sudo ubiquity

ubuntu@ubuntu:~$ sudo ubiquity
Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 185, in <module>
    main()
  File "/usr/lib/ubiquity/bin/ubiquity", line 182, in main
    install()
  File "/usr/lib/ubiquity/bin/ubiquity", line 44, in install
    mod = __import__('ubiquity.frontend', globals(), locals(), frontends)
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 53, in <module>
    from ubiquity.debconfcommunicator import DebconfCommunicator
  File "/usr/lib/ubiquity/ubiquity/debconfcommunicator.py", line 22, in <module>
    import debconf
ImportError: No module named debconf
ubuntu@ubuntu:~$

---

### Post by pochu on 2007-01-18
Please, search for that bug at Launchpad and add a comment with that, confirming it.

Thanks
Pochu

---

### Post by bigern75 on 2007-01-18
bug 80253 ***

sudo/gksudo is irrelevant (and in any case you don't need to explicitly
sudo to run Ubiquity in Feisty any more - it'll gain root by itself).
 since fixed in debconf.

** Changed in: ubiquity (Ubuntu)
Sourcepackagename: ubiquity => debconf

---

### Post by UBfusion on 2007-01-18
> **pochu said:**
> Please, search for that bug at Launchpad and add a comment with that, confirming it.

Thanks
Pochu

It is a part of bug #78810: [https://bugs.launchpad.net/ubuntu/+bug/78810](https://bugs.launchpad.net/ubuntu/+bug/78810)

Please use the debconf workaround described in Comment 9 and report there if you can go further with the partitioning and formatting.

---

