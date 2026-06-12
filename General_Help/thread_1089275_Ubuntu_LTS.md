---
title: "Ubuntu LTS"
date: 2009-03-06
forum: General Help
---

### Post by measekite on 2009-03-06
**Two Questions**

**One**
I know that the Long Term Support goes for 5 years from date of release.  Do any of the application software version get updated during that time as they are released or is it just like the standard releases where the versions are fixed at time of release?

**Two**
If they are updated then why can't you use the LTS repositories to upgrade application software for the standard releases?

---

### Post by howefield on 2009-03-06
Applications tend not to be updated within the lifetime of a particular version of Ubuntu, outside of security updates.

---

### Post by hansdown on 2009-03-06
Hi measekite.

Hardy is supported for 18 months.

It is very stable if you would like to have a newer distro.

---

### Post by martrn on 2009-03-06
> **measekite said:**
> I know that the Long Term Support goes for 5 years from date of release.  Do any of the application software version get updated during that time as they are released or is it just like the standard releases where the versions are fixed at time of release?

It there are any critical bug fixes in the (?3?) years then the application software will be updated, however if there are significant changes to either the software or an application that does not include critical software fixes then the application will not be updated in the 8.04 LTS repository.  The next version(s) not of an LTS release will have newer versions of some softare packages.

> **measekite said:**
> If they are updated then why can't you use the LTS repositories to upgrade application software for the standard releases?

You should not use ubuntu repositories of 8.04LTS release to upgrade your software on a 8.10 release as the 8.10 is maintained separately from the 8.04 repository, and may have newer release software in it (and newer features and newer bugs maybe), unless of course you need a reason to do this.  The linux kernels and desktops such as gnome and kde follow a cycle of releases where there will be differences that may cause problems.

The maintainers of the Ubuntu reposotories will concentrate on the most recent version of Ubuntu for newer releases and bug fixing and important security issues for the later versions, they are maintained separately,

If you wish to be a maintainer of a pagackage or packages in the ubuntu repositories then contact the ubuntu team : [https://wiki.ubuntu.com/UbuntuDevelopment]("https://wiki.ubuntu.com/UbuntuDevelopment")

---

### Post by howefield on 2009-03-07
> **hansdown said:**
> Hardy is supported for 18 months.

As the OP already knows, Hardy desktop is supported for 3 years and the server edition for 5.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

