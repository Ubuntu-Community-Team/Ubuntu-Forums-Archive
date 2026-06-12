---
title: "apt-get update Problems.."
date: 2005-12-08
forum: Desktop Environments
---

### Post by windowsXuser on 2005-12-08
When i booted up kubuntu today and tried to update my repositories i get these errors:

 
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras Release.gpg
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg
  Temporary failure resolving 'packages.freecontrib.org'
Err [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg
  Temporary failure resolving 'kubuntu.org'
Err [http://soulmachine.net](http://soulmachine.net) unstable/ Release.gpg
  Temporary failure resolving 'soulmachine.net'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy Release.gpg
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release.gpg
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Temporary failure resolving 'ca.archive.ubuntu.com'
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Temporary failure resolving 'ca.archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/breezy-extras/Release.gpg](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/Release.gpg)  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg)  Temporary failure resolving 'packages.freecontrib.org'
Failed to fetch [http://kubuntu.org/packages/kde35/dists/breezy/Release.gpg](http://kubuntu.org/packages/kde35/dists/breezy/Release.gpg)  Temporary failure resolving 'kubuntu.org'
Failed to fetch [http://soulmachine.net/breezy/unstable/Release.gpg](http://soulmachine.net/breezy/unstable/Release.gpg)  Temporary failure resolving 'soulmachine.net'
Reading package lists... Done
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://kubuntu.org](http://kubuntu.org) breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde35_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://soulmachine.net](http://soulmachine.net) unstable/ Packages (/var/lib/apt/lists/soulmachine.net_breezy_unstable_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


for some reason it cant connect to any of my repositories.  I am a little confused at why its doing this.  I did the update as the superuser and just before i tried the update i installed prelink in adept manager. I uninstalled it because i though that was the problem, but still get the same errors.

help please.

blair..

---

### Post by RAOF on 2005-12-08
All those errors essentially say "I can't connect to the internet, so I can't connect to the repositories".  So, the first step of the solution is: does your internet work? ;)

---

### Post by aysiu on 2005-12-08
Mirrormax is no longer around, as far as I know.
Follow the instructions in the first link of my sig.

---

### Post by windowsXuser on 2005-12-08
All my repositories were fine yesterday and everyother time i update them. For some reason its not working today.

my internet doesn't work when i log into linux, but its fine in windows.

I though it was my internet, but its fine on my windows partition.

Blair..

---

### Post by funkydan2 on 2005-12-08
How are you trying to access the internet - dial-up modem, wireless network, wired network?

---

### Post by RAOF on 2005-12-08
Ok, so your internet is **not** working in linux.  Thus, when "apt-get update" tries to connect to the repositories, and download the latest package list, it won't work.  **Now** we get to play "get your internet working in Ubuntu" :)

---

### Post by windowsXuser on 2005-12-08
i am connecting through a router which uses rogers hi speed cable.  

I guess it is my internet, but the thing is it was fine before today.  Havent changed anything.

blair..

---

### Post by funkydan2 on 2005-12-08
So you can open up your favourite web-browser when you're running **Ubuntu** and browse to these forums?

---

### Post by zasf on 2005-12-18
[QUOTE=RAOF]Ok, so your internet is **not** working in linux.  Thus, when "apt-get update" tries to connect to the repositories, and download the latest package list, it won't work.  **Now** we get to play "get your internet working in Ubuntu" :)[/QUOTE]

Hi RAOF, i'm having the same problem as windowsXuser, apt-get update won't find repositories, it seems like he's trying to connect to the internet, but it times out

```
matteo@ubuntu:~$ sudo apt-get update
Password:
Err http://security.ubuntu.com breezy-security Release.gpg
  Impossibile connettersi a security.ubuntu.com:80 (1.0.0.0), tempo limite di connessione esaurito
Err http://archive.ubuntu.com breezy Release.gpg
  Impossibile connettersi a archive.ubuntu.com:80 (1.0.0.0), tempo limite di connessione esaurito
0% [Connessione a archive.ubuntu.com (1.0.0.0) in corso
```

I'm connecting with my ethernet card via router, the problem is that internet works!! I'm surfing the net with firefox under ubuntu, right now!! Can you help me?

---

### Post by antidrugue on 2005-12-18
What is the content of /etc/apt/sources.list?

```

cat /etc/apt/sources.list

```

Post it!

---

### Post by zasf on 2005-12-18
[QUOTE=antidrugue]What is the content of /etc/apt/sources.list?

```

cat /etc/apt/sources.list

```

Post it![/QUOTE]

here it is

```
matteo@ubuntu:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```

---

### Post by aysiu on 2005-12-18
[QUOTE=zasf]
  Impossibile connettersi a archive.ubuntu.com:80 (1.0.0.0), tempo limite di connessione esaurito
0% [Connessione a archive.ubuntu.com (1.0.0.0) in corso[/CODE][/QUOTE] Timeout errors usually have nothing to do with your sources.list. They're usually a firewall or proxy issue. Unfortunately, I don't know how to solve the timeout issue, but if you search around these forums, you may find something on apt-get update timeouts.

---

### Post by zasf on 2005-12-18
[QUOTE=aysiu]Timeout errors usually have nothing to do with your sources.list. They're usually a firewall or proxy issue. Unfortunately, I don't know how to solve the timeout issue, but if you search around these forums, you may find something on apt-get update timeouts.[/QUOTE]

You might be right, I switched from wired to wireless and now it works.

```
matteo@ubuntu:~$ sudo apt-get update
Password:
Get:1 http://it.archive.ubuntu.com breezy Release.gpg [189B]
Ign http://security.ubuntu.com breezy-security Release.gpg
Get:2 http://it.archive.ubuntu.com breezy-updates Release.gpg [189B]
Ign http://security.ubuntu.com breezy-security Release
Get:3 http://it.archive.ubuntu.com breezy Release [30,9kB]
Ign http://security.ubuntu.com breezy-security/main Packages
Ign http://security.ubuntu.com breezy-security/restricted Packages
Ign http://security.ubuntu.com breezy-security/main Sources
Get:4 http://it.archive.ubuntu.com breezy-updates Release [19,6kB]
Ign http://security.ubuntu.com breezy-security/restricted Sources
Ign http://security.ubuntu.com breezy-security/universe Packages
Get:5 http://it.archive.ubuntu.com breezy/main Packages [586kB]
Ign http://security.ubuntu.com breezy-security/multiverse Packages
Ign http://security.ubuntu.com breezy-security/universe Sources
Ign http://security.ubuntu.com breezy-security/multiverse Sources
Err http://security.ubuntu.com breezy-security/main Packages
  301 Moved Permanently
Err http://security.ubuntu.com breezy-security/restricted Packages
  301 Moved Permanently
Err http://security.ubuntu.com breezy-security/main Sources
  301 Moved Permanently
Err http://security.ubuntu.com breezy-security/restricted Sources
  301 Moved Permanently
Err http://security.ubuntu.com breezy-security/universe Packages
  301 Moved Permanently
Err http://security.ubuntu.com breezy-security/multiverse Packages
  301 Moved Permanently
Err http://security.ubuntu.com breezy-security/universe Sources
  301 Moved Permanently
Err http://security.ubuntu.com breezy-security/multiverse Sources
  301 Moved Permanently
Get:6 http://it.archive.ubuntu.com breezy/restricted Packages [5061B]
Get:7 http://it.archive.ubuntu.com breezy/main Sources [232kB]
Get:8 http://it.archive.ubuntu.com breezy/restricted Sources [1454B]
Get:9 http://it.archive.ubuntu.com breezy/universe Packages [2304kB]
Get:10 http://it.archive.ubuntu.com breezy/multiverse Packages [91,9kB]
Get:11 http://it.archive.ubuntu.com breezy/universe Sources [914kB]
Get:12 http://it.archive.ubuntu.com breezy/multiverse Sources [46,9kB]
Get:13 http://it.archive.ubuntu.com breezy-updates/main Packages [17,9kB]
Get:14 http://it.archive.ubuntu.com breezy-updates/restricted Packages [14B]
Get:15 http://it.archive.ubuntu.com breezy-updates/main Sources [5088B]
Get:16 http://it.archive.ubuntu.com breezy-updates/restricted Sources [14B]
Get:17 http://it.archive.ubuntu.com breezy-updates/universe Packages [8204B]
Get:18 http://it.archive.ubuntu.com breezy-updates/multiverse Packages [708B]
Get:19 http://it.archive.ubuntu.com breezy-updates/universe Sources [743B]
Get:20 http://it.archive.ubuntu.com breezy-updates/multiverse Sources [365B]
Scaricato 4266kB in 1m39s (42,8kB/s)
Impossibile ottenere http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz  301 Moved Permanently
Impossibile ottenere http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz  301 Moved Permanently
Impossibile ottenere http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz  301 Moved Permanently
Impossibile ottenere http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz  301 Moved Permanently
Impossibile ottenere http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz  301 Moved Permanently
Impossibile ottenere http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz  301 Moved Permanently
Impossibile ottenere http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz  301 Moved Permanently
Impossibile ottenere http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/source/Sources.gz  301 Moved Permanently
Lettura della lista dei pacchetti in corso... Fatto
E: Impossibile scaricare alcune file di indice, essi verranno ignorati, oppure si useranno quelli precedenti.
```

I can ping anything, but not it.archive.ubuntu.com.. could it be a dns problem??

---

### Post by zasf on 2005-12-18
not working anymore.. anyone willing to help? I'm getting mad at this

```
matteo@ubuntu:~$ ping ubuntuforums.org
PING ubuntuforums.org (64.21.33.9) 56(84) bytes of data.
64 bytes from ubuntuforums.org (64.21.33.9): icmp_seq=1 ttl=49 time=184 ms
64 bytes from ubuntuforums.org (64.21.33.9): icmp_seq=2 ttl=49 time=191 ms
64 bytes from ubuntuforums.org (64.21.33.9): icmp_seq=3 ttl=49 time=183 ms
64 bytes from ubuntuforums.org (64.21.33.9): icmp_seq=4 ttl=49 time=184 ms
64 bytes from ubuntuforums.org (64.21.33.9): icmp_seq=5 ttl=49 time=186 ms

--- ubuntuforums.org ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4003ms
rtt min/avg/max/mdev = 183.427/185.915/191.375/2.956 ms
matteo@ubuntu:~$ ping it.archive.ubuntu.com
PING it.archive.ubuntu.com (194.185.88.30) 56(84) bytes of data.

--- it.archive.ubuntu.com ping statistics ---
25 packets transmitted, 0 received, 100% packet loss, time 23996ms

matteo@ubuntu:~$
```

---

### Post by zasf on 2005-12-18
this is really strange.. the only way for me to get apt-get working is to connect via firefox to it.archive.ubuntu.com, then I hit F5 a few times, do apt-get and it works.. any ideas??

---

