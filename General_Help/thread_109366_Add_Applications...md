---
title: "Add Applications.."
date: 2005-12-28
forum: General Help
---

### Post by godvict on 2005-12-28
When i open 'Add Applications' from -Applications>Add Applications. I am eble to select some of the programs, but in others (for Example: juk) a window pops up saying.
 
                                                              "Information"                                          Cannot install 'juk' Installing this application would mean that something else needs to be removed. Please use the "Advanced" mode to install 'juk'.

What does that mean, and how do i install it? 
Thx You For You Help

---

### Post by Kyral on 2005-12-28
It most likely means something that Juk depends on would conflict with something already installed. The commandline Apt-Get should tell more

Try this in a Terminal

```
sudo apt-get install juk -s
```

Don't worry, the -s option means it will only simulate. Paste what it spits out

---

### Post by godvict on 2005-12-30
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
  juk: Depends: libmusicbrainz4 (>= 2.1.1) but it is not going to be installed
       Depends: libtunepimp2 (>= 0.3.0) but it is not going to be installed
       Depends: libtunepimp-bin but it is not going to be installed
E: Broken packages

.WHATEVER THAT MEANS.

---

### Post by KrazyPenguin on 2005-12-30
Try Synaptic.  See what it says.  Some packages may have to be removed and reinstalled.

---

