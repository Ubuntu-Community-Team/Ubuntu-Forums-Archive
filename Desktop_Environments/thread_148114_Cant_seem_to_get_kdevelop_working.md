---
title: "Cant seem to get kdevelop working"
date: 2006-03-21
forum: Desktop Environments
---

### Post by sharperguy on 2006-03-21
i am trying to write a qt application with kdevelop in ubuntu with kde added. However when I try to compile i get: 

configure: error:
in the prefix, you've chosen, are no KDE libraries installed. This will fail.
So, check this please and use another prefix!
*** Exited with status: 1 ***


and i have hear that i need kdelibs-dev but when i do that i get:

sharp@xxxxx:~$ sudo apt-get install kdelibs-dev
Reading package lists... Done
Building dependency tree... Done
Package kdelibs-dev is a virtual package provided by:
  kdelibs4-dev 4:3.4.3-0ubuntu2
You should explicitly select one to install.
E: Package kdelibs-dev has no installation candidate

so i do:
sharp@xxxxxx:~$ sudo apt-get install kdelibs4-dev

and get:
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
  kdelibs4-dev: Depends: kdelibs4c2 (= 4:3.4.3-0ubuntu2) but 4:3.5.1-0ubuntu0breezy1 is to be installed
                Depends: kdelibs-bin (= 4:3.4.3-0ubuntu2) but 4:3.5.1-0ubuntu0breezy1 is to be installed
                Depends: libarts1-dev (>= 1.4.0) but it is not going to be installed
E: Broken packages

any help appreciated

---

