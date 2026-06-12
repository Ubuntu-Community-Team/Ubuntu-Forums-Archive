---
title: "Synaptic, apt-get, Gaim do not work!"
date: 2005-12-28
forum: Desktop Environments
---

### Post by desperate_cry on 2005-12-28
Hi,

I tried to find & solve the IPv6 problem in a week time :???: 

Now, i can open webpages, vs vs... But i can not use synaptic, or apt-get to install apps and also Gaim do not connect to MSN server...

I think the problem is the same that causes connection errors, i'm using a Minton ADSL Modem, may i have config errors?

I tried to change the repositories and also checked the sources.list, and i found nothing, i have no idea about what is wrong...:confused: 

Please help, i got tired...

---

### Post by desperate_cry on 2005-12-28
No suggestions?
No solutions?

---

### Post by spincricket on 2005-12-28
ok. step by step. What error do you get when you use apt-get. Can you post your sources.list?

---

### Post by desperate_cry on 2005-12-28
sources.list

```

#deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
#deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

#deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

#deb-src http://security.ubuntu.com/ubuntu breezy-security universe


deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
#deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free

deb http://archive.ubuntu.com/ubuntu breezy-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main universe multiverse restricted

deb ftp://ftp.nerim.net/debian-marillat/ sarge main

deb http://ubuntu.tower-net.de/ubuntu/ breezy java
#deb ftp://ftp.nerim.net/debian-marillat/ sid main

deb http://wine.sourceforge.net/apt breezy/
deb http://people.ubuntu.com/~doko/OOo2 ./

#deb http://mirror.free.net.ph/debian-volatile stable/volatile main
deb http://pkg-boinc.alioth.debian.org/debian/ sarge main
#deb http://www.csd.uwo.ca/~mfgalizi/debian hoary unichrome

```

$sudo apt-get update returns;

```

d3s@cryptobox:~$ sudo apt-get update
Err http://people.ubuntu.com ./ Release.gpg
  Could not connect to people.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com breezy-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ubuntu.tower-net.de breezy Release.gpg
  Could not connect to ubuntu.tower-net.de:80 (32.1.7.168), connection timed outErr ftp://ftp.nerim.net sarge Release.gpg
  Could not create a socket for 2001:7a8:1:5::14 (f=10 t=1 p=6) - socket (97 Address family not supported by protocol) [IP: 2001:7a8:1:5::14 21]
Err http://antesis.freecontrib.org breezy Release.gpg
  Could not connect to antesis.freecontrib.org:80 (32.1.7.168), connection timed out
Err http://wine.sourceforge.net breezy/ Release.gpg
  Could not connect to wine.sourceforge.net:80 (32.1.7.168), connection timed out
Err http://pkg-boinc.alioth.debian.org sarge Release.gpg
  Could not connect to pkg-boinc.alioth.debian.org:80 (32.1.7.168), connection timed out
Err http://ubuntu-backports.mirrormax.net breezy-extras Release.gpg
  Could not connect to ubuntu-backports.mirrormax.net:80 (32.1.7.168), connection timed out
Ign ftp://ftp.nerim.net sarge Release
Ign ftp://ftp.nerim.net sarge/main Packages
Err ftp://ftp.nerim.net sarge/main Packages
  Could not create a socket for 2001:7a8:1:5::14 (f=10 t=1 p=6) - socket (97 Address family not supported by protocol) [IP: 2001:7a8:1:5::14 21]
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg  Could not connect to antesis.freecontrib.org:80 (32.1.7.168), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/breezy-extras/Release.gpg  Could not connect to ubuntu-backports.mirrormax.net:80 (32.1.7.168), connection timed out
Failed to fetch ftp://ftp.nerim.net/debian-marillat/dists/sarge/Release.gpg  Could not create a socket for 2001:7a8:1:5::14 (f=10 t=1 p=6) - socket (97 Address family not supported by protocol) [IP: 2001:7a8:1:5::14 21]
Failed to fetch http://ubuntu.tower-net.de/ubuntu/dists/breezy/Release.gpg  Could not connect to ubuntu.tower-net.de:80 (32.1.7.168), connection timed out
Failed to fetch http://wine.sourceforge.net/apt/breezy/Release.gpg  Could not connect to wine.sourceforge.net:80 (32.1.7.168), connection timed out
Failed to fetch http://people.ubuntu.com/~doko/OOo2/./Release.gpg  Could not connect to people.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://pkg-boinc.alioth.debian.org/debian/dists/sarge/Release.gpg  Could not connect to pkg-boinc.alioth.debian.org:80 (32.1.7.168), connection timed out
Failed to fetch ftp://ftp.nerim.net/debian-marillat/dists/sarge/main/binary-i386/Packages.gz  Could not create a socket for 2001:7a8:1:5::14 (f=10 t=1 p=6) - socket (97 Address family not supported by protocol) [IP: 2001:7a8:1:5::14 21]
Reading package lists... Done
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net sarge/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_sarge_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu.tower-net.de breezy/java Packages (/var/lib/apt/lists/ubuntu.tower-net.de_ubuntu_dists_breezy_java_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://wine.sourceforge.net breezy/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://people.ubuntu.com ./ Packages (/var/lib/apt/lists/people.ubuntu.com_%7edoko_OOo2_._Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://pkg-boinc.alioth.debian.org sarge/main Packages (/var/lib/apt/lists/pkg-boinc.alioth.debian.org_debian_dists_sarge_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


```

