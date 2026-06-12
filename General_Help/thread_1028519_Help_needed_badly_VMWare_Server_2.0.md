---
title: "Help needed badly VMWare Server 2.0"
date: 2009-01-02
forum: General Help
---

### Post by chrispche on 2009-01-02
I tried to install VMWare Server 2.0 and it would not configure. So now I get an error message. My package manager is messed up. Here is the error message:

"The package 'vmware-server' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system."

I can't re-install it. How do I get rid of this. I should have tried Virtual Box First. :confused:

---

### Post by chrispche on 2009-01-03
Someone must know how to remove this. I tried sudo apt-get remove vmware-server and got:

E: The package vmware-server needs to be reinstalled, but I can't find an archive for it.

I can't re-install this. Is there any other way to remove it? My package manager is broken.

---

### Post by Hybrid-photog on 2009-01-03
Having a quick look on the internet for some help, I found this page...
[http://blog.tremend.ro/2006/08/10/the-package-jedit-needs-to-be-reinstalled-but-i-cant-find-an-archive-for-it/#comments]("http://blog.tremend.ro/2006/08/10/the-package-jedit-needs-to-be-reinstalled-but-i-cant-find-an-archive-for-it/#comments")

Reading up about the --force-remove-reinstreq switch, I found this page...
[http://www.ubuntugeek.com/package-installation-error-and-solution.html]("http://www.ubuntugeek.com/package-installation-error-and-solution.html")

I'd give that a go.

---

### Post by paragkalra on 2009-01-03
How are you trying to install VMware Server 2.0.

Whats your Ubuntu version?

I believe you are using VMware server 2.0 downloaded from:
[http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)

There is un-install script inside the tarball:
vmware-server-distrib/bin/vmware-uninstall.pl

> I should have tried Virtual Box First.

I am using VMware Server 2.0 on Ubuntu 8.10 from past 1 month. Initially I too faced some glitches but once it got installed - there has been no issues what so ever.

---

### Post by chrispche on 2009-01-03
I'm using 8.04. Does that make a difference?

---

### Post by paragkalra on 2009-01-06
> I'm using 8.04. Does that make a difference? 

I guess it should not make much difference...

BTW, were you able uninstall it using "vmware-uninstall.pl" script?

---

