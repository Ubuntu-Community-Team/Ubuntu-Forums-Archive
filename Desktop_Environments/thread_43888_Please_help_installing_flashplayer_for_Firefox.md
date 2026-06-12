---
title: "Please help installing flashplayer for Firefox"
date: 2005-06-23
forum: Desktop Environments
---

### Post by braveerudite on 2005-06-23
I did this: [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

Then this: [http://www.ubuntuguide.org/#flash-mozilla](http://www.ubuntuguide.org/#flash-mozilla)

Then got this:

jok3r@ubuntu:~$ sudo apt-get install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe  Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_ binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/u niverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-secu rity_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_bi nary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dist s_hoary-backports_main_binary-amd64_Packages) - stat (2 No such file or director y)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_ dists_hoary-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_multiverse_binary-amd64_Packages) - stat (2 No such file  or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_restricted_binary-amd64_Packages) - stat (2 No such file  or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_h oary-extras_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dis ts_hoary-extras_universe_binary-amd64_Packages) - stat (2 No such file or direct ory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_d ists_hoary-extras_multiverse_binary-amd64_Packages) - stat (2 No such file or di rectory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_d ists_hoary-extras_restricted_binary-amd64_Packages) - stat (2 No such file or di rectory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe  Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_ binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/u niverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-secu rity_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_bi nary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dist s_hoary-backports_main_binary-amd64_Packages) - stat (2 No such file or director y)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_ dists_hoary-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_multiverse_binary-amd64_Packages) - stat (2 No such file  or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.ne t_dists_hoary-backports_restricted_binary-amd64_Packages) - stat (2 No such file  or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_h oary-extras_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dis ts_hoary-extras_universe_binary-amd64_Packages) - stat (2 No such file or direct ory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_d ists_hoary-extras_multiverse_binary-amd64_Packages) - stat (2 No such file or di rectory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary -extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_d ists_hoary-extras_restricted_binary-amd64_Packages) - stat (2 No such file or di rectory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package flashplayer-mozilla


I am using the AMD 64 Ubuntu version ](*,)

---

### Post by Noddy on 2005-06-23
Did you do
```
sudo apt-get update
```after configuring the extra repositories?

Updating from within Firefox failed for me and although I've managed to install Flash using the ubuntuguide method, it doesn't seem to work properly.

---

### Post by braveerudite on 2005-06-24
[QUOTE=Noddy]Did you do
```
sudo apt-get update
```after configuring the extra repositories?

Updating from within Firefox failed for me and although I've managed to install Flash using the ubuntuguide method, it doesn't seem to work properly.[/QUOTE]


I found out today that there is no flashplayer pluggin for Mozilla Firefox runnig  Linux 64.... amazing..... If anyone finds a plugin let me know plz

---

