---
title: "Restoring improperly renamed files"
date: 2020-05-01
forum: Desktop Environments
---

### Post by couzin2000 on 2020-05-01
Help!
I'm running a Ubuntu fileserver at home. Running Samba. I accessed the Ubuntu shared folders from a Mac Mini running High Sierra. 

On the Mac, I was using an app called NameChanger - a batch file rename app. I had a folder B nested in folder A. I selected all the files from B and some individual files from A, opened all in NameChanger. I chose to remove the last "-1" that was in the filenames (for example: IMAX.Antartica.1999.DVD-1.m4v). Once I hit @rename@, all the files were renamed. I then selected a "Change Case" tool in NameChanger and ran that. Immediately, 12 out of 14 files disappeared! Cannot be found anymore!

I need those files back. How do I find them or even look for them? Should I start in Ubuntu, or the Mac? Any tools I can use?

Edit: The files were stored in a mounted ExFAT partition on a USB3-attached HDD.

---

### Post by lvm on 2020-05-02
Ok, files are gone, that means that they have either been moved to a new location or deleted so do nothing with this disk. If files have been moved and you say it happened instantaneously chances are they remain on the same disk. Search for them using locate (running updatedb.mlocate before that to refresh locate database is recommended) or find. If they have been deleted, on ubuntu you can use testdisk to try to recover them

---