---

### Post by spincricket on 2005-12-28
Why dont you backup your current sources.list , and use this one :
```
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
Then:
```
sudo apt-get update
```

And lastly, are you behind a firewall?

---

### Post by spincricket on 2005-12-28
```
d3s@cryptobox:~$ sudo apt-get update
Err http://people.ubuntu.com ./ Release.gpg
  Could not connect to people.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com breezy-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ubuntu.tower-net.de breezy Release.gpg

```
Do you see in the brackets, the "1.0.0.0" I.P address? Are you connected to the modem or are you using wireless. I dont think that should be there. 
Also run this
```
ping -c 10 archive.ubuntu.com
```
and paste results please.

Also these errors:
```
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net sarge/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_sarge_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu.tower-net.de breezy/java Packages (/var/lib/apt/lists/ubuntu.tower-net.de_ubuntu_dists_breezy_java_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://wine.sourceforge.net breezy/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://people.ubuntu.com ./ Packages (/var/lib/apt/lists/people.ubuntu.com_%7edoko_OOo2_._Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://pkg-boinc.alioth.debian.org sa
```
Are caused by the repositories. Try the ones i posted and the other suggestions. See what happens. Wow, ill let you digest all i said. :)

---

### Post by desperate_cry on 2005-12-28
1.
```

d3s@cryptobox:~$ ping -c 10 archive.ubuntu.com
PING archive.ubuntu.com (82.211.81.182) 56(84) bytes of data.
64 bytes from archive.ubuntu.com (82.211.81.182): icmp_seq=1 ttl=51 time=94.6 ms64 bytes from archive.ubuntu.com (82.211.81.182): icmp_seq=2 ttl=51 time=92.6 ms64 bytes from archive.ubuntu.com (82.211.81.182): icmp_seq=3 ttl=51 time=93.1 ms64 bytes from archive.ubuntu.com (82.211.81.182): icmp_seq=4 ttl=51 time=161 ms
64 bytes from archive.ubuntu.com (82.211.81.182): icmp_seq=5 ttl=51 time=93.2 ms64 bytes from archive.ubuntu.com (82.211.81.182): icmp_seq=6 ttl=51 time=264 ms
64 bytes from archive.ubuntu.com (82.211.81.182): icmp_seq=7 ttl=51 time=93.4 ms64 bytes from archive.ubuntu.com (82.211.81.182): icmp_seq=8 ttl=51 time=93.1 ms64 bytes from archive.ubuntu.com (82.211.81.182): icmp_seq=9 ttl=51 time=92.3 ms64 bytes from archive.ubuntu.com (82.211.81.182): icmp_seq=10 ttl=51 time=95.2 ms

--- archive.ubuntu.com ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9005ms
rtt min/avg/max/mdev = 92.308/117.371/264.261/53.021 ms

```

2.
```

d3s@cryptobox:~$ sudo apt-get update
Get:1 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Get:4 http://archive.ubuntu.com breezy Release [30.9kB]
Get:5 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:6 http://security.ubuntu.com breezy-security Release [19.6kB]
Get:7 http://archive.ubuntu.com breezy-updates Release [19.6kB]
Get:8 http://archive.ubuntu.com breezy-backports Release [19.6kB]
Get:9 http://archive.ubuntu.com breezy/main Packages [586kB]
Get:10 http://security.ubuntu.com breezy-security/main Packages [28.5kB]
Get:11 http://security.ubuntu.com breezy-security/restricted Packages [4458B]
Get:12 http://security.ubuntu.com breezy-security/main Sources [8844B]
Get:13 http://security.ubuntu.com breezy-security/restricted Sources [960B]
Get:14 http://security.ubuntu.com breezy-security/universe Packages [23.1kB]
Get:15 http://security.ubuntu.com breezy-security/universe Sources [3722B]
Get:16 http://archive.ubuntu.com breezy/restricted Packages [5061B]
Get:17 http://archive.ubuntu.com breezy/main Sources [232kB]
Get:18 http://archive.ubuntu.com breezy/restricted Sources [1454B]
Get:19 http://archive.ubuntu.com breezy/universe Packages [2304kB]
Get:20 http://archive.ubuntu.com breezy/universe Sources [914kB]
Get:21 http://archive.ubuntu.com breezy/multiverse Packages [91.9kB]
Get:22 http://archive.ubuntu.com breezy/multiverse Sources [46.9kB]
Get:23 http://archive.ubuntu.com breezy-updates/main Packages [17.9kB]
Get:24 http://archive.ubuntu.com breezy-updates/restricted Packages [14B]
Get:25 http://archive.ubuntu.com breezy-updates/main Sources [5088B]
Get:26 http://archive.ubuntu.com breezy-updates/restricted Sources [14B]
Get:27 http://archive.ubuntu.com breezy-backports/main Packages [8850B]
Get:28 http://archive.ubuntu.com breezy-backports/restricted Packages [14B]
Get:29 http://archive.ubuntu.com breezy-backports/universe Packages [22.3kB]
Get:30 http://archive.ubuntu.com breezy-backports/multiverse Packages [875B]
Fetched 4397kB in 1m37s (45.3kB/s)
Reading package lists... Done

```

:smile:  Hehe, at last i'm so happy... It seems that's OKE :KS 

Now, the second problem; i still get "Reading Error" when connecting to MSN Server using port 207.46.4.97. And X-chat can not connect...

I'm not behind a firewall...
...
Thanks!

---

### Post by desperate_cry on 2005-12-28
But, maybe pinging  -c 10 archive.ubuntu.com is the point that solves packet receiving  prob?

And also, GAIM, X-Chat does not work...

---

### Post by desperate_cry on 2005-12-28
```

d3s@cryptobox:~$ ping -c 10 archive.ubuntu.com
PING archive.ubuntu.com (1.0.0.0) 56(84) bytes of data.

--- archive.ubuntu.com ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 8998ms

```

```

d3s@cryptobox:~$ sudo apt-get update
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.

```

I'm behind an ADSL Modem/Router and there's another machine(WindowsXP) connected to Router :confused:

---

### Post by spincricket on 2005-12-28
woah, waht did you do, is that what you get with 
```
sudo apt-get update
```?

Try also
```
sudo apt-get upgrade
```

I thought you had it working a second ago. 
Your router probably has a firewall. Are you behind proxy?

---

### Post by desperate_cry on 2005-12-28
1.
```

d3s@cryptobox:~$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
d3s@cryptobox:~$ sudo apt-get update
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.

```

2. Screenshots attached...

---

### Post by desperate_cry on 2005-12-28
And now, it's working again...
Upgrading...

But something wrong about Modem config, i think...

---

