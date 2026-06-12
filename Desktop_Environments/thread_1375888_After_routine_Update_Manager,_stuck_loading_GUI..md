---
title: "After routine Update Manager, stuck loading GUI."
date: 2010-01-08
forum: Desktop Environments
---

### Post by Metaxa on 2010-01-08
One evening I finished running Update manager on 9.10 and shut my machine down for the night. The next morning I got an error message " Install Error, power management (somethingsomething) failed and needs to be reinstalled". After 20 seconds it goes away and I get an additional failure, failed to start evolution-alarm. After pressing Ok, the system busy icon for my mouse cursor keeps spinning and doesn't load. I have restarted the machine and tried recovery mode to upgrade all damaged packages but nothing has changed. Any advise would be appreciated. 

Metaxa

---

### Post by SalahTr on 2010-01-08
What's the following command's output :
```
sudo apt-get upgrade
```

---

### Post by Metaxa on 2010-01-08
All packages are up to date, 0 upgraded. paraphrased of course.

---

### Post by SalahTr on 2010-01-08
send me **/var/log/messages** file

---

### Post by Metaxa on 2010-01-11
Anyone else able to lend a hand?



Metaxa

---

### Post by pavi_elex on 2011-11-04
```
sudo dpkg --configure -a
sudo aptitude install -f
sudo apt-get update
```or
Replace your apt directory from /etc with new-fresh and try
```
sudo apt-get update
sudo apt-get upgrade
```or
```
sudo apt-get clean
sudo apt-get dist-upgrade
```or
```
do-release-upgrade
```

---

