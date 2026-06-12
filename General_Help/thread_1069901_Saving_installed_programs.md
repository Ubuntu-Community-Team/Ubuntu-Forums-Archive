---
title: "Saving installed programs"
date: 2009-02-14
forum: General Help
---

### Post by MyFathersSon on 2009-02-14
Is there any way to back up installed software and upgrades to disk?

I hate the idea of having to re-download everything in the event of a recovery.

Under Windows all you do is run a self extracting program that installs itself.  You can save these program to CD or something.

This whole package manager scheme seems to assume that you will always have access to the net, and/or the net will always be up and running.

I want to be able to save the downloaded software to CD or something.

---

### Post by geirha on 2009-02-14
If you have not run «sudo apt-get clean» then all packages that have been installed from the repositories should be located under: /var/cache/apt/archives/

Also, have a look at: [https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)

---

