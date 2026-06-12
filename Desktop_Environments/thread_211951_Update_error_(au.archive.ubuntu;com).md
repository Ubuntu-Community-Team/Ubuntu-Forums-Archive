---
title: "Update error (au.archive.ubuntu;com) ???"
date: 2006-07-09
forum: Desktop Environments
---

### Post by pcolamar on 2006-07-09
Hi,
  that's one of the 7 messagges I am getting today morning while doing the automatic update.

Any idea why ??

Thanks
Palmer

--------- error msg ------------
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.2.1-0ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.2.1-0ubuntu1_i386.deb)
  404 Not Found

---

### Post by slimdog360 on 2006-07-09
Im getting the same thing so dont worry your not alone, though this doesnt mean I know how to solve it. sorry

---

### Post by pcolamar on 2006-07-09
Maybe they are still sleeping in Australia !   :-)

---

### Post by slimdog360 on 2006-07-09
okay I know how to fix it, the credit goes to woedend.
open a terminal
  ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
 sudo gedit /etc/apt/sources.list
```
then get rid of the   au.  in the addresses that you see that look like
 [http://au.archive.ubuntu.com/](http://au.archive.ubuntu.com/)...
so it looks like
 [http://archive.ubuntu.com/](http://archive.ubuntu.com/)...
then save the file and type into the terminal
```
sudo apt-get update
sudo apt-get upgrade

```
one line at a time.

---

### Post by maskd on 2006-07-09
You just have to give it time for the files to be transfered throughout the mirrors, try again in a couple of hours and the file will be downloaded.

---

### Post by enbuyukfener on 2008-04-26
> **pcolamar said:**
> Hi,
  that's one of the 7 messagges I am getting today morning while doing the automatic update.

Any idea why ??

Thanks
Palmer

--------- error msg ------------
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.2.1-0ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.2.1-0ubuntu1_i386.deb)
  404 Not Found
This happened again (au.archive.ubuntu.com is down or not working) and this is a near top Google result so I'll just add that the fix is to choose a different software source (system > administration > software sources). Easiest option is to select "best server" and use the one it recommends.

If you are a BigPond customer, and you have BigPond repositories for everything but multiverse, you can manually edit your /etc/apt/sources.list (as root) and replace [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) to [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) (note: planetmirror.com is supposedly the "best" server by ubuntu's ping tests but that mirror gave me trouble with 302 issues that synaptic would not accept)

And then reload/update, e.g. sudo apt-get update or press reload in Synaptic

The reason I added this despite the solution above is that the above recommended using a non-Australian server (or so i think, maybe it determines the user's country and redirects accordingly). Also to give a GUI method of solving the problem.

pcolamar and maskd: That doesn't matter, the only thing that would affect is the time until new packages or package versions are made available. Until then, the old packages are available.

---

