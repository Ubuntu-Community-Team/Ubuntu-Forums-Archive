---
title: "ongoing problems with apt-get and update manager"
date: 2010-06-10
forum: Desktop Environments
---

### Post by 6py7 on 2010-06-10
I can't seem to get apt-get or the update manager to work consistently since I upgraded to 10.04.  

First, I get a regular segmentation fault on about a daily basis, I run sudo rm /var/cache/apt/*.bin as I saw in other threads, and then it usually works.

However now anytime I try to update, upgrade or install, I get the following error:

Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing git-cola (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Does anyone know how I can fix this? Thanks

---

### Post by drs305 on 2010-06-10
> **6py7 said:**
> 
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Does anyone know how I can fix this? Thanks

Try opening Synaptic or Software Sources. Click on Settings, Repositories: Ubuntu Software tab. Note which ones are selected, then deselect them. Do the same in the Third Party/Other Software tabs. Then reselect all the ones you unticked.

This should restore the repositories and eliminate any errors in the lists. RELOAD after reselecting the repositories to update the available packages.

---

### Post by 6py7 on 2010-06-10
That solved the issue- then I found out a .deb package was corrupted and I think that was causing the whole thing. I removed it, reinstalled those packages and life seems good. Thanks for your help!

---

### Post by drs305 on 2010-06-10
Glad you fixed it. Would you please mark the thread SOLVED via the "Thread Tools" link at the top right of the original post. It helpers others find threads with known solutions and allows 'helpers' concentrate on unresolved issues.

Should it become necessary, the status can be reversed via the same link.  ;-)

---

### Post by 6py7 on 2010-06-13
Just a heads up for anyone who may face these issues.  I was getting segmentation faults in almost every program I ran, and it turns out I had a bad stick of RAM.  I removed it and everything runs fine now.

---

