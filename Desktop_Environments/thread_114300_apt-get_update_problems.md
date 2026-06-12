---
title: "apt-get update problems"
date: 2006-01-08
forum: Desktop Environments
---

### Post by psyone on 2006-01-08
I've tried almost everything about this problems, but so far nothing has helped.

I always get the same errors when I do: apt-get update

```
stef@laptopStef:~$ sudo apt-get update
Password:
Get:1 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:2 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy Release.gpg [189B]
Hit http://security.ubuntu.com breezy-security Release
Hit http://archive.ubuntu.com breezy-updates Release
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://archive.ubuntu.com breezy Release
Hit http://security.ubuntu.com breezy-security/restricted Packages
Ign http://archive.ubuntu.com breezy-updates/main Packages
Ign http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Ign http://archive.ubuntu.com breezy/main Packages
Ign http://archive.ubuntu.com breezy/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Ign http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Ign http://archive.ubuntu.com breezy/main Sources
Ign http://archive.ubuntu.com breezy/universe Sources
Ign http://archive.ubuntu.com breezy/multiverse Sources
Get:4 http://archive.ubuntu.com breezy/restricted Sources [1454B]
Ign http://archive.ubuntu.com breezy/restricted Sources
Get:5 http://archive.ubuntu.com breezy-updates/main Packages [20.4kB]
98% [5 Packages gzip 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com breezy-updates/main Packages
  Sub-process gzip returned an error code (1)
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Get:6 http://archive.ubuntu.com breezy/main Packages [769kB]
99% [Connecting to archive.ubuntu.com (82.211.81.182)]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com breezy/main Packages
  Sub-process gzip returned an error code (1)
Get:7 http://archive.ubuntu.com breezy/universe Packages [3028kB]
99% [Connecting to archive.ubuntu.com (82.211.81.182)]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com breezy/universe Packages
  Sub-process gzip returned an error code (1)
Get:8 http://archive.ubuntu.com breezy/multiverse Packages [116kB]
99% [Connecting to archive.ubuntu.com (82.211.81.182)]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com breezy/multiverse Packages
  Sub-process gzip returned an error code (1)
Get:9 http://archive.ubuntu.com breezy/main Sources [305kB]
99% [Connecting to archive.ubuntu.com (82.211.81.182)]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com breezy/main Sources
  Sub-process gzip returned an error code (1)
Hit http://archive.ubuntu.com breezy/universe Sources
Get:10 http://archive.ubuntu.com breezy/multiverse Sources [58.0kB]
99% [Connecting to archive.ubuntu.com (82.211.81.182)]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com breezy/multiverse Sources
  Sub-process gzip returned an error code (1)
Err http://archive.ubuntu.com breezy/restricted Sources
  416 Requested Range Not Satisfiable [IP: 82.211.81.182 80]
Fetched 9B in 3s (3B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binar y-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/P ackages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i3 86/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary- i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Source s.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/ Sources.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/ Sources.gz  416 Requested Range Not Satisfiable [IP: 82.211.81.182 80]
Reading package lists... Done
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/ma in Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_m ain_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packa ges (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_ Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe P ackages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_bina ry-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse  Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_ binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.

```

416 Requested Range Not Satisfiable [IP: 82.211.81.182 80]
Sub-process gzip returned an error code

are the main errors that keep coming back, I tried various sources.list files but none of them can solve it

my source.list:

```
 Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

I personally (though I don't know much about apt or anything) think someting is wrong with my internet configuration.
The strange thing is, I had ubuntu installed a week ago, and then everything worked fine, but then I re-installed it and the problem began.
I'm sure that, the time synaptic was working (thus a week ago) my internet configuration was pretty much the same (I mean that I look at the System>Administration>Networking, and there are no differences with a week ago.)

I can surf the internet without any problems and also I can manually browse the archives apt-get can not.

I thank the people who are going to help me...
greetz

---

### Post by socrazy143 on 2006-01-08
I know you said you have tried different sources.list files but try the following that I used from EasyLinux.info:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```

Replace everything with the following lines

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
## You may replace "us" with your country code to get the closest mirror.

deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://ubuntu-backports.mirrormax.net breezy-extras main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf breezy free non-free
```

Save the edited file.

---

### Post by psyone on 2006-01-08
I did what you askes and here are my command lines:

```
stef@laptopStef:/etc/apt$ sudo gedit sources.list
stef@laptopStef:/etc/apt$ sudo apt-get update
Ophalen:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Ophalen:2 http://archive.ubuntu.com breezy Release.gpg [189B]
Ophalen:3 http://security.ubuntu.com breezy-security Release [19,6kB]
Ophalen:4 http://us.archive.ubuntu.com breezy Release.gpg [189B]
Ophalen:5 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Genegeerd http://packages.freecontrib.org breezy Release.gpg
Geraakt http://security.ubuntu.com breezy-security/main Packages
Ophalen:6 http://archive.ubuntu.com breezy Release [30,9kB]
Genegeerd http://ubuntu-backports.mirrormax.net breezy-extras Release.gpg
Ophalen:7 http://us.archive.ubuntu.com breezy-updates Release.gpg [189B]
Genegeerd http://packages.freecontrib.org breezy Release
Ophalen:8 http://archive.ubuntu.com breezy-backports Release [19,6kB]
Geraakt http://security.ubuntu.com breezy-security/restricted Packages
Genegeerd http://packages.freecontrib.org breezy/free Packages
Genegeerd http://packages.freecontrib.org breezy/non-free Packages
Geraakt http://security.ubuntu.com breezy-security/main Sources
Ophalen:9 http://us.archive.ubuntu.com breezy Release [30,9kB]
Ophalen:10 http://archive.ubuntu.com breezy/universe Packages [2304kB]
Genegeerd http://ubuntu-backports.mirrormax.net breezy-extras Release
Genegeerd http://packages.freecontrib.org breezy/free Sources
Genegeerd http://ubuntu-backports.mirrormax.net breezy-extras/main Packages
Genegeerd http://packages.freecontrib.org breezy/non-free Sources
Geraakt http://security.ubuntu.com breezy-security/restricted Sources
Ophalen:11 http://packages.freecontrib.org breezy/free Packages [545B]
8% [Wachtend op de kopteksten] [Wachtend op de kopteksten] [10 Packages 95944/2
gzip: stdin: unexpected end of file
Fout http://packages.freecontrib.org breezy/free Packages
  Subproces gzip gaf de foutcode 1 terug
Ophalen:12 http://security.ubuntu.com breezy-security/universe Packages [23,1kB]
Genegeerd http://ubuntu-backports.mirrormax.net breezy-extras/restricted Package s
Genegeerd http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages
Ophalen:13 http://packages.freecontrib.org breezy/non-free Packages [2337B]
Ophalen:14 http://us.archive.ubuntu.com breezy-updates Release [19,6kB]
Fout http://packages.freecontrib.org breezy/non-free Packages
  Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw i ngesteld)
Ophalen:15 http://packages.freecontrib.org breezy/free Sources [316B]
Genegeerd http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Package s
Fout http://ubuntu-backports.mirrormax.net breezy-extras/main Packages
  Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw i ngesteld)
Ophalen:16 http://security.ubuntu.com breezy-security/universe Sources [3722B]
Ophalen:17 http://packages.freecontrib.org breezy/non-free Sources [473B]
Ophalen:18 http://us.archive.ubuntu.com breezy/main Packages [586kB]
Ophalen:19 http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packag es [33B]
Fout http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages
  Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw i ngesteld)
Ophalen:20 http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages  [33B]
Ophalen:21 http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packag es [33B]
Ophalen:22 http://us.archive.ubuntu.com breezy/restricted Packages [5061B]
Genegeerd http://us.archive.ubuntu.com breezy/restricted Packages
Ophalen:23 http://us.archive.ubuntu.com breezy/main Sources [232kB]
Ophalen:24 http://us.archive.ubuntu.com breezy/restricted Sources [1454B]
Ophalen:25 http://us.archive.ubuntu.com breezy-updates/main Packages [17,9kB]
Ophalen:26 http://us.archive.ubuntu.com breezy-updates/restricted Packages [14B]
Ophalen:27 http://us.archive.ubuntu.com breezy-updates/main Sources [5088B]
Ophalen:28 http://us.archive.ubuntu.com breezy-updates/restricted Sources [14B]
Ophalen:29 http://us.archive.ubuntu.com breezy/restricted Packages [4735B]
94% [29 Packages gzip 0] [10 Packages 2145136/2304kB 93%]            207kB/s 0s
gzip: stdin: not in gzip format
Fout http://us.archive.ubuntu.com breezy/restricted Packages
  Subproces gzip gaf de foutcode 1 terug
