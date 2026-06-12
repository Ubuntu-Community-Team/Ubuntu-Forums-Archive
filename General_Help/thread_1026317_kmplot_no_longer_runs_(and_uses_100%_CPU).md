---
title: "kmplot no longer runs (and uses 100% CPU)"
date: 2008-12-31
forum: General Help
---

### Post by s3a on 2008-12-31
Running it from menu has same problem but to offer something to work with:

[I]deniz@deniz-laptop:~$ kmplot
kmplot(7977) MainDlg::MainDlg: parentWidget->objectName(): "KmPlot"
kmplot(7977) MainDlg::setupActions: KStandardDirs::resourceDirs( icon )= ("/home/deniz/.kde/share/icons/", "/usr/share/icons/")
^C
deniz@deniz-laptop:~$[/I]

Earlier on today, it worked perfectly! After playing around excessively with the zooming in and out, I noticed this problem. Please help because this program helps me with school!

Edit: When I run it as root, it works!:

deniz@deniz-laptop:~$ kmplot
kmplot(6753) MainDlg::MainDlg: parentWidget->objectName(): "KmPlot"
kmplot(6753) MainDlg::setupActions: KStandardDirs::resourceDirs( icon )= ("/home/deniz/.kde/share/icons/", "/usr/share/icons/")
^C
deniz@deniz-laptop:~$ sudo -i
root@deniz-laptop:~# kmplot
kmplot(6780) MainDlg::MainDlg: parentWidget->objectName(): "KmPlot"
kmplot(6780) MainDlg::setupActions: KStandardDirs::resourceDirs( icon )= ("/root/.kde/share/icons/", "/usr/share/icons/")
root@deniz-laptop:~# logout
deniz@deniz-laptop:~$

As user it still uses 100% CPU and doesn't really launch while as root, it launches without a problem!

---

### Post by s3a on 2009-01-21
I went to **/home/deniz/.kde** and deleted the folder called: **share** and then ran it as user and it works perfectly again! (replace *deniz* by whatever your user name is if you ever experience such a problem)

---

