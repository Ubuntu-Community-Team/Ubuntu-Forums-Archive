---
title: "Installing a bittorrent client in Xebian 1.1.4"
date: 2008-08-09
forum: Debian
---

### Post by melat0nin on 2008-08-09
Hi all

I have a working Xebian system on my Xbox (v 1.1.4).  I can use apt-get etc to install stuff.

I tried installing Transmission using apt-get install, but it wanted to install 70mbs of other stuff (about 60-70 other packages) and when I said yes to this, there was all kinds of extra stuff happening like services being stopped and whatnot. I think it was essentially trying to upgrade to etch.

I'm pretty sure this will have broken my Xebian installation, which isn't a problem because I can reinstate it quite easily.

Ideally I would like to install Deluge (or any other decent BT client with a web ui).  How would I go about doing this without 'upgrading' and thus breaking my install? Should I compile from source? The .debs on the Deluge website are for Lenny and SID only so I don't want to try them without proper advice first.

Any help would be much appreciated :)

---

### Post by TenPlus1 on 2008-08-09
Why not go for something in console like rTorrent, it works just as well as Transmission/Deluge and docs can be found here:

[http://www.digipedia.pl/man/rtorrent.1.html](http://www.digipedia.pl/man/rtorrent.1.html)

---

### Post by melat0nin on 2008-08-09
> **TenPlus1 said:**
> Why not go for something in console like rTorrent, it works just as well as Transmission/Deluge and docs can be found here:

[http://www.digipedia.pl/man/rtorrent.1.html](http://www.digipedia.pl/man/rtorrent.1.html)

Thanks for the suggestion. I keep getting these confusing questions when I try to install it though:

```

xebian:/home/live# apt-get install rtorrent
Reading Package Lists... Done
Building Dependency Tree... Done
The following extra packages will be installed:
  gcc-4.1-base libc6 libc6-dev libcurl3 libgcc1 libidn11 libkrb53 libncurses5
  libncurses5-dev libsigc++-2.0-0c2a libssl0.9.8 libstdc++6 libtorrent9
  locales tzdata
Suggested packages:
  glibc-doc libcurl3-gssapi libldap2-dev krb5-doc krb5-user
The following packages will be REMOVED:
  base-config
The following NEW packages will be installed:
  gcc-4.1-base libsigc++-2.0-0c2a libssl0.9.8 libstdc++6 libtorrent9 rtorrent
  tzdata
The following packages will be upgraded:
  libc6 libc6-dev libcurl3 libgcc1 libidn11 libkrb53 libncurses5
  libncurses5-dev locales
9 upgraded, 7 newly installed, 1 to remove and 378 not upgraded.
Need to get 18.1MB of archives.
After unpacking 10.9MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://ftp.at.debian.org stable/main tzdata 2007k-1etch1 [355kB]
Get:2 http://ftp.at.debian.org stable/main libc6-dev 2.3.6.ds1-13etch7 [2718kB]
Get:3 http://ftp.at.debian.org stable/main locales 2.3.6.ds1-13etch7 [4020kB]  
Get:4 http://ftp.at.debian.org stable/main libc6 2.3.6.ds1-13etch7 [4700kB]    
Get:5 http://ftp.at.debian.org stable/main gcc-4.1-base 4.1.1-21 [199kB]       
Get:6 http://ftp.at.debian.org stable/main libgcc1 1:4.1.1-21 [21.7kB]         
Get:7 http://ftp.at.debian.org stable/main libncurses5-dev 5.5-5 [1396kB]      
Get:8 http://ftp.at.debian.org stable/main libncurses5 5.5-5 [300kB]           
Get:9 http://ftp.at.debian.org stable/main libstdc++6 4.1.1-21 [294kB]         
Get:10 http://ftp.at.debian.org stable/main libsigc++-2.0-0c2a 2.0.17-2 [33.3kB]
Get:11 http://ftp.at.debian.org stable/main libssl0.9.8 0.9.8c-4etch3 [2717kB] 
Get:12 http://ftp.at.debian.org stable/main libidn11 0.6.5-1 [116kB]           
Get:13 http://ftp.at.debian.org stable/main libkrb53 1.4.4-7etch6 [408kB]      
Get:14 http://ftp.at.debian.org stable/main libcurl3 7.15.5-1etch1 [168kB]     
Get:15 http://ftp.at.debian.org stable/main libtorrent9 0.10.4-1 [293kB]       
Get:16 http://ftp.at.debian.org stable/main rtorrent 0.6.4-1 [328kB]           
Fetched 18.1MB in 50s (361kB/s)                                                
Reading changelogs... Done
apt-listchanges: Mailing root: apt-listchanges: news for xebian.localdomain.local
2008-08-09 11:39:45 1KRkvJ-0000Zw-66 Cannot open main log file "/var/log/exim4/mainlog": Permission denied: euid=101 egid=101
2008-08-09 11:39:45 1KRkvJ-0000Zw-66 <= root@xebian.localdomain.local U=root P=local S=1152
2008-08-09 11:39:45 1KRkvJ-0000Zw-66 Cannot open main log file "/var/log/exim4/mainlog": Permission denied: euid=101 egid=101
exim: could not open panic log - aborting: see message(s) above
Preconfiguring packages ...
(Reading database ... 35816 files and directories currently installed.)
Removing base-config ...
Selecting previously deselected package tzdata.
(Reading database ... 35708 files and directories currently installed.)
Unpacking tzdata (from .../tzdata_2007k-1etch1_all.deb) ...
Replacing files in old package libc6 ...
Preparing to replace libc6-dev 2.3.2.ds1-22 (using .../libc6-dev_2.3.6.ds1-13etch7_i386.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace locales 2.3.2.ds1-22 (using .../locales_2.3.6.ds1-13etch7_all.deb) ...
Unpacking replacement locales ...
Preparing to replace libc6 2.3.2.ds1-22 (using .../libc6_2.3.6.ds1-13etch7_i386.deb) ...

Name Service Switch update in the C Library: pre-installation question.

Running services and programs that are using NSS need to be restarted,
otherwise they might not be able to do lookup or authentication any more.
The installation process is able to restart some services (such as ssh or
telnetd), but other programs cannot be restarted automatically.  One such
program that needs manual stopping and restart after the glibc upgrade by
yourself is xdm - because automatic restart might disconnect your active
X11 sessions.

Known packages that need to be stopped before the glibc upgrade are:
        xdm kdm gdm postgresql xscreensaver

This script detected the following installed services which must be
stopped before the upgrade:
        xdm

If you want to interrupt the upgrade now and continue later, please
answer No to the question below.

Do you want to upgrade glibc now? [Y/n] 

```

My steps were:
1) apt-get update
2) apt-get install rtorrent

I think Xebian is very out of date, but all I want to do is install one or two BT packages (nothing exotic!).  Is there some way of getting round this stuff?

I've left it at the above prompt, pending any replies!

---

### Post by melat0nin on 2008-08-09
> **TenPlus1 said:**
> Why not go for something in console like rTorrent, it works just as well as Transmission/Deluge and docs can be found here:

[http://www.digipedia.pl/man/rtorrent.1.html](http://www.digipedia.pl/man/rtorrent.1.html)

I've managed to get rTorrent working well, but I'd ideally like a web gui.  I've read about wTorrent but I've no idea how to install it.

Every time I try install something remotely graphical, I get a load of stuff about having to upgrade 60-70 packages.  This takes ages and inevitable fails, citing things like /usr/X11R6/bin cannot be deleted etc etc.

Ideally I just want a half decent BT client with a web interface running on top of vanilla Xebian.  Nothing flash, just functional.

Would compiling from source avoid the shitstorm that happens every time I try to install anything other than rtorrent or bittorrent from the repos?

---