Ophalen:30 http://archive.ubuntu.com breezy/multiverse Packages [91,9kB]
Genegeerd http://archive.ubuntu.com breezy/multiverse Packages
Ophalen:31 http://archive.ubuntu.com breezy/universe Sources [914kB]
Genegeerd http://archive.ubuntu.com breezy/universe Sources
Ophalen:32 http://archive.ubuntu.com breezy/multiverse Sources [46,9kB]
Genegeerd http://archive.ubuntu.com breezy/multiverse Sources
Ophalen:33 http://archive.ubuntu.com breezy-backports/main Packages [10,4kB]
Genegeerd http://archive.ubuntu.com breezy-backports/main Packages
Ophalen:34 http://archive.ubuntu.com breezy-backports/restricted Packages [14B]
Genegeerd http://archive.ubuntu.com breezy-backports/restricted Packages
Ophalen:35 http://archive.ubuntu.com breezy-backports/universe Packages [23,0kB]
Genegeerd http://archive.ubuntu.com breezy-backports/universe Packages
Ophalen:36 http://archive.ubuntu.com breezy-backports/multiverse Packages [1353B ]
Genegeerd http://archive.ubuntu.com breezy-backports/multiverse Packages
Ophalen:37 http://archive.ubuntu.com breezy-backports/main Sources [4678B]
Genegeerd http://archive.ubuntu.com breezy-backports/main Sources
Ophalen:38 http://archive.ubuntu.com breezy-backports/restricted Sources [14B]
Genegeerd http://archive.ubuntu.com breezy-backports/restricted Sources
Ophalen:39 http://archive.ubuntu.com breezy-backports/universe Sources [9881B]
Genegeerd http://archive.ubuntu.com breezy-backports/universe Sources
Ophalen:40 http://archive.ubuntu.com breezy-backports/multiverse Sources [701B]
Genegeerd http://archive.ubuntu.com breezy-backports/multiverse Sources
Ophalen:41 http://archive.ubuntu.com breezy/multiverse Packages [116kB]
Fout http://archive.ubuntu.com breezy/multiverse Packages
  Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw i ngesteld) [IP: 82.211.81.151 80]
Ophalen:42 http://archive.ubuntu.com breezy/universe Sources [1223kB]
Fout http://archive.ubuntu.com breezy/universe Sources
  Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw i ngesteld) [IP: 82.211.81.151 80]
