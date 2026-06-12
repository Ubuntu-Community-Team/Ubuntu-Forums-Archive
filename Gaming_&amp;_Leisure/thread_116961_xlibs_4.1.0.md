---
title: "xlibs 4.1.0?"
date: 2006-01-13
forum: Gaming &amp; Leisure
---

### Post by MrChips on 2006-01-13
xlibs is no longer a part of Ubuntu (Breezy) correct?.... or is there a substitute?

Trying to install Cedega, terminal states following:

j@ubuntu:~$ cd Desktop
j@ubuntu:~/Desktop$ sudo dpkg -i cedega_5.0.1_i386.deb
(Reading database ... 63492 files and directories currently installed.)
Preparing to replace cedega 5.0.1 (using cedega_5.0.1_i386.deb) ...
Unpacking replacement cedega ...
dpkg: dependency problems prevent configuration of cedega:
 cedega depends on xlibs (>> 4.1.0); however:
  Package xlibs is not installed.
dpkg: error processing cedega (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cedega

I know it looks like a second install, and it is...with the same results.  So I go to their forums for answers...they say "apt-get xlibs"
Here's what I get....

j@ubuntu:$ sudo apt-get install xlibs
Reading package lists... Done
Building dependency tree... Done
Package xlibs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  xkeyboard-config libxft1
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package xlibs has no installation candidate

And here I am.  What is the solution for getting xlibs to therefore get Cedega to work?

---

### Post by leech on 2006-01-14
It's there... not sure why your apt is having issues with it.

[http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77_all.deb) there is a direct download link, just download it and run 'sudo dpkg -i xlibs_6.8.2-77_all.deb'

Leech

---

### Post by MrChips on 2006-01-14
I'm not sure either...But your link did the trick! :) 
Cedega is installed and running.

I'm not sure why it was not gathered during my updates.  I may be having issues with repository access.

Thanks!:cool:

---

### Post by livecdobsessed on 2009-04-30
> **leech said:**
> It's there... not sure why your apt is having issues with it.

[http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77_all.deb) there is a direct download link, just download it and run 'sudo dpkg -i xlibs_6.8.2-77_all.deb'

Leech
leech
your link is broken and i have the same problem. please fix.

---

