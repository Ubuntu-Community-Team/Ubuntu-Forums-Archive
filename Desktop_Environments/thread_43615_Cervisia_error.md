---
title: "Cervisia error"
date: 2005-06-22
forum: Desktop Environments
---

### Post by ivomans on 2005-06-22
After upgrading to Kubuntu's KDE 3.4.1 I'm getting following error in Cervisia:

> cvsaskpass: error while loading shared libraries: libkdeinit_cvsaskpass.so: cannot open shared object file: No such file or directory
Permission denied, please try again. 

I don't get a dialog for entering my password for the repository and so I'm not able to update or whatsoever.

I tried locating the file libkdeinit_cvsaskpass.so, but it's not on my system at all.

Anybody got advice how to solve this?

---

### Post by SGC on 2005-06-22
Try to install Cervisia again ( sudo apt-get install cervisia )

---

### Post by ivomans on 2005-06-22
Just tried 'sudo apt-get install cervisia': refused since cervisia was already installed.

Then I tried 'sudo apt-get --reinstall install cervisia': that did a reinstall, but in the end still resulting in the same error.

---

### Post by ecadre on 2005-07-06
I'm getting exactly the same error,  libkdeinit_cvsaskpass.so  seems to be missing from the Cervisia package.

I use CVS every day so losing a working Cervisia is a real pain!

---

### Post by alanic on 2005-07-18
someone please do a bug report

---

### Post by hod139 on 2005-08-15
I too am getting this error, and was wondering if anyone has filed a bug report yet.

---

### Post by ivomans on 2005-08-15
[QUOTE=hod139]I too am getting this error, and was wondering if anyone has filed a bug report yet.[/QUOTE]

I just did: [http://bugzilla.ubuntu.com/show_bug.cgi?id=13498](http://bugzilla.ubuntu.com/show_bug.cgi?id=13498)

---

### Post by hod139 on 2005-08-22
[QUOTE=ivomans]I just did: [http://bugzilla.ubuntu.com/show_bug.cgi?id=13498](http://bugzilla.ubuntu.com/show_bug.cgi?id=13498)[/QUOTE]

FYI, the fix from bugzilla is: "Please use the KDE 3.4.2 packages"

---

