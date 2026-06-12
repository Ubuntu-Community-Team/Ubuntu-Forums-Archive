---
title: "Commercial digital distribution for Linux ?"
date: 2009-04-09
forum: General Help
---

### Post by willz06jw on 2009-04-09
Hi,

Is there a commercial digital distribution client for Linux?  If so, what type of software is available through it?  Please no flames about open source vs commercial software.

Thanks for your help,
Will

---

### Post by soltanis on 2009-04-09
Uh yeah there are many. A lot of them have open versions that are just about as good. Look into

Red Hat Enterprise Linux (formerly Red Hat Linux) - [www.redhat.com](www.redhat.com)
SUSE Linux Enterprise - [www.novell.com/linux](www.novell.com/linux)

Open versions of the same (community support, no branding) are:

Fedora, the RHEL testbed
CentOS, a RHEL clone that uses the fact that all RHEL code is open-source to compile a GPL distribution for free
openSUSE, the SUSE testbed

---

### Post by willz06jw on 2009-04-12
Thanks for the quick reply,

I am not looking necessarily for a commercial distribution of Linux as I am looking for a way to sell programs through a repository (like the apple app store or the google store).  I think it is incredibly hard for developers to get a commercial product to the millions of Linux users.

Thanks,
Will

---

### Post by mb_webguy on 2009-04-13
Many software development projects, such as Deluge, maintain repositories for their software.  This works great for free software, but less so for commercial software.  The problem with commercial software is access control -- ensuring that only those individuals who have paid for the software are able to install and upgrade it.

No access control method is perfect.  All can be (and have been) bypassed if users are determined enough.  Once you accept that, then several options are available.

Using a repository to distribute the software is probably more trouble than it's worth, because controlling access to the repository would be extraordinarily difficult.  You can't simply use a whitelist of customer IP addresses, since IP addresses can change, and multiple users can have the same external IP address if using a proxy.  You could use a specialized client to control access to the installation and updating of the software based on a hardware signature, but then you'd have to create the client rather than using some sort of pre-existing software.

The easiest way would probably be to distribute installable software using a download from a website that requires a password login.  The problem with this is that password can be shared, and it doesn't prevent the software from being shared after it is downloaded.

The best way, in my opinion, to control the use of commercial software is to make it a web app (like Google Apps) or a network app (like some online games where the software is free but users pay a fee for server access) requiring a user login.  Even if the login information is shared, only one user could access the software at a time.  The downside is that such a method requires users to have a good Internet connection.

---

### Post by willz06jw on 2009-04-13
I am not interested in locking up my software after it is sold(DRM).  I am just looking for a way to showcase the software in an application that lists other programs for sale and takes care of the initial credit collection for me.

Thanks again,
Will

---

