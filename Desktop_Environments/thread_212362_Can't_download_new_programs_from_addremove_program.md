---
title: "Can't download new programs from add/remove programs"
date: 2006-07-09
forum: Desktop Environments
---

### Post by tylerjroach on 2006-07-09
I was messing with the repositories and adding new ones to apt-get, but then now when I go to add/remove applications, on every program I want to download  it says:____ is not available in any software channel. The application might not support your system architecture. I think it has to do with the repositories or something. If someone could help me by giving me the default look of what apt-get is supposed to be or do something else to fix this it would be greatly appreciated.

---

### Post by Dr. Nick on 2006-07-09
Post up your sources.list file using

cat /etc/apt/sources.list

or make a new one from here
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

That file may be messed up now, once you edit it you need to run

sudo apt-get update

---

### Post by tylerjroach on 2006-07-10
Here is my apt-get list during apt-get update:

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release [30.9kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release [19.6kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [24.5kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [14B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [14B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [7105B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [974B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [902B]
Fetched 115kB in 1s (67.1kB/s)
Reading package lists... Done

---

### Post by lordlollo on 2006-07-10
Can't you download anything even after the update?

---

