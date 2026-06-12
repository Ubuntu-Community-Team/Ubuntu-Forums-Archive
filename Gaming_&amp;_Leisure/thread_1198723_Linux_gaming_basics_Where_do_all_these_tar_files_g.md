---
title: "Linux gaming basics: Where do all these tar files go?"
date: 2009-06-27
forum: Gaming &amp; Leisure
---

### Post by mantisdolphin on 2009-06-27
Okay, I've got Ubuntu 9.04 running on my Dell 3.4Ghz/3GbRAM machine.  I wanted to download Warzone 2100.  I downloaded the tarball from [here]("https://sourceforge.net/project/downloading.php?group_id=142032&filename=warzone2100-2.2.1.tar.bz2&a=89985485").  

Then I found the following package handling command [here]("http://developer.wz2100.net/wiki/LinuxCompileGuide"): 

```
apt-get install subversion build-essential automake flex bison
```

I ran this "apt-get install" command and ended up with files in /usr/share/apt-install/desktop (where a Warzone config file now resides, though right-clicking for the context menu does not give me the option to edit it) and in /usr/share/apt-install/icons.  

Then I tried to use Ubuntu's archive handling program to unpack the previously downloaded tarball "warzone2100-2.2.1.tar.bz2".  I couldn't put it in the previous directory (/usr/share/apt-install...), because I didn't have root permission (and I don't see a place in the archive program to ask to be prompted for root password), so I unpacked the tarball to my user directory, where the file was unpacked to its own directory: /home/me/warzone2100-2.2.1.

Okay, I'm ready to check out the game!  No I'm not.  Here's the file list and I'm not sure where the "executable" is.  How do I "launch" the game?

/home/me/warzone2100-2.2.1/build_tools
/home/me/warzone2100-2.2.1/data
/home/me/warzone2100-2.2.1/doc
/home/me/warzone2100-2.2.1/icons
/home/me/warzone2100-2.2.1/lib
/home/me/warzone2100-2.2.1/m4
/home/me/warzone2100-2.2.1/pkg
/home/me/warzone2100-2.2.1/po
/home/me/warzone2100-2.2.1/src
/home/me/warzone2100-2.2.1/win32
/home/me/warzone2100-2.2.1/aclocal.m4
/home/me/warzone2100-2.2.1/AUTHORS
/home/me/warzone2100-2.2.1/autogen.sh
/home/me/warzone2100-2.2.1/ChangeLog
/home/me/warzone2100-2.2.1/config.guess
/home/me/warzone2100-2.2.1/config.h.in
/home/me/warzone2100-2.2.1/config.rpath
/home/me/warzone2100-2.2.1/config.sub
/home/me/warzone2100-2.2.1/configure
/home/me/warzone2100-2.2.1/configure.ac
/home/me/warzone2100-2.2.1/COPYING
/home/me/warzone2100-2.2.1/COPYING.NONGPL
/home/me/warzone2100-2.2.1/COPYING.README
/home/me/warzone2100-2.2.1/depcomp
/home/me/warzone2100-2.2.1/install-sh
/home/me/warzone2100-2.2.1/Makefile.am
/home/me/warzone2100-2.2.1/Makefile.in
/home/me/warzone2100-2.2.1/missing


Clearly I am clueless.  WTF am I doing wrong?  Where is my basic misunderstanding of how to install this game?  Yes, I've searched the forums on installing the game.  I am not trying to be a PITA.  Why won't the Applications / Games menu auto-update?  I truly hate to say this but even Windows 95 updated your programs menu with newly installed games and apps.  Argh.

Thanks in advance!

---

### Post by Blood//Stain//Child on 2009-06-27
Why don't you just install it from Add/Remove?

---

### Post by philcamlin on 2009-06-27
go to the install.sh and open in terminal :)

---

### Post by Grishka on 2009-06-27
heh, source tars are for compiling software, usually you don't wanna do that as a casual gamer. get Warzone2100 .deb packages [from GetDeb](http://www.getdeb.net/app/Warzone2100) for an easy installation of the newest version.

---

### Post by mantisdolphin on 2009-06-27
Haha.  Thank you.  I thought the .deb game packages in Add/Remove were just for mini-games (cards, iagno, mines, that sort of stuff).  I didn't have a lot of confidence in that approach either: I'd downloaded Lgeneral from there, ran the game, and couldn't figure out how to get started.  

Okay, I'm a tard. It's weird, I pursue every stupid angle I can to find my own workaround before posting to a forum for help, but maybe I need to cut bait sooner.

@philcamlin: Thanks for the suggestion.  I sniffed around that .sh file, right clicking, clicking it, etc., but couldn't get anything going.  I tried "run" (nothing happened) but not "run in terminal."

---

