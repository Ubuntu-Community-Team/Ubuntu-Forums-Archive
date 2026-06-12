---
title: "Synaptic  Package manager issues"
date: 2009-06-01
forum: General Help
---

### Post by EgilsBlood on 2009-06-01
Yeah long time since i used Ubuntu just started to use it again as Windows just got lamer and lamer but i have an issue with SPM every time i try to open it it gives me a message witch says 

> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/is.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

and its bugging me a bit any solutions

---

### Post by michy99 on 2009-06-01
In a terminal enter```
sudo apt-get update
```and post any error messages you get.

---

### Post by sisco311 on 2009-06-01
This post could be related to an Ubuntu bug filed at:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/370294]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/370294")

Open a terminal (Application -> Accessories -> Terminal)
and remove the file:
```
sudo rm -i /var/lib/apt/lists/is.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages
```


Be careful when using rm! The rm command can delete your entire filesystem!

---

### Post by EgilsBlood on 2009-06-01
> **michy99 said:**
> In a terminal enter```
sudo apt-get update
```and post any error messages you get.


> Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Fetched 174kB in 1s (98.0kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/is.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.[/QUOTE]


i got this

---

### Post by Kevbert on 2009-06-01
Please try this in terminal:
```

cd /var/lib/dpkg
sudo mv status status-bad
sudo cp status-old status
sudo apt-get update

```
It looks like your package status file has been corrupted.

---

### Post by EgilsBlood on 2009-06-01
it has some sort of issues with (sudo mv status status-bad) think its a typo in it

---

### Post by michy99 on 2009-06-01
Have you tried the suggestion by sisco311 above?

---

### Post by EgilsBlood on 2009-06-01
what sisco311 sended had no effect

---

### Post by Soul-Sing on 2009-06-01
```
sudo rm /var/lib/apt/lists/* -vf
```

```
sudo apt-get update
```

---

### Post by Kevbert on 2009-06-02
> **EgilsBlood said:**
> it has some sort of issues with (sudo mv status status-bad) think its a typo in it

You should get a prompt for your login password. The command is renaming the status file to status-bad. There's no typo as I've just rechecked this in Hardy. Please post back any error that is displayed.  Alternatively you could remove the status file with
```
sudo rm status
```
and then rename the status-old file to status with
```
sudo cp status-old status
```
which means that until you update, the contents of both status-old and status files will be the same.

---

