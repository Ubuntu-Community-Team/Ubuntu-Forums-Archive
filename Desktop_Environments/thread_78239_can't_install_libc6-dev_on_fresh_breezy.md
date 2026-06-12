---
title: "can't install libc6-dev on fresh breezy"
date: 2005-10-18
forum: Desktop Environments
---

### Post by bcrowell on 2005-10-18
I have a fresh install of breezy badger. Basically all I've done is to edit my /etc/apt/sources.list (comment out the cd, uncomment universe), do an apt-get update, and then try to install some of the development stuff. When I try to do an apt-get install libc6-dev, here's what I get:

# apt-get install libc6-dev
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
  libc6-dev: Depends: libc6 (= 2.3.5-1ubuntu8) but 2.3.5-1ubuntu12 is to be installed
E: Broken packages

Any suggestions on how to fix this problem? TIA!

---

### Post by bcrowell on 2005-10-18
I posted this before going to bed. Woke up in the morning, did an apt-get update, and it had a *ton* of updates. Tried the install again, and it worked.

---

