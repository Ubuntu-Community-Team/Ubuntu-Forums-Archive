---
title: "apt-get"
date: 2005-11-25
forum: Desktop Environments
---

### Post by Draconis on 2005-11-25
Hi to all members am new to forums so please excuse any errors.
I am having trouble using apt-get:confused: 
sudo apt-get install \dir\dir\folder\programm gives error message 
I have downloaded gnucash, extracted to a folder called gnucash.
any advice on how to install would be appreciated.:)

---

### Post by ngnr on 2005-11-25
Hi, 

apt-get installs software located in repositories, so if you want to install gnucash just type:

```
$ sudo apt-get install gnucash
```

and package management system will download & install the software

if you downloaded a .deb or .rpm package try:

```
$ sudo dpkg -i <packagename>.deb
```

for RPM :

```
$ sudo alien -i <packagename>.rpm
```

If you don't want the console try synaptic.

System > Administration > synaptic package manager

good luck

:)

---

### Post by Draconis on 2005-11-26
Thank you for your assistance. I had downloaded a .tar file.
I first used mandrake many years ago, but find Ubuntu far superior. Just need to learn some new ways of doing things. 
I will use the methods tou suggested and post the reults.
Again thank you:)

---

### Post by metoo on 2005-11-27
.tar files are usually source code files. You might need to compile this first.
This can be tricky and requires to install additional software.

Use synaptic to install the gnucash which comes with breezy (if you don't need a newer version than the one from the repository).

If it is not listed, you need to extend your /etc/apt/sources.list file.
The wiki might tell you how to do this and holds an up to date list with the repositories: restricted, universe, multiverse. Otherwise, a quick forum search should give the answer.

---

### Post by Draconis on 2005-12-06
:confused: Thank you for your responses, 
I have scanned the forum and downloaded some guides. I am still expreincing problems.
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list gives me error massage
cannot stat cp /etc/apt/sources.list_bakup

apt-get update downloads quite a few repositaries however 
sudo etc/apt/sources.list_backup /etc/apt/sources.list sudo apt-get update
gives error massage cannot stat no such file

apt-get install gnucash gives error
could not open lock file /var/lib/apt/lists/lock - open (13 permission denied)

I am quite adept at the dreaded Windows and would love to swap to Ubuntu, but am finding it quite frustrating. I carefully follow instructions only to keep getting error messages. Oh well went through the same learning Windows at 52 I will learn Linux.
I hope some one will be able to point me in the right direction.
In the mean time will continue to troll the forums to see what I am able to find.:)

---

### Post by fishbroetchn on 2005-12-06
[QUOTE=Draconis]:confused: Thank you for your responses, 
I have scanned the forum and downloaded some guides. I am still expreincing problems.
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list gives me error massage
cannot stat cp /etc/apt/sources.list_bakup

apt-get update downloads quite a few repositaries however 
sudo etc/apt/sources.list_backup /etc/apt/sources.list sudo apt-get update
gives error massage cannot stat no such file

apt-get install gnucash gives error
could not open lock file /var/lib/apt/lists/lock - open (13 permission denied)

I am quite adept at the dreaded Windows and would love to swap to Ubuntu, but am finding it quite frustrating. I carefully follow instructions only to keep getting error messages. Oh well went through the same learning Windows at 52 I will learn Linux.
I hope some one will be able to point me in the right direction.
In the mean time will continue to troll the forums to see what I am able to find.:)[/QUOTE]


-first of all, make sure you are superuser while installing software. That can be the problem when having a permission problem.
-for apt-get: just open the /etc/apt/sources.list in an editor (eg. vi) and edit the #-marks. Removing them will open the way to download the package-updates
-next procedure is sudo apt-get update
-then audo apt-get upgrade and your system is up to date

hf fishbroetchn

---

### Post by Draconis on 2005-12-06
I will try your suggestion, Thank you.
In the mean time apologies for the long post, but I would like to solve this, as it is the only problem I have:
My attempt at installing from desktop:

draconis@ubuntu:~$ tar -xvzf gnu.tar.gz
tar: gnu.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

My attempt at installing from online repository:

draconis@ubuntu:~$ apt-get install gnucash
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

My attempt at installing from on line repository after following official guide on how to add extra repositories:

draconis@ubuntu:~$ sudo apt-get install gnucash
E: Malformed line 24 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

After typing in new etc/apt/sources.list:

draconis@ubuntu:~$ sudo apt-get update
E: Malformed line 24 in source list /etc/apt/sources.list (dist parse)

After deleting etc/apt/sources.list
draconis@ubuntu:~$ sudo gedit /etc/apt/sources.list
draconis@ubuntu:~$ sudo apt-get update
Reading package lists... Done
draconis@ubuntu:~$ sudo cp /etc/apt-get/sources.list_backup /etc/apt/sources.list sudo apt-get update
cp: `update': specified destination directory does not exist
Try `cp --help' for more information.
draconis@ubuntu:~$  sudo cp etc/apt/sources.list_backup /etc/apt/sources.list
cp: cannot stat `etc/apt/sources.list_backup': No such file or directory

After copying and pasting /etc/apt/sources.list from guide:

 draconis@ubuntu:~$ sudo apt-get install gnucash
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package gnucash

I open /etc/apt/sources.list in terminal. As you can see I always use sudo.
Any assistance will be gratefully accepted.

---

### Post by aysiu on 2005-12-06
[QUOTE=Draconis]:confused: Thank you for your responses, 
I have scanned the forum and downloaded some guides. I am still expreincing problems.
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list gives me error massage
cannot stat cp /etc/apt/sources.list_bakup[/quote] The way you have it written here, you're saying to the computer: "With root privileges make a copy of the file sources.list_backup (which lives in /etc/apt) and call that copy sources.list."

There is no sources.list_backup yet. You need to use this command instead: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
``` That means: "With root privileges make a copy of the file sources.list (which lives in /etc/apt) and call that copy sources.list_backup."

> I carefully follow instructions only to keep getting error messages. Obviously not that carefully (see above). Your best bet is to copy and paste terminal instructions instead of retyping them. Retyping leaves too much room for human error.

---

### Post by Draconis on 2005-12-09
My apologies AYSIU, obviously I am human and make some maistakes. Should have stated that I try tp follow instructions accurately.
However that does not assist me in solving this problem, as the rest of the post shows no matter how I try I cannot download and install. I will retry by cutting and pasting your instructions.
I have also taken what to me is the easy way and used Synaptic and managed to install Gnucash. Now I need find where it is and how to run it.
I began on computers with a Commodore 64, and am qute adept with Windows, so I can usually solve most problems, Linux is just a bit more difficult. 
Again my thanks to all who are willing to give advice to a newbie stumblin' along.

---

### Post by Draconis on 2005-12-09
Thank you for the links, they are the guides I used. I did finally cut and paste the repository listing. As my post shows still no luck.
I know I am doing something wrong, just need to be pointed in the right direstion.

---

### Post by xaos5 on 2005-12-09
your making this really harder then it is, do this since you can't seem to get your repositories right.

1.) download the .deb package from their website:
[http://www.gnucash.org/pub/gnucash/debian/gnucash_1.6.4-1_i386.deb](http://www.gnucash.org/pub/gnucash/debian/gnucash_1.6.4-1_i386.deb)
2.) from command line do this:
cd /path/to/where/you/saved/
sudo dpkg -i gnucash_1.6.4-1_i386

the apt-get error unable to lock means that you probably have synaptics running and it already has the lock.

Like quoted before .tar, .tar.bz2 are usually source code which needs compiling.
.deb is used by debian, ubuntu, knoppix, and any other debian based distro
.rpm is used by mandrivia, redhat, etc.
.ebuild is used by gentoo and possibly others?
.tgz is used by slackware.

---

