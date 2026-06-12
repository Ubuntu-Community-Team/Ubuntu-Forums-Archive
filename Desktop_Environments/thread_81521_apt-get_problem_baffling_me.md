---
title: "apt-get problem baffling me"
date: 2005-10-24
forum: Desktop Environments
---

### Post by red devil on 2005-10-24
Hi,
I've been trying to install mplayer via apt-get; I update apt-get each time (the universe and multiverse repositories are there since I used the new 'add application feature in the Gnome menu in 5.10). Then, when I apt-get install mplayer, I get the following:

steve@ubuntu:~$ su
Password:
root@ubuntu:/home/steve# apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Sources
Fetched 3B in 0s (6B/s)
Reading package lists... Done
root@ubuntu:/home/steve# apt-get install mplayer
Reading package lists... Done
Building dependency tree... Done
Package mplayer is a virtual package provided by:
  mplayer-nogui 1:1.0-pre7cvs20050716-0.1ubuntu9
  mplayer-k6 1:1.0-pre7cvs20050716-0.1ubuntu9
  mplayer-custom 1:1.0-pre5-0.6ubuntu1
  mplayer-586 1:1.0-pre7cvs20050716-0.1ubuntu9
  mplayer-386 1:1.0-pre7cvs20050716-0.1ubuntu9
You should explicitly select one to install.
E: Package mplayer has no installation candidate

So, then I enter: 

root@ubuntu:/home/steve# apt-get install mplayer-586 1:1.0-pre7cvs20050716-0.1ubuntu9
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package 1:1.0-pre7cvs20050716-0.1ubuntu9

So I tried:

root@ubuntu:/home/steve# apt-get install mplayer-386 1:1.0-pre7cvs20050716-0.1ubuntu9
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package 1:1.0-pre7cvs20050716-0.1ubuntu9
root@ubuntu:/home/steve#

I also tried getting Mplayer through the new add apps menu item, but although I can 'see' it in the list, it can't be found by the installer.
What am I doing wrong?
Thanks,
Red Devil

---

### Post by Kyral on 2005-10-24
Try installing just "mplayer-586"

---

### Post by red devil on 2005-10-24
I'll be damned... that worked just fine! Many thanks my friend.
Red Devil

---

