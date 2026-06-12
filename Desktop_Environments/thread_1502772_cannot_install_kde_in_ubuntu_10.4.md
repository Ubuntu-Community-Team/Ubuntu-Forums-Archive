---
title: "cannot install kde in ubuntu 10.4"
date: 2010-06-06
forum: Desktop Environments
---

### Post by Rorschachdigital on 2010-06-06
so yea basically i went into terminal and  typed  "[FONT=monospace]sudo apt-get install kubuntu-desktop"
and it told me that the packages dependencies could not be resolved and installed.

anyone have any advice on how to work around this or what to install to get past this hiccup?          thank you kindly
[/FONT]

---

### Post by Nythain on 2010-06-06
```

sudo add-apt-repository ppa:kubuntu-ppa/ppa

```
will add the kubuntu updates ppa, wich should have everything kubuntu-desktop needs to install, and up to date at that

---

### Post by aysiu on 2010-06-06
> **Rorschachdigital said:**
> so yea basically i went into terminal and  typed  "[FONT=monospace]sudo apt-get install kubuntu-desktop"
and it told me that the packages dependencies could not be resolved and installed.

anyone have any advice on how to work around this or what to install to get past this hiccup?          thank you kindly
[/FONT]
Sounds as if you have conflicting repositories.

Can you paste these commands into the terminal and then post the output back here? ```
sudo apt-get update
cat /etc/apt/sources.list
```

---

### Post by Rorschachdigital on 2010-06-06
thank you for the responses guys 
nythain i did ask you suggested  and it told me i still had broken packages and dependencies not met

 here are the responses you asked for aysiu


sudo apt-get update 
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources.gz)  Unable to connect to packages.freecontrib.org:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.


cat /etc/apt/sources.list
    ## Add comments (##) in front of any line to remove it from being checked.
    ## Use the following sources.list at your own risk.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

    ## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

    ## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

    ## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

    ## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

---

### Post by Rorschachdigital on 2010-06-06
also when i input 
sudo add-apt-repository  ppa:kubuntu-ppa/ppa

this was my output :
sudo add-apt-repository ppa:kubuntu-ppa/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv E4DFEC907DEDA4B8A670E8042836CB0A8AC93F7A
gpg: requesting key 8AC93F7A from hkp server keyserver.ubuntu.com
gpg: key 8AC93F7A: "Launchpad Kubuntu Updates" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

---

### Post by aysiu on 2010-06-06
Actually, apart from your down PLF repositories (the freecontrib error), your sources look fine.

If you do have broken ones, maybe this command might help: ```
sudo apt-get -f install
```

---

### Post by Rorschachdigital on 2010-06-06
perhaps thats the thing then  when i try to install it the coding at the bottom tells me there are broken packages.

---

### Post by vahrammur on 2010-06-29
Hello, I don't have direct connection to Internet, how can I install KDE desktop of ubuntu 10.04 server offline.

---

### Post by aysiu on 2010-06-29
> **vahrammur said:**
> Hello, I don't have direct connection to Internet, how can I install KDE desktop of ubuntu 10.04 server offline.
Get a hold of the Kubuntu *Alternate* CD, add it as a software source, and then install KDE through the CD.

This will **not** work with the Kubuntu Desktop CD. You need the Alternate CD.

---

