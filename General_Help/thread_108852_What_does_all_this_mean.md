---
title: "What does all this mean?"
date: 2005-12-27
forum: General Help
---

### Post by Duo Maxwell on 2005-12-27
Well this is my 1st real use of linux outside of OS X on my ibook, got it going on a cobbled together P4 a week ago but I've run into some problems, the 1st is that I had a hard restart a few days ago, all seemed right till I opened Synaptic to install some new stuff I was greeted with this:

> W: Couldn't stat source package list [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com") breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
 
What does it all mean? I know my way around a windows or Mac OS machine but I'm really not sure what it wants me to do here yet.

---

### Post by hajk on 2005-12-27
This is a problem that sometimes crops up with an Ubuntu mirror. You might want to remove the "us." mirror prefix in every line of /etc/apt/sources.list, and then try again to update.

Sometimes a mirror problem causes corrupted GPG and file errors. To recover from that, the /var/lib/apt/lists directory can be cleaned out with

cd /var/lib/apt
sudo rm -fr lists
sudo mkdir lists
sudo mkdir lists/partial

Running "sudo apt-get update" once more with a good mirror fixes the problem with the sources.

---

### Post by Thunk on 2005-12-27
Are you sure your sources list is fine? Have you used it before? If not, try this thread:

[http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

### Post by limit223 on 2005-12-27
[QUOTE=hajk]This is a problem that sometimes crops up with an Ubuntu mirror. You might want to remove the "us." mirror prefix in every line of /etc/apt/sources.list, and then try again to update.

Sometimes a mirror problem causes corrupted GPG and file errors. To recover from that, the /var/lib/apt/lists directory can be cleaned out with

cd /var/lib/apt
sudo rm -fr lists
sudo mkdir lists
sudo mkdir lists/partial

Running "sudo apt-get update" once more with a good mirror fixes the problem with the sources.[/QUOTE]


I had the same problem....and all above did the trick after reload and restart synaptic....thanks!

---

