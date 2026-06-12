---
title: "dpkg error"
date: 2008-12-10
forum: General Help
---

### Post by bjm1904 on 2008-12-10
I get the following error every time I try to install something:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

This also comes up when I try to run Synaptic Package manager. While updating, the files are downloaded, but they are not installed.

I have run ```
dpkg --configure -a
```, only to get the following output:

```
dpkg: parse error, in file `/var/lib/dpkg/updates/0055' near line 1:
 newline in field name `#padding'

```
This has only been the case since a recent kernel upgrade. I am tempted to reinstall Ubuntu Intrepid, but what's to stop this happening again?

If anyone has come across this problem, then any help would be appreciated. Otherwise I'll submit this as a bug report.

---

### Post by taurus on 2008-12-10
Probably some package didn't get installed completely so you have to run that command to fix a broken package.  So, make sure you close down synaptic, add/remove, or update-manager.  Then open a terminal and run

```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by bjm1904 on 2008-12-10
I tried that, but unfortunately it didn't solve the problem - I just got the same error as before. Thanks for your help though. :)

---

### Post by taurus on 2008-12-10
I don't even have that file, /var/lib/dpkg/updates/0055, on my machine!

---

### Post by linux_tech on 2008-12-10
Open synaptic package manager and click on Edit > Fix broken packages to fix your broken packages

---

