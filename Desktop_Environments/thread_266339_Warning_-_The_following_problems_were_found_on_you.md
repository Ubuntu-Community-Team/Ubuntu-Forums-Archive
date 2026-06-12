---
title: "Warning - The following problems were found on your system"
date: 2006-09-27
forum: Desktop Environments
---

### Post by netnut on 2006-09-27
Hi guys,

When I open the software properties I get a dialogue box titled "Warning" followed by this:
> W: Duplicate sources.list entry cdrom://Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531) dapper/main Packages (/var/lib/apt/lists/Ubuntu%206.06%20%5fDapper%20Drake%5f%20-%20Release%20i386%20(20060531)_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531) dapper/restricted Packages (/var/lib/apt/lists/Ubuntu%206.06%20%5fDapper%20Drake%5f%20-%20Release%20i386%20(20060531)_dists_dapper_restricted_binary-i386_Packages)

Now can anyone tell me what this is all about? I am completely new to Linux so I can't make heads or tails of it.

Thanks in advance.
Netnut.

---

### Post by cotcot on 2006-09-27
Put a # (hash) in front of the lines with the CD source in your /etc/apt/sources.list; do "sudo apt-get update" in terminal and I think you will not have the warming anymore. The install CD will not be used anymore to install packages. They will be taken from the other repositories.

---

### Post by Kateikyoushi on 2006-09-27
Well it seems your cd entry has been added two times to your software sources.
Check it in system >> Administration >> Software sources.

---

### Post by netnut on 2006-09-29
Thanks guys... I have edited my sources.list file and the problem seems to have gone. Thanks again.

By the way, I would like to install all there is on the Ubuntu CD... how do I do that? More specifically I have been told that gcc resides on the Ubuntu CD but I don't know how to install that... if I use the synaptic it asks me to download certain things.. which I don't want at this point of time. Also, is there a way to reuse the downloaded packages for installing on other systems?

Regards,
Netnut.

---

