---
title: "How to change from desktop to server?"
date: 2010-01-27
forum: Desktop Environments
---

### Post by Poloperson57 on 2010-01-27
Hi,
 
Sorry for the basic question, but I'm very new to Linux.
 
 
If I have installed ubuntu v9.10 desktop for example, what are the steps I need to go through to convert this to a server version?
 
I understand the Kernel for the server is different to that of the desktop. Is there a stragihtforward way to change the kernel as well?
 
Thanks

---

### Post by nerdy_kid on 2010-01-27
```

sudo apt-get remove ubuntu-desktop
sudo apt-get autoremove

```
and then to the server kernel, i think would be this:
```

sudo apt-get install linux-server

```

all you get is a commandline, and if your are new to linux the LAST thing i would be doing is trying out a server version.  Maybe if you had windows server experience, but i still wouldnt do it.

---

### Post by mcduck on 2010-01-27
Also keep in mind that the desktop version is capable of running all the same server software as the server version is. The only difference between the two versions is what packages are installed out-of-the-box. Technically they are both exactly the same Ubuntu. You can install any desktop aps you want on server version, and any server stuff you want on the desktop version.

So unless you are low on resources there is no reason to remove the desktop stuff from your system. Just install whatever server apps you want.

(you can of course also install the server kernel, but unless the machine really is intended for some heavy server use that won't give you any benefits. Both kernels are capable of running exactly the same stuff, the difference is how they balance with different tasks. Desktop kernel is optimized for all normal computer usage from desktop use to server use, while server kernel is optimized for running lots and lots of background tasks.)

---

### Post by Devi1903 on 2010-01-27
When i do a server i usually just use the desktop version. Unless i am doing a server not requiring gui. I don't know about others, but i hope they add some nice server features into the server edition in the near future.

---

### Post by doas777 on 2010-01-27
desktop ver = server ver + gnome & apps. there is no special kernel or drivers or subsystems... its the exact same system, but with a GUI

---

### Post by Poloperson57 on 2010-01-28
Thank you all for the replies. Very informative.
 
nerdy_kid. Thanks for those pointers, and you've answered what I didn't know, and this is the Kernel issue. As for diving straight in to server....I'll be fine, dont worry. ;)
 
It's interesting to see though that there are some conflicting views on the Kernel.  I always thought that the kernels were different, in that the server version was optimised for server type activities, and the desktop was optimized for graphical type apps.
 
As I am building a LAMP server, I really do want the server kernel, hence my question. but I see that DOAS777 is of the view that there is no difference in the kernel?   Has there been a change then in later versions of Ubuntu?
 
I expect a number of you will be asking the question, why dont I just install the server version?  .....well that's another loooooong story which I'll bore you with if you like. But for now lets just say I have to install desktop first.
 
Thanks for the contributions  so far anyway.  I look forward to finding out more about kernel versions.

---

### Post by doas777 on 2010-01-28
there is no server kernel for now, though people have talked about forking a "desktop kernel" in recent years ( [http://www.linux.com/archive/feed/119256](http://www.linux.com/archive/feed/119256) ), but ultimately, nothing has been done. 

now there are multiple distro's of the kernel (ubuntus kernel is not mainstream for instance) so there can be choices to be made, but not desktop vs server. the kernel is one-size-fits-all; it;s the software package around it that makes the differance between server and desktop distros (mostly just the inclusion of x and gnome/kde/xfce/etc).

---

### Post by xifer on 2010-01-28
Kernel tuning is what may be required when you get your services up.

Thinks like max process memory space, number of IPC slots, file system buffers etc etc etc,

have a look at sysctl and numerous guides around on the net to get you started - once you find out what your requirements are.

---

### Post by Seq on 2010-01-28
> **doas777 said:**
> desktop ver = server ver + gnome & apps. there is no special kernel or drivers or subsystems... its the exact same system, but with a GUI

You're correct, except about the kernel. Desktop installs use the -generic kernel, and there is indeed a -server kernel. I believe it is 64-bit only now, apparently there is not enough of a reason for a special 32-bit server kernel. For 32-bit systems with the need (and hardware support) there is a -generic-pae kernel for large memory support, though I'm not sure if 32-bit server install discs use it by default. There is also a -virtual targeted at virtual machines.

There are only a few differences between the different flavours. For example, -generic-pae only enables pae support, which -generic doesn't have. If you're interested, run `apt-get source linux` and run through the debian directory. It has all the configuration for the different kernel flavours built.

You can view the different linux-image packages available in Karmic on launchpad: [Linux source package]("https://edge.launchpad.net/ubuntu/+source/linux/2.6.31-14.48") info page

That said, if you just want to try out some server stuff on your desktop, you'll probably have a much more enjoyable experience with the default kernel you're already using since it was configured with desktops in mind.

Interestingly, while researching this it appears that Lucid doesn't currently have a -server kernel as part of the 'linux' source package. I'll have to go through the server team logs and see if things are changing.

---

### Post by Seq on 2010-01-28
> **Seq said:**
> There are only a few differences between the different flavours.

There is actually a page for [Ubuntu Server Edition Kernel Features]("http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel"). It lists the differences.
> 
[LIST]
[*]The Server Edition uses the Deadline I/O scheduler instead of the CFQ scheduler used by the Desktop Edition.
[*]Pre-emption is turned off in the Server Edition.
[*]The timer interrupt is 100 Hz in the Server Edition and 250 Hz in the Desktop Edition.
[*]The Server Edition is optimised for i686 processors while the Desktop Edition is optimised for both the i586 and i686.
[*]Virtualization is better supported in the Server Edition through the enabling of IPC namespaces.
[*]Multiple routing tables for the IPv6 protocol are also supported in the Server Edition.
[*]For 32-bit systems the Server Edition is configured to use PAE which allows addressing up to 64GB of memory while the Desktop Edition is configured for 4GB.
[*]When running a 64-bit version of Ubuntu on 64-bit processors you are not limited by memory addressing space.
[/LIST]



---

### Post by Millie.T.Cook on 2010-01-28
Thanks to all the responses. I learned quite a bit.

---