Ophalen:43 http://archive.ubuntu.com breezy/multiverse Sources [58,0kB]
57% [43 Sources gzip 0] [Er wordt verbinding gemaakt met archive.ubuntu.com (82
gzip: stdin: not in gzip format
Fout http://archive.ubuntu.com breezy/multiverse Sources
  Subproces gzip gaf de foutcode 1 terug
Ophalen:44 http://archive.ubuntu.com breezy-backports/main Packages [10,4kB]
Fout http://archive.ubuntu.com breezy-backports/main Packages
  Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw i ngesteld) [IP: 82.211.81.151 80]
Ophalen:45 http://archive.ubuntu.com breezy-backports/restricted Packages [20B]
57% [45 Packages gzip 0] [Er wordt verbinding gemaakt met archive.ubuntu.com (8
gzip: stdin: unexpected end of file
Fout http://archive.ubuntu.com breezy-backports/restricted Packages
  Subproces gzip gaf de foutcode 1 terug
Ophalen:46 http://archive.ubuntu.com breezy-backports/universe Packages [25,6kB]
Fout http://archive.ubuntu.com breezy-backports/universe Packages
  Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw i ngesteld) [IP: 82.211.81.151 80]
Ophalen:47 http://archive.ubuntu.com breezy-backports/multiverse Packages [1241B ]
Ophalen:48 http://archive.ubuntu.com breezy-backports/main Sources [4606B]
57% [Er wordt verbinding gemaakt met archive.ubuntu.com (82.211.81.151)]
gzip: stdin: not in gzip format
Fout http://archive.ubuntu.com breezy-backports/main Sources
  Subproces gzip gaf de foutcode 1 terug
Ophalen:49 http://archive.ubuntu.com breezy-backports/restricted Sources [20B]
Ophalen:50 http://archive.ubuntu.com breezy-backports/universe Sources [10,8kB]
57% [Er wordt verbinding gemaakt met archive.ubuntu.com (82.211.81.151)]
gzip: stdin: not in gzip format
Fout http://archive.ubuntu.com breezy-backports/universe Sources
  Subproces gzip gaf de foutcode 1 terug
Ophalen:51 http://archive.ubuntu.com breezy-backports/multiverse Sources [593B]
3366kB opgehaald in 33s (101kB/s)
Ophalen van http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary- i386/Packages.gz Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/bin ary-i386/Packages.gz Fout bij het lezen van de server - read (104 Verbinding doo r partner opnieuw ingesteld) is mislukt
Ophalen van http://ubuntu-backports.mirrormax.net/dists/breezy-extras/main/binar y-i386/Packages.gz Fout bij het lezen van de server - read (104 Verbinding door partner opnieuw ingesteld) is mislukt
Ophalen van http://ubuntu-backports.mirrormax.net/dists/breezy-extras/restricted /binary-i386/Packages.gz Fout bij het lezen van de server - read (104 Verbinding  door partner opnieuw ingesteld) is mislukt
Ophalen van http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i 386/Packages.gz Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386 /Packages.gz Fout bij het lezen van de server - read (104 Verbinding door partne r opnieuw ingesteld) [IP: 82.211.81.151 80] is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Source s.gz Fout bij het lezen van de server - read (104 Verbinding door partner opnieu w ingesteld) [IP: 82.211.81.151 80] is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sour ces.gz Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary- i386/Packages.gz Fout bij het lezen van de server - read (104 Verbinding door pa rtner opnieuw ingesteld) [IP: 82.211.81.151 80] is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/b inary-i386/Packages.gz Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/bin ary-i386/Packages.gz Fout bij het lezen van de server - read (104 Verbinding doo r partner opnieuw ingesteld) [IP: 82.211.81.151 80] is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/ Sources.gz Subproces gzip gaf de foutcode 1 terug is mislukt
Ophalen van http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/sou rce/Sources.gz Subproces gzip gaf de foutcode 1 terug is mislukt
Pakketlijsten worden ingelezen... Klaar
E: Ophalen van sommige indexbestanden is mislukt, deze zijn of genegeerd, of er zijn oudere versies van gebruikt.
stef@laptopStef:/etc/apt$

```

104 connection reset by peer
subproces gzip returned errorcode 1

i dont know what it can be

---

### Post by lamego on 2006-01-08
The most probable reasons for your problem are:
1) You don't have enough disk space, the disk gets full when downloading the packages list
2) You have network issues and the data gets corrupted during the download

---

### Post by psyone on 2006-01-08
I got it fixed.

I replaced all my http:// with ftp:// and everything was solved.

Here is my current sources.list file (for people who have the same problem)

```
## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.
## You may replace "us" with your country code to get the closest mirror.

deb ftp://archive.ubuntu.com/ubuntu breezy main restricted
deb-src ftp://archive.ubuntu.com/ubuntu breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb ftp://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src ftp://archive.ubuntu.com/ubuntu breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb ftp://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src ftp://security.ubuntu.com/ubuntu breezy-security main restricted

deb ftp://security.ubuntu.com/ubuntu breezy-security universe
deb-src ftp://security.ubuntu.com/ubuntu breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)
deb ftp://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src ftp://archive.ubuntu.com/ubuntu breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb ftp://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src ftp://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb ftp://ubuntu-backports.mirrormax.net breezy-extras main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb ftp://packages.freecontrib.org/ubuntu/plf breezy free non-free
deb-src ftp://packages.freecontrib.org/ubuntu/plf breezy free non-free

```

I still find it strange tough, but you don't hear my complain anymore

ps: thank you for the list socrazy143

---

