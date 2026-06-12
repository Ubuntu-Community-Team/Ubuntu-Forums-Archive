---
title: "Can't install Ubuntu Desktop error"
date: 2009-03-04
forum: Desktop Environments
---

### Post by hawkhock on 2009-03-04
I was attempting to upgrade from Gimp 2.4.6 to Gimp 2.6.5 and screwed things up royally.  Now Add/Remove says it can't install Gimp 2.4.6 because there is conflict with existing files. Found several Gimp files in Synaptic which are not installed (green box) but can't remove them.  Upgrade error says "can't install Ubuntu Desktop" so upgrade was only partially done.  Not sure what I did or how to fix it.

---

### Post by wfp on 2009-03-05
Have you tried > sudo apt-get install ubuntu-desktop

---

### Post by hawkhock on 2009-03-05
> **wfp said:**
> Have you tried > sudo apt-get install ubuntu-desktop

Thanks for your reply. Terminal ouput re sudo apt-get install unbuntu-desktop is:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: gimp-python
                  Recommends: gimp but it is not going to be installed
                  Recommends: gimp-gnomevfs but it is not going to be installed
                  Recommends: xsane but it is not going to be installed
E: Broken packages

What next?  Would an autoclean help? or and autoremove to clean up unwanted dependencies?  I'll search out "broken packages" to see how to fix also.

---

### Post by hawkhock on 2009-03-06
Consider this post solved.  Problems kept compiling as I tried to fix things so I did a fresh install.

---

