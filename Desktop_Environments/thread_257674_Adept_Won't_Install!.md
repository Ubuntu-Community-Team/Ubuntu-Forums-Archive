---
title: "Adept Won't Install!"
date: 2006-09-14
forum: Desktop Environments
---

### Post by draggor on 2006-09-14
I run sudo apt-get install adpet, and get this:
```
sudo apt-get install adept
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  adept: Depends: debtags but it is not going to be installed
         Depends: libapt-pkg-libc6.3-6-3.10
E: Broken packages

```
I found that my current version of Apt provides libapt-pkg-libc6.3-6-3.11, not libapt-pkg-libc6.3-6-3.10.  What do I do to get my Adept back?

---

