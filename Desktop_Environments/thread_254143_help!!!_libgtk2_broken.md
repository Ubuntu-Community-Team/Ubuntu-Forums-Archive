---
title: "help!!! libgtk2 broken"
date: 2006-09-09
forum: Desktop Environments
---

### Post by boast on 2006-09-09
When I try to do apt-get anything I get ```
The following packages have unmet dependencies:
  libgtk2.0-0: Depends: libgtk2.0-common (= 2.8.20-1) but 2.8.18-0ubuntu2 is to be installed
               Depends: libatk1.0-0 (>= 1.12.1) but 1.11.4-0ubuntu1 is to be installed
               Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
               Depends: libcairo2 (>= 1.2.2) but 1.0.4-0ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

I don't want to do apt-get -f install because it would remove 400mb of programs installed. What do I to be able to reinstall libgtk2 without uninstalling everything.

---

### Post by Ramses de Norre on 2006-09-09
What are your sources??

---

### Post by boast on 2006-09-09
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse



## MAJOR BUG FIX UPDATES produced after the final release
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
#deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

# The Opera web browser repopsitory
deb http://deb.opera.com/opera etch non-free
deb http://download.gna.org/praksys praksys/

## PEERGUARDIAN
deb http://moblock-deb.sourceforge.net/debian unstable main
deb-src http://moblock-deb.sourceforge.net/debian unstable main

##WINE
deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main

deb http://apt.cerkinfo.be/ unstable main contrib
deb-src http://apt.cerkinfo.be/ unstable main contrib

##gaim 2 beta 3
deb http://people.ubuntu.com/~seb128/deb ./ 
deb-src http://people.ubuntu.com/~seb128/deb ./

```

---

### Post by boast on 2006-09-10
i really need this fixed.

---

### Post by boast on 2006-09-11
i thought ubuntu was good for the community support


i was lied to. aahhhh

---

### Post by boast on 2006-09-12
sigh ](*,)

---

### Post by ebash on 2006-09-12
It looks like if one of your extra repositories broke your libgtk2.

Try commenting all the repositories execpt for those in the domain ubuntu.com. 

Then do:
```

sudo apt-get udpdate
sudo apt-get dist-upgrade

```

---

### Post by Anduu on 2006-09-12
I bet it is this one
```
## PEERGUARDIAN
deb http://moblock-deb.sourceforge.net/debian unstable main
deb-src http://moblock-deb.sourceforge.net/debian unstable main
```

or this one
```
deb http://apt.cerkinfo.be/ unstable main contrib
deb-src http://apt.cerkinfo.be/ unstable main contrib
```

Comment those out and apt-get update/upgrade again.

---

### Post by boast on 2006-09-13
I had put the debian rep. in order to try to get the newer version of libgtk2.

```
user@UbuntuBox:~$ sudo apt-get udpdate
E: Invalid operation udpdate
user@UbuntuBox:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libgtk2.0-0: Depends: libgtk2.0-common (= 2.8.20-1) but 2.8.18-0ubuntu2 is installed
               Depends: libatk1.0-0 (>= 1.12.1) but 1.11.4-0ubuntu1 is installed
               Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is installed
               Depends: libcairo2 (>= 1.2.2) but 1.0.4-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.

```

---

### Post by Anduu on 2006-09-13
> **boast said:**
> I had put the debian rep. in order to try to get the newer version of libgtk2.

```
user@UbuntuBox:~$ sudo apt-get udpdate
E: Invalid operation udpdate
user@UbuntuBox:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libgtk2.0-0: Depends: libgtk2.0-common (= 2.8.20-1) but 2.8.18-0ubuntu2 is installed
               Depends: libatk1.0-0 (>= 1.12.1) but 1.11.4-0ubuntu1 is installed
               Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is installed
               Depends: libcairo2 (>= 1.2.2) but 1.0.4-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.

```

Trying to update system files using Debian repos is ***always*** a bad idea.

---

### Post by boast on 2006-09-14
Is there no command or way I can force ONLY the reinstall of libgtk2 and nothing else?

---

### Post by boast on 2006-09-16
> **boast said:**
> Is there no command or way I can force ONLY the reinstall of libgtk2 and nothing else?

???????????

---

### Post by Anduu on 2006-09-16
OK once you have gotten rid of the offending entries in your sources.list open synaptic and hit reload.

Then find libgtk2 and highlight it.Then select Package>Force Version from the menu and choose the previous one.

---

