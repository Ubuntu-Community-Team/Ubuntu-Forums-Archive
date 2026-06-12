---
title: "Vmware player does not install"
date: 2006-07-13
forum: Desktop Environments
---

### Post by Matthai on 2006-07-13
I have Ubuntu Dapper. Upgraded, so I have new kernel.

uname -r
2.6.15-26-386

so...

sudo apt-get install vmware-player

and it is not working. It seems to me that the reason is that vmware installs kernel modules.

I think this one:
vmware-player-kernel-modules-2.6.15-23


But for my kernel there is no modules. So that could be the reason why dpkg return error while installing?

If I try to install vmpware player from the official website, I get this:
 sudo ./vmware-install.pl A previous installation of VMware software has been detected.

Failure

Execution aborted.



ANY idea?

---

### Post by luckylucky on 2006-07-14
I just did a fresh reinstall of Ubuntu 6.06... actually numerous reinstalls because I thought that perhaps I've screwed up something since I couldn't get vmware player working.  I've been beating my head on the wall trying to figure out why it worked before (as little as a week ago) but now it's totally fubared. ](*,)  

From posts I've come across I've learned that something has changed from the online repositories, and that many other people are having the same problem.  Now I realize that I'm not an idiot doing something wrong, but that somehow Ubuntu has gotten messed up and vmware player no longer works.

I've lost now two full days of work (and income) due to this.  VMware player is an absolutely critical need for me to having working on Ubuntu.  I'm an absolute Ubuntu lover/fan, but unfortunately if I can't get this matter fixed I might have to jump ship to another linux distro, which is sad as I prefer Ubuntu to all others.  :( 

Can somebody PLEASE figure out what the heck is going on and provide a fix???  I, and many others out there are desperately needing a fix to this issue.

Thanks to any techie-saviors out there who can help to get a fix for this.

LuckyLucky

---

### Post by theturtlemoves on 2006-07-14
The problem is that the updated packages for vmware-player-kernel-modules have not made it to the repository. The version available from the repository is 2.6.15-10. The most recent kernel from Ubuntu is 2.6.15-26.

There are two fixes, neither of which I have tried yet. If you still have the 2.6.15-10 kernel on your system, boot into that and use it to install vmware-player. It will then work only under that kernel.

Otherwise, you could either wait for the next version of the vmware-player-kernel-modules to be released (hopefully soon) or you could download and compile the modules yourself. 

I'm about to try compiling them from the source package available in the official repositories. If that doesn't work, you'll have to get the source from the vmware site and compile that instead.

Hope this helps - I'll keep you posted.

---

### Post by XaeroDegreaz on 2006-08-30
Please read my other post, it solves this problem.

[http://www.ubuntuforums.org/showthread.php?t=236491&page=2](http://www.ubuntuforums.org/showthread.php?t=236491&page=2)

---

### Post by GadgetsGuy on 2006-08-30
You do know that VMWare SERVER is now available for FREE?

why mess around with a single application appliance, when you can run multiple applications with VMWare server.

I have this setup on 4 machines running Ubuntu now, and I am veery happy with the performance.

---

### Post by NZ-Wanderer on 2006-10-20
Wanna do us (me) a favour and tell us which file you downloaded and how you got it to install please?? (not used to installing anything out of synaptic) :)

> **GadgetsGuy said:**
> You do know that VMWare SERVER is now available for FREE?
why mess around with a single application appliance, when you can run multiple applications with VMWare server.
I have this setup on 4 machines running Ubuntu now, and I am veery happy with the performance.

---

