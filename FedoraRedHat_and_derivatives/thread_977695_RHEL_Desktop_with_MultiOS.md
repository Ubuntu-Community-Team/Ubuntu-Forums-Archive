---
title: "RHEL Desktop with MultiOS"
date: 2008-11-10
forum: Fedora/RedHat and derivatives
---

### Post by twade on 2008-11-10
I have an application that "requires" RHEL Desktop with MultiOS option.  I'm not entirely sure what the MultiOS option is other than it allows virtualization. Is it just a VMware package, something like VirtualBox or something entirely different.  Also is it possible to get something similar with Fedora or CentOS.
Thanks.

---

### Post by igknighted on 2008-11-10
Is that a technical requirement?  Or does running it on other OS's just void any support/warranty you have?

---

### Post by twade on 2008-11-10
I think it is more of a soft technical requirement, and there really isn't much support/warranty to worry about.  The installation instructions and scripts just assume that particular OS without mentioning why.  I'll probably just try a CentOS install and see what happens.  Downtime on the machine is an issue so I'm trying to figure out what might be involved and whether it would just be a dead end before I start.

---

### Post by igknighted on 2008-11-10
You can change the name in a centos release to trick the system into thinking it is RHEL, which it is for all intents and purposes.

---

### Post by twade on 2008-11-10
Thanks, for the useful tip.  You wouldn't happen to know what the "MultiOS option" includes (vs just standard RHEL Desktop)?  It sounds something like VMware, but apparently it's not VMware.

---

### Post by cardinals_fan on 2008-11-10
> **twade said:**
> Thanks, for the useful tip.  You wouldn't happen to know what the "MultiOS option" includes (vs just standard RHEL Desktop)?  It sounds something like VMware, but apparently it's not VMware.
[http://www.redhat.com/promo/streamline/Virtualization/?intcmp=70160000000HZNu](http://www.redhat.com/promo/streamline/Virtualization/?intcmp=70160000000HZNu) ?

EDIT: [http://www.redhat.com/rhel/desktop/details/](http://www.redhat.com/rhel/desktop/details/)

---

### Post by smartboyathome on 2008-11-10
I think MultiOS is basically Xen specialised for RHEL. I'm not sure, but from looking around on the web, and the fact that RHEL is more of a server distro, it makes sense to me.

---

### Post by twade on 2008-11-11
Thanks smartboy.  That's what I was looking for.  I had originally thought it was VMware, but that clip on the redhat page made me wonder.  I'll let you know if I get it working.

---

### Post by twade on 2008-11-27
Update:
Still not 100% sure what the MultiOS is, but the download for regular RHEL Desktop is the same asd RHEL Desktop with MultiOS (only found this out after purchasing it!)

In the end though, RHEL proved to be entirely unnecessary.  There were problems with the package we were sent that were messing up the installation on a custom Fedora box. . .

---

