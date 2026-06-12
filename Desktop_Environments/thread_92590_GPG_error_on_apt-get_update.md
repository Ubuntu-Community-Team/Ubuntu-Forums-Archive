---
title: "GPG error on apt-get update"
date: 2005-11-19
forum: Desktop Environments
---

### Post by b3nw on 2005-11-19
Fetched 191B in 2s (90B/s)
Reading package lists... Done
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

giving apt-get update only returns this error, please advise!

---

### Post by aysiu on 2005-11-19
Read the first link in my sig.

---

### Post by ihristov on 2006-02-15
The solution is the post from **AgenT** at
[http://ubuntuforums.org/showthread.php?t=128602](http://ubuntuforums.org/showthread.php?t=128602)

> 
There's some weird glitch where residual info hangs out and gives you a GPG signature error. If that's the case, do this:

```

# become root
sudo su

# go to apt folder
cd /etc/apt

# Back up current sources.list
cp sources.list sources.list_backup

# make an empty sources.list
> sources.list

# update with your empty repositories list
apt-get update

# revert to saved list
cp sources.list_backup sources.list

# update again and this time you should get no errors
apt-get update 

```


---

