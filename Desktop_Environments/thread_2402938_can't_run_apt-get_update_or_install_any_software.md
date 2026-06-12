---
title: "can't run apt-get update or install any software"
date: 2018-10-05
forum: Desktop Environments
---

### Post by Lost Crotchet on 2018-10-05
Hi All,

It seems my package manager in Ubuntu 16.04 is completely broken. When running ```
sudo apt-get update
``` I get the following:

```
Err:1 http://archive.canonical.com/ubuntu trusty InRelease  Could not connect to 213.192.64.75:41258 (213.192.64.75). - connect (111: Connection refused)
Err:2 http://archive.ubuntu.com/ubuntu trusty InRelease                                       
  Could not connect to 213.192.64.75:41258 (213.192.64.75). - connect (111: Connection refused)
Err:3 http://archive.ubuntu.com/ubuntu trusty-updates InRelease                               
  Unable to connect to 213.192.64.75:41258:
Err:4 http://extras.ubuntu.com/ubuntu trusty InRelease
  Could not connect to 213.192.64.75:41258 (213.192.64.75). - connect (111: Connection refused)
Err:5 http://archive.ubuntu.com/ubuntu trusty-security InRelease
  Unable to connect to 213.192.64.75:41258:
Err:6 http://archive.ubuntu.com/ubuntu trusty-backports InRelease
  Unable to connect to 213.192.64.75:41258:
Err:7 http://archive.ubuntu.com/ubuntu xenial InRelease
  Unable to connect to 213.192.64.75:41258:
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty/InRelease  Could not connect to 213.192.64.75:41258 (213.192.64.75). - connect (111: Connection refused)
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease  Unable to connect to 213.192.64.75:41258:
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-security/InRelease  Unable to connect to 213.192.64.75:41258:
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease  Unable to connect to 213.192.64.75:41258:
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/trusty/InRelease  Could not connect to 213.192.64.75:41258 (213.192.64.75). - connect (111: Connection refused)
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/InRelease  Could not connect to 213.192.64.75:41258 (213.192.64.75). - connect (111: Connection refused)
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease  Unable to connect to 213.192.64.75:41258:
W: Some index files failed to download. They have been ignored, or old ones used instead.



```


When trying to install any software I get:
```
sudo apt-get install nmap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nmap is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'nmap' has no installation candidate



```

Any ideas?

---

### Post by #&amp;thj^% on 2018-10-05
You have both Trusty 14.04 and Xenial 16.04 for download sources>>>this is a bad way to go as you can plainly see.
You will need to amend those to correct your problem.
For 16.04 your /etc/apt/sources.list should read as follows:
```
#deb cdrom:[Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2)]/ xenial main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
```
Now try updating again

---

### Post by Lost Crotchet on 2018-10-10
Hi 1fallen

From following that, the new error message I get is this:

```
Err:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease  Could not connect to 213.192.64.75:41258 (213.192.64.75). - connect (111: Connection refused)
Err:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease
  Unable to connect to 213.192.64.75:41258:
Err:3 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease
  Unable to connect to 213.192.64.75:41258:
Err:4 http://security.ubuntu.com/ubuntu xenial-security InRelease
  Could not connect to 213.192.64.75:41258 (213.192.64.75). - connect (111: Connection refused)
Reading package lists... Done                   
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial/InRelease  Could not connect to 213.192.64.75:41258 (213.192.64.75). - connect (111: Connection refused)
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease  Unable to connect to 213.192.64.75:41258:
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease  Unable to connect to 213.192.64.75:41258:
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease  Could not connect to 213.192.64.75:41258 (213.192.64.75). - connect (111: Connection refused)
W: Some index files failed to download. They have been ignored, or old ones used instead.



```

---

### Post by Autodave on 2018-10-11
What is the possibility of you either reinstalling 16.04 or 18.04?  I have always found that a clean install works way better than upgrading.  Make sure that you backup everything important to an external source first!!

---

### Post by Lost Crotchet on 2018-10-13
Reinstalling would be very awkward because I will have to reinstall so much much software. Also my external hard drive is already full, so I'd have to buy a new external hard drive just to back up whilst reinstalling...

---

### Post by dino99 on 2018-10-13
Test the 'main' archive:
> sudo gedit   /etc/apt/sources.list 
and remove 'us.' in front of 'archive; then save.

Before doing something else, clean the system:
> sudo apt-get autoremove
> sudo apt-get autoclean
> sudo apt-get clean

Reboot, then:
> sudo dpkg --configure -a
> sudo apt-get update
> sudo apt-get install -f

---

### Post by Holger_Gehrke on 2018-10-13
What surprises me a bit is the address and port it's trying to connect to. 'us.archive.ubuntu.com' is 91.189.91.23 or 91.189.91.25 while 213.192.64.75 is 'v75.viator.gda.pl'. Have you perhaps configured a proxy which has stopped working ?

Holger

---

### Post by Lost Crotchet on 2018-10-13
I haven't used a proxy for a long time, but what I find very strange, is that when I go to network proxy and click from Method, "none" to "manual", it appears 213.192.64.75 is the last proxy address I used! Why the hell is the package manager using that proxy when I've clearly turned it off? :S

---

### Post by Lost Crotchet on 2018-10-16
The issue is fixed now.

My issue was that there appeared to be the aforementioned proxy configured in /etc/apt/apt.conf , so I set it to "false" for all protocols as follows:

```
Acquire::http::proxy "false";
Acquire::https::proxy "false";
Acquire::ftp::proxy "false";
Acquire::socks::proxy "false";
```

---

### Post by dino99 on 2018-10-18
Good to know you have fixed it. Please set that thread as "SOLVED" from the top right dropdown menu (1st post)

---

