---
title: "Repository Error"
date: 2008-12-13
forum: General Help
---

### Post by amgc5 on 2008-12-13
Need some help/direction on the following: I am trying to get my system updated using the Update manager/ terminal and get the error detailed below.

Update Manager: The system was last updated over 200 days ago. When I click on the "Check" Box to update ...I get the following error:

Could not download all repository Indexes

Failed to fetch [http://www.getautomatix.com/apt/dists/gutsy/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/gutsy/main/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

a. I would like to know what exactly is going on?
b. Would like to fix this?

Thanks/am.

---

### Post by SPr on 2008-12-13
Open a terminal and enter:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.automatix
gksudo gedit /etc/apt/sources.list

```
and at the start of the line that says "http://www.getautomatix.com/apt/dist...86/Packages.gz" add a # (hash sign) to comment out that repository. Automatix is not used any more.

```

sudo aptitude update
sudo aptitude safe-upgrade

```
or
```

sudo apt-get update
sudo apt-get upgrade

```
depending on whether you use apt-get or aptitude. If you use add/remove programs or Synaptic use the "apt-get" version.

Can you update now or do the same errors appear?

---

### Post by amgc5 on 2008-12-13
No Errors! But don't I need some repository? Do I replace it with something more current?

---

### Post by adult swim on 2008-12-13
if all of your stuff still works then you dont need to add any more repositories.  if you find you cant play mp3s or videos then youll need to run 
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by SPr on 2008-12-13
Well, which version of Ubuntu do you use? If you haven't had any updates for the past 200 days then support for that version may have ended.

---

