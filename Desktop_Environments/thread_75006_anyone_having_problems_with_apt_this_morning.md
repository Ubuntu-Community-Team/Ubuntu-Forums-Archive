---
title: "anyone having problems with apt this morning?"
date: 2005-10-13
forum: Desktop Environments
---

### Post by sal on 2005-10-13
anyone ells having problems with apt-get this morning?
i'm assuming because everyone is hitting the servers hard with the downloads of the iso discs and the apt-get upgrade apt-get dist-upgrade's going on they must be slowing to a crawl.

i've been running breezy for a few weeks now, tryed to apt-get dist-upgrade this morning and it kept failing.

im thinking because of the load on the servers. anyone ells with this issue?

---

### Post by machaval on 2005-10-13
I was having the same I think problem when when i try a new installation... It freezed when downloading some stuff from the repositories....

---

### Post by joshuai on 2005-10-13
[QUOTE=sal]i'm assuming because everyone is hitting the servers hard with the downloads of the iso discs and the apt-get upgrade apt-get dist-upgrade's going on they must be slowing to a crawl.[/QUOTE]

I'm sure that's all it is.  I haven't even started the dist-upgrade yet (forgot to refresh before I hit upgrade).  Just doing a few VLC packages now, and it's crawling through.  I'm sure it'll get better...eventually. :) 

Make ISOs torrent-only for the first week of release. :evil: 

I kid.

---

### Post by TonyDTV on 2005-11-07
Newbie here,how does one use the apt-get command?? Been running Kubuntu 5.10 using a AMD64 machine for a few days and so far Its "different"? Thanks

---

### Post by Navyblue on 2005-11-08
[QUOTE=TonyDTV]Newbie here,how does one use the apt-get command?? Been running Kubuntu 5.10 using a AMD64 machine for a few days and so far Its "different"? Thanks[/QUOTE]

First you gotta update your package list to the latest one
sudo apt-get update

To install
sudo apt-get install packagename

To do system wide upgrade
sudo apt-get dist-upgrade

To uninstall
sudo apt-get remove packagename

You can also use synaptic which is a GUI front end to apt.

---

### Post by TonyDTV on 2005-11-08
Sorry, but I need a walk thru. Where do I type the command "sudo apt-get ..."in KDE?? Thanks.

---

### Post by Cufishing on 2005-11-08
[QUOTE=sal]anyone ells having problems with apt-get this morning?
i'm assuming because everyone is hitting the servers hard with the downloads of the iso discs and the apt-get upgrade apt-get dist-upgrade's going on they must be slowing to a crawl.

i've been running breezy for a few weeks now, tryed to apt-get dist-upgrade this morning and it kept failing.

im thinking because of the load on the servers. anyone ells with this issue?[/QUOTE]
I had same-same last night. The US repositories were failing to acknowledge.

---

### Post by Cufishing on 2005-11-08
[QUOTE=TonyDTV]Sorry, but I need a walk thru. Where do I type the command "sudo apt-get ..."in KDE?? Thanks.[/QUOTE]
In KDE it's called 'Konsole' look for it, and other great features from your KDE panel.

Also, here is the quick guide.
[http://kubuntu.org/docs/kquickguide/C/index.html](http://kubuntu.org/docs/kquickguide/C/index.html)

---

### Post by Ameet on 2005-11-08
I have been having a lot of trouble with updating since I got Breezy.  This has been going on for a week regardless of time of day, whether I use Synaptic or use a shell command - 
```
sudo apt-get update
```
I get a lot of errors like -
> Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_ Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.


(Others are having the same problem, see [http://ubuntuforums.org/showthread.php?t=83728](http://ubuntuforums.org/showthread.php?t=83728))

Does anybody have any ideas what is going on?

---

