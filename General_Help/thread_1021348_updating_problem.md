---
title: "updating problem"
date: 2008-12-25
forum: General Help
---

### Post by garrynigel on 2008-12-25
alright 
i have a  problem ... i have a linux kernel version2.6.27-7 and bye mistake i installed  linux headers for 2.6.27-11.. now der are some headers or some files for linux 2.6.27-7 dat i wanted to install..or update.. first a warning comes sayn u are supposed to install software not authenticated ..etc den i pressd install der was a error sayn cant lock the file
not possible to install  Failed to lock /var/cache/apt/archives/loc
dis is wat was coming wat do i do..?

---

### Post by taurus on 2008-12-25
Sounds like you have another process (add/remove, synaptic, adept, etc.) running in the background.

Look at the output of this list to see if you see any.

Applications -> Accessories -> Terminal
```
ps -A
```

---

### Post by albinootje on 2008-12-25
> **garrynigel said:**
> alright 
i have a  problem ... i have a linux kernel version2.6.27-7 and bye mistake i installed  linux headers for 2.6.27-11.. now der are some headers or some files for linux 2.6.27-7 dat i wanted to install..or update.. first a warning comes sayn u are supposed to install software not authenticated 

Can you run this in a terminal :
```

sudo apt-get update

```
And post the errors ?
> 
..etc den i pressd install der was a error sayn cant lock the file
not possible to install  Failed to lock /var/cache/apt/archives/loc
dis is wat was coming wat do i do..?

After a boot the update-manager will try to update the information about the repositories.
Also, you cannot use apt-get in a terminal and have Synaptic package manager open at the same time.
Try again now, and see whether it works now.

---

