---
title: "Trying to install packages not available in the package manager. Please HELP."
date: 2006-01-20
forum: Desktop Environments
---

### Post by joejac on 2006-01-20
I am using Kubuntu 5.10
I am trying to install packages not available in the package manager:

NVU
Kmymoney

Unfortunately I am new to Linux, so I need advice step by step on how to do this, because I am not familiar with the command line, please be patience and do not assume I know. I appreciate your help in provide me with a step by step procedure.
Sorry but I got lost and headaches searching in the documentation.

Thanks a lot for your help in advance.
Best regards
joejac

---

### Post by GeneralZod on 2006-01-20
Luckily, both of those are actually in the repositories, but maybe you don't have the correct ones enabled.  A good intro (it's pretty much step-by-step) is given by aysiu here:

[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by joejac on 2006-01-20
GeneralZod, thanks a lot.

I got the error:
tecnico@admin:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
tecnico@admin:~$ sudo kwrite /etc/apt/sources.list
Error: "/var/tmp/kdecache-tecnico" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/tmp/kde-tecnico" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/kde-root"
Error: "/tmp/ksocket-tecnico" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/ksocket-root"

I did not understand the error, but the sources.list was opened I copied the links for 5.10 and it worked!
I have now NVU and Kmymoney, incredible, a first class support for an open source product, unbelievable.
I spent a lot more time to thank you than you to reply with the solution, thanks again.

This is a wonderful proyect and community. I have seen a lot of improvements from my last attempt to move to Linux on april 2005, better graphics applications and web authoring tools, Konqueror is very nice also. I still miss some wonderful Win programs but I think I can migrate 2 of my 3 home computers to Linux now.

Best regards
joejac

---

### Post by GeneralZod on 2006-01-21
The errors are unimportant - justs general Kubuntu bugginess :)

I'm very happy to hear that Kubuntu and the community are treating you well and meeting (most of!) your needs :)

Good luck!
Simon

---

### Post by joejac on 2006-01-23
Yes, Ubuntu community is very friendly.

I have one additional question, on the Win world I use KeyNotes, a very nice outliner to organize notes, documentation and more. I understand that in Linux there is Knowit, I have read good comments of it. Unfortunately it seems to be that it is not in any of the repositories.

How can I install Knowit in an easy way?

I understand that trying to compile a program in linux is for gurus, I appreciate any help in order to install this program, an outliner is a very valuable tool for me to organize myself.

Thanks a lot
Regards
joejac

---

### Post by cwaldbieser on 2006-01-23
[QUOTE=joejac]Yes, Ubuntu community is very friendly.

I have one additional question, on the Win world I use KeyNotes, a very nice outliner to organize notes, documentation and more. I understand that in Linux there is Knowit, I have read good comments of it. Unfortunately it seems to be that it is not in any of the repositories.

How can I install Knowit in an easy way?

I understand that trying to compile a program in linux is for gurus, I appreciate any help in order to install this program, an outliner is a very valuable tool for me to organize myself.

Thanks a lot
Regards
joejac[/QUOTE]

I am not familiar with KnowIt, but several other note-taking applications are in the repositories.  Would something like the "tomboy" package be useful to you?

If you really want to compile KnowIt, you should get the .tar.bz2 tarball.  You will also need to 
```

$ sudo apt-get update
$ sudo apt-get kdebase-dev
$ sudo apt-get build essential

```
To get the KDE development headers from the repositories.
Then you unpack the tarball (with ark or file roller or whatever).
Then open a terminal in the folder you unpacked, and
```

$ ./configure
$ make
$ sudo checkinstall -D

```
You will be prompted for what you want to call the new .deb file, etc.  This way, you can uninstall easily if you want to get rid of the package.

---

### Post by sappman2 on 2006-01-28
I'm running into problems trying to do something similar... I'm attempting to install the newest version of KMyMoney (v 8.2.1) from their website using "dpkg -1 *filename*" when the downloaded file is a *.deb file.  Installation halts because there is another package it depends on that doesn't come with it, and I can't seem to find it. It probably has something to do with the fact that I'm on GNOME, KyMyMoney is KDE. ???

Why I'm trying this: The Ubuntu repository version of KMyMoney has a glitch that won't let the help file work. There has been two ugrades since the Ubuntu version came out. Same problem with GNUCash, as well, only it has many more "boo-boo's" that are fixed by newer versions. 

What do I do if I would like to get the "latest-greatest" versions of applications that UBUNTU already suports, but the latest versions do not appear in the repositories?  Can I add other repositories to my "source.list" at will? if so, anything I should be careful of? If not, are there any other scripts or applications that can auto-search, get, install applications *and* their dependencies that are outside Ubuntu's repos?

---

### Post by gingermark on 2006-01-28
[QUOTE=sappman2]What do I do if I would like to get the "latest-greatest" versions of applications that UBUNTU already suports, but the latest versions do not appear in the repositories?  Can I add other repositories to my "source.list" at will? if so, anything I should be careful of? If not, are there any other scripts or applications that can auto-search, get, install applications *and* their dependencies that are outside Ubuntu's repos?[/QUOTE]

Basically, it depends on the program. Adding unnofficial repositories is not recommended as I understand things, but if you do, make sure they are intended for Ubuntu. Adding a Debian repository is a bad idea (or more specifically, having a Debian repository permanently enabled) because of dependency differences between the distros. I have installed some Debian deb files that don't seem to depend on much else and they have worked, but you really need to judge things on a case by case basis.

Backports, plus the addititional repos Kubuntu have been kind enough to provide (for the new versions of KDE and amaroK) are the best way to get the "latest-greatest" versions, but sometimes (like the case of Firefox 1.5) this isn't possible.

If you are looking for a program that isn't in the repositories, search the forums. If you can't find something there, try searching google for a .deb file, but as I say, if it's for Debian you will have to use your own judgement to decide if it is suitable or not.

---

### Post by sappman2 on 2006-01-29
Thank you for your sound advice. Perhaps I just need to be patient & wait for one of our Ubuntu-community's  kind programmers to compile "the latest/greatest" into Ubuntu repositories. I'd love to learn how to help advance Ubuntu myself in this regard, but I have very limited programming experience. (BASIC language only.) I wish I could find time and money to take a linux/unix class. Thanks again.

---

