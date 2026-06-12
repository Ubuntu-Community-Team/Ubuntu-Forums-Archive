---
title: "how to install vmware 8.0 in 11.10"
date: 2012-02-23
forum: Desktop Environments
---

### Post by deepantjain on 2012-02-23
Hello All,

First post here officially, I've been using Linux for about a year now, and I always find myself at the Ubuntu forums troubleshooting. Well, I've come across a problem that I can't find any good solutions to along the internet. So, here I am.

I am running Ubuntu 11.10

Kernel version 3.0.0-12.


First, I had been trying the free version of VMWare Workstation 8. Two things happen:

a) (vmware-installer.py:1757): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
(repeats itself 3 times)

b) A dialog window pops up from VMWare Installer that says, "One or more of your processors does not have the necessary 64-bit extensions to run VMware virtual machines."

I am trying to run the i386 (32bit) version of this as well, so I don't know why its giving me an error about 64 bit.

[EDIT]: Installation Requirements

64-bit x86 CPU

[http://www.vmware.com/support/player...n_Requirements](http://www.vmware.com/support/player...n_Requirements)

*oops* Ok. anyone got any solution on the VMWare Player then?

------------------

Then I tried VMWare Player 3.15 because I heard maybe there was some compatibility with 4.0 and the new release of Ubuntu 11.10. Well, no avail there. I had a similar issue and went through a bunch of troubleshooting and tried the patch over at [http://reformedmusings.wordpress.com...rnel-3-0-0-12/](http://reformedmusings.wordpress.com...rnel-3-0-0-12/).

-------------------

So now, I'm stuck with no VMware. And I can't figure out why I'm getting a bunch of GtK errors. Did I compile my GtK library wrong? What do I need to know?

Thanks for educating me,

---

### Post by cbanakis on 2012-02-23
Are you attached to VMware?

I use VirtualBox (In the software center)

I have not used anything else, but it seems to work perfect, and very easy to use.
Not sure what any other program could have to offer that would make it better.

---

### Post by linuxnas on 2012-02-23
> **cbanakis said:**
> Are you attached to VMware?

I use VirtualBox (In the software center)

I have not used anything else, but it seems to work perfect, and very easy to use.
Not sure what any other program could have to offer that would make it better.

I gave up VMware for VirtualBox for many years. VirtualBox at ubuntu is very stable and easy to use. worth try it out

---

