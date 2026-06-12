---
title: "Ubuntu Server 8.10, bad apt sources, unable to update"
date: 2009-04-06
forum: General Help
---

### Post by Predatorian on 2009-04-06
hello all,

i recently downloaded and installed ubuntu server 8.10. so far i am happy with the base intallation, but i wanted to install some other programs, and for some reason, apt-get update gives me a bunch of errors, mainly cannot resolve the servers. what should i do fix the apt sources file? 
i can ping outside my gateway, and conenct to the net, but im not sure what eles i need to do.

---

### Post by taurus on 2009-04-06
Post the output of this command from a prompt.

```
sudo apt-get update
```
Also, post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```
p.s.  You don't happen to use proxy, do you?

---

### Post by KayakJim on 2009-04-06
Can you post the actual messages that you receive when you run apt-get update?

---

### Post by Predatorian on 2009-04-06
```
 W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2  Could not resolve 'de.archive.ubuntu.com'
-bash: W:: command not found
predatorian@Ubu-Serv:~$
predatorian@Ubu-Serv:~$ W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2  Could not resolve 'de.archive.ubuntu.com'
-bash: W:: command not found
predatorian@Ubu-Serv:~$
predatorian@Ubu-Serv:~$ W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2  Could not resolve 'de.archive.ubuntu.com'
-bash: W:: command not found
predatorian@Ubu-Serv:~$
predatorian@Ubu-Serv:~$ W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'de.archive.ubuntu.com'
-bash: W:: command not found
predatorian@Ubu-Serv:~$
predatorian@Ubu-Serv:~$ W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg  Could not resolve 'de.archive.ubuntu.com'
-bash: W:: command not found
predatorian@Ubu-Serv:~$
predatorian@Ubu-Serv:~$ W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'de.archive.ubuntu.com'
-bash: W:: command not found
predatorian@Ubu-Serv:~$
predatorian@Ubu-Serv:~$ W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'de.archive.ubuntu.com'
-bash: W:: command not found
predatorian@Ubu-Serv:~$
predatorian@Ubu-Serv:~$ W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'de.archive.ubuntu.com'
-bash: W:: command not found
predatorian@Ubu-Serv:~$
predatorian@Ubu-Serv:~$ W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'de.archive.ubuntu.com'
-bash: W:: command not found
predatorian@Ubu-Serv:~$
predatorian@Ubu-Serv:~$ W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg  Could not resolve 'security.ubuntu.com'
-bash: W:: command not found
predatorian@Ubu-Serv:~$
predatorian@Ubu-Serv:~$ W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'
-bash: W:: command not found
predatorian@Ubu-Serv:~$
predatorian@Ubu-Serv:~$ W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'
-bash: W:: command not found
predatorian@Ubu-Serv:~$
predatorian@Ubu-Serv:~$ W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'
-bash: W:: command not found
predatorian@Ubu-Serv:~$
predatorian@Ubu-Serv:~$ W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'
-bash: W:: command not found
predatorian@Ubu-Serv:~$
predatorian@Ubu-Serv:~$ W: Some index files failed to download, they have been ignored, or old ones used instead.
-bash: W:: command not found
predatorian@Ubu-Serv:~$ W: You may want to run apt-get update to correct these problems
-bash: W:: command not found
predatorian@Ubu-Serv:~$

predatorian@Ubu-Serv:~$ sudo apt-get update
Err http://de.archive.ubuntu.com intrepid Release.gpg
  Could not resolve 'de.archive.ubuntu.com'
Err http://de.archive.ubuntu.com intrepid/main Translation-en_US
  Could not resolve 'de.archive.ubuntu.com'
Err http://de.archive.ubuntu.com intrepid/restricted Translation-en_US
  Could not resolve 'de.archive.ubuntu.com'
Err http://de.archive.ubuntu.com intrepid/universe Translation-en_US
  Could not resolve 'de.archive.ubuntu.com'
Err http://de.archive.ubuntu.com intrepid/multiverse Translation-en_US
  Could not resolve 'de.archive.ubuntu.com'
Err http://de.archive.ubuntu.com intrepid-updates Release.gpg
  Could not resolve 'de.archive.ubuntu.com'
Err http://de.archive.ubuntu.com intrepid-updates/main Translation-en_US
  Could not resolve 'de.archive.ubuntu.com'
Err http://de.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
  Could not resolve 'de.archive.ubuntu.com'
Err http://de.archive.ubuntu.com intrepid-updates/universe Translation-en_US
  Could not resolve 'de.archive.ubuntu.com'
Err http://de.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
  Could not resolve 'de.archive.ubuntu.com'
Err http://security.ubuntu.com intrepid-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com intrepid-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com intrepid-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com intrepid-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg  Could not resolve 'de.archive.ubuntu.com'

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2  Could not resolve 'de.archive.ubuntu.com'

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2  Could not resolve 'de.archive.ubuntu.com'

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2  Could not resolve 'de.archive.ubuntu.com'

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'de.archive.ubuntu.com'

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg  Could not resolve 'de.archive.ubuntu.com'

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'de.archive.ubuntu.com'

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'de.archive.ubuntu.com'

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'de.archive.ubuntu.com'

W: Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'de.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


```

---

### Post by Predatorian on 2009-04-06
```

  GNU nano 2.0.7                                            File: /etc/apt/sources.list

#
# deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release i386 (20081028.1)]/ intrepid main restricted

#deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release i386 (20081028.1)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://de.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://de.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://de.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://de.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://de.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse




^G Get Help                   ^O WriteOut                   ^R Read File                  ^Y Prev Page                  ^K Cut Text                   ^C Cur Pos
^X Exit                       ^J Justify                    ^W Where Is                   ^V Next Page                  ^U UnCut Text                 ^T To Spell

```

---

### Post by Predatorian on 2009-04-08
i was thinking, would i have to edit any files like the hosts file since i had to statically give my server an IP? i guess that was another problem, my DHCP "server" wouldnt give my server the right IP. would that have something to do with it?

---

