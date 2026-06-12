---
title: "Partial Upgrade required??"
date: 2009-03-05
forum: General Help
---

### Post by fig_wright on 2009-03-05
I have been trying to get rid of old kernels that are left lying around on my system, as I have very little disk space left. In particular the modules and headers of the kernels are left around. Trying to remove them with package manager often doesnt work for some reason - they either fail to uninstall or they just end up in the "autoremove" section and wont go.

I found a cleaning script called ubucleaner.sh which I ran and it did the trick and cleared them all :D The script runs "sudo aptitude purge $OLDKERNELS"

But... yesterday some new updates appeared for download, and now when I launch package manger to do it it tells me that I need to do a "Partial Upgrade" for some reason. If I proceed, I am told that it wants to **reinstall** some of the kernels I got rid of! :( Why??

---

### Post by fig_wright on 2009-03-09
No one seen this before?? :(

---

### Post by fig_wright on 2009-03-15
OK, I just did the partial upgrade and then ran ubucleaner.sh to remove the re-installed old kernels again.

---

