---
title: "Medibuntu?..."
date: 2009-02-05
forum: General Help
---

### Post by Josshill on 2009-02-05
How do I add Medibuntu?... Can someone help me.. The guides arnt making to much since..

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
tom@ubuntu:~$ 


Thanks,
Joss

---

### Post by taurus on 2009-02-05
Which release are you running?

Applications -> Accessories -> Terminal
```
lsb_release -a
```

---

### Post by Josshill on 2009-02-05
> **taurus said:**
> Which release are you running?

Applications -> Accessories -> Terminal
```
lsb_release -a
```

> No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid
tom@ubuntu:~$ 


Hope that helps.

---

### Post by mc4man on 2009-02-05
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by Josshill on 2009-02-05
> **mc4man said:**
> ```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

I got this error when I did the second command:
> 
E: Malformed line 60 in source list /etc/apt/sources.list (dist parse)


Any help?

---

### Post by m_duck on 2009-02-05
Line 60 has an error in, presumably from one of the guides. Post the output of the following command and I'll see what it is (hopefully :p ) ```
cat /etc/apt/sources.list
```

---

### Post by Josshill on 2009-02-05
> **m_duck said:**
> Line 60 has an error in, presumably from one of the guides. Post the output of the following command and I'll see what it is (hopefully :p ) ```
cat /etc/apt/sources.list
```

Alright,

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
tom@ubuntu:~$ 

```

---

### Post by m_duck on 2009-02-05
Okay, it looks like you just need to delete this line (the bottom one) ```
deb http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```You can do this by typing the following in a terminal window, deleting the line and saving the file```
gksudo gedit /etc/apt/sources.list
```After that, run the following in a terminal and then you should be good to go for re-adding the medibuntu repo ```
sudo apt-get update
```If there are no errors, to add the medibuntu repo, past the following two commands into terminal (one at a time)```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
``````
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by Josshill on 2009-02-05
> **m_duck said:**
> Okay, it looks like you just need to delete this line (the bottom one) ```
deb http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```You can do this by typing the following in a terminal window, deleting the line and saving the file```
gksudo gedit /etc/apt/sources.list
```After that, run the following in a terminal and then you should be good to go for re-adding the medibuntu repo ```
sudo apt-get update
```If there are no errors, to add the medibuntu repo, past the following two commands into terminal (one at a time)```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
``````
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
You are truely a brilliant man M_Duck. Thanks :)

Joss

---

### Post by m_duck on 2009-02-05
Why thank you :D

Glad to be of service.

---

### Post by Josshill on 2009-02-05
> **m_duck said:**
> Why thank you :D

Glad to be of service.

Great after all that work skype wont work =/

Joss..

---

