---
title: "Errors when updating or installing"
date: 2006-02-11
forum: Desktop Environments
---

### Post by dizawg on 2006-02-11
Hello all.  I am new to linux and am trying to upgrade and install some things including xine. I did the sudo apt-get upgrade and also update.  I keep getting the following:

 [B]Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)


**W: Couldn't stat source package list [http://u](http://u)**buntu-backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.[/B]


Please help me out.  Thanks

---

### Post by Sutekh on 2006-02-12
Two problems;

Those repositories have **hoary** in them
[QUOTE=dizawg]W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) **hoary**-backports/main Packages
[/QUOTE]
I'm taking that you use Breezy (You posted in the Breezy section, but correct me if I'm wrong), so these repositories won't like that.


Also the mirrormax repositories are obsolete.

Here is a link with up-to-date repositories
[Up-To-Date Repositories - by ]("http://www.psychocats.net/linux/sources.php")[aysiu]("http://www.ubuntuforums.org/member.php?u=21941")

---

