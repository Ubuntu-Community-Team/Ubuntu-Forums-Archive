---
title: "Moving from Ubuntu to CentOS 6"
date: 2014-11-19
forum: Fedora/RedHat and derivatives
---

### Post by andrew102 on 2014-11-19
What to know?

Do I have to dive into the dark art of IPTABLES or is there an alternative to UFW ?

The only other difference I know of is yum instead of apt.

---

### Post by buzzingrobot on 2014-11-20
If memory serves, a firewall config GUI is in the 'Adminstration' section of the Gnome 2 menu on CentOS 6.  Think the package is "system-config-firewall". 

Check out centos.org. The RHEL 6 documentation at the Red Hat site is extensive and directly applicable since CentOS is an RHEL rebuild.

If you are looking to create a usuable CentOS desktop, you'll need some codecs, etc.  Check out [http://li.nux.ro/repos.html](http://li.nux.ro/repos.html). I've used the RPM's there with great success, as have many others.  There's also rpmfusion.org, the EL Repo site for hardware related packages, etc., and the Epel site maintained for RHEL/CentOS users by the Fedora team. The GTK2 and python versions in CentOS 6 are old, and pretty much cannot be updated, and so may introduce dependency issues that can't be resolved when trying to config a contemporary desktop.

---

### Post by TheFu on 2014-11-20
Debian-based distros are different from Redhat-based distros. Config files are different, put in different places.
Expectations about what auto-starts and what doesn't are different.
apparmor vs SELinux ... 

There are many, many, subtle differences - however, from an end user perspective things are mostly the same at the CLI. From an admin perspective, I'd guess about 50% differences in the specifics, but 95% similar in the overall ideas.

---

### Post by mips on 2014-11-20
Do what you have to, there are other alternatives.

---

### Post by andrew102 on 2014-12-01
Thanks for the feedback. So far it's looking fairly similar to Debian in some ways. The problem I'm now encountering is that many packages are quite old and dated. My main concern is that some of our applications would need significant re-working in order to run on packages available through the main repo.

For example, tomcat6 is available but not tomcat7. I delved into essentially reconfiguring tomcat6 to operate like tomcat7 (with later .jar versions) This became too much of a task so I've successfully run the binary of tomcat7 on CentOS instead. One issue though is that the shutdown doesn't properly kill the process and one can consume a lot of RAM that way.

Unfortunately, it looks like the only way to work with some decent features is going outside of the main repos. This isn't ideal from a support and security perspective.

---

### Post by buzzingrobot on 2014-12-01
> **andrew102 said:**
> ...The problem I'm now encountering is that many packages are quite old and dated.

The tradeoff for the 10-year-plus support cycle is that the system shows its age eventually. CentOS 6 has been around now for some time. Red Hat's "Software Collections" approach might allow a way to build some things and get around the un-upgradability of some core components, like gtk2 and python.

CentOS 7 is considerably more current at the moment, having been released earlier this year. 

This -- [http://wiki.centos.org/AdditionalResources/Repositories](http://wiki.centos.org/AdditionalResources/Repositories) -- in my experience is an honest and accurate discussion of the pros and cons of using "foreign" repos. For personal desktop use, I've used the EPEL and Nux repos in tandem with no problems. The El Repo site provides hardware-related packages -- drivers and kernels -- that I've also used.

---

