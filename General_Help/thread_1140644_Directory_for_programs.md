---
title: "Directory for programs"
date: 2009-04-27
forum: General Help
---

### Post by ztangg on 2009-04-27
Simple question for u all.

I have just downloaded Songbird. Now I wonder where you usually install user programs like this.

I am very very new to linux.

---

### Post by mb_webguy on 2009-04-27
Here's a brief overview of the Linux [Filesystem Hierarchy Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard").

Programs installed through the repositories are located in /usr, with executables in /usr/bin, and application data in /usr/share.  Programs you've installed locally, such as by compiling from source, are located in /usr/local, with executables in /usr/local/bin, and application data in /usr/local/share.

Some programs that use binary installers will install themselves in the /opt directory.

Basically, most programs are located somewhere in /usr, but you may rarely find one in /opt.

---

