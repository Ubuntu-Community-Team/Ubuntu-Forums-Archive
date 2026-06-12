---
title: "update error in ubuntu 20.04"
date: 2020-11-18
forum: Desktop Environments
---

### Post by slkamath on 2020-11-18
Hi everyone,

Hope al are staying safe & healthy.

while updating from terminal in ubuntu 20.04 i am getting below error.

```
sudo apt update
Err:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease
  400  Bad Request [IP: 91.189.88.152 80]
Err:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates InRelease
  400  Bad Request [IP: 91.189.88.152 80]
Err:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports InRelease
  400  Bad Request [IP: 91.189.88.152 80]
Err:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security InRelease
  400  Bad Request [IP: 91.189.88.152 80]
Hit:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease
Reading package lists... Done
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
E: The repository 'http://archive.ubuntu.com/ubuntu focal InRelease' is not signed.
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/focal/InRelease](http://archive.ubuntu.com/ubuntu/dists/focal/InRelease)  400  Bad Request [IP: 91.189.88.152 80]
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
E: The repository 'http://archive.ubuntu.com/ubuntu focal-updates InRelease' is not signed.
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/focal-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/focal-updates/InRelease)  400  Bad Request [IP: 91.189.88.152 80]
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/focal-backports/InRelease](http://archive.ubuntu.com/ubuntu/dists/focal-backports/InRelease)  400  Bad Request [IP: 91.189.88.152 80]
E: The repository 'http://archive.ubuntu.com/ubuntu focal-backports InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/focal-security/InRelease](http://archive.ubuntu.com/ubuntu/dists/focal-security/InRelease)  400  Bad Request [IP: 91.189.88.152 80]
E: The repository 'http://archive.ubuntu.com/ubuntu focal-security InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

can someone help me to resolve this issue
Thanks in advance.

Lokesh Kamath

---

### Post by ajgreeny on 2020-11-18
Please show us the content of your sources.list file with cat** /etc/apt/sources.list** as I suspect something there is the problem.

Has updating been successful in the past or is this a new installation?

---

### Post by slkamath on 2020-11-18
Hi Ajgreeny,

Thanks for your response.

In initial update it's updated successfully. 

Later it started giving that error.

I will send you the cat** /etc/apt/sources.list **by tomorrow morning.

Lokesh Kamath

---

### Post by ActionParsnip on 2020-11-18
Do you use a proxy for web access, or a VPN?

---

### Post by grahammechanical on 2020-11-18
You could try opening Software & Updates>Ubuntu software and selecting another download server. I think that you are using the Main Server. You can try selecting Other and then selecting a server closer to your location.

Regards.

---

### Post by slkamath on 2020-11-18
Thanks for your response.

cat** /etc/apt/sources.list **

```
# deb cdrom:[Ubuntu 20.04.1 LTS _Focal Fossa_ - Release amd64 (20200731)]/ focal main restricted

#See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) focal universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic main universe multiverse restricted
#deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) bionic-security main multiverse universe restricted
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates main multiverse universe restricted
```

Proxy is there for other machines, this machine have direct internet.

I changed that too. but no use.

Initially it was India server, i changed to Main server. No luck...

---

### Post by ActionParsnip on 2020-11-19
If you run:
```

echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf > /dev/null
sudo apt-get update

```

is it OK then?

---

