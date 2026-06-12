---
title: "Can you install python-kde?"
date: 2005-04-30
forum: Desktop Environments
---

### Post by brk3 on 2005-04-30
Ive been trying to install python-kde and python-qt for some of amaroks scripts, but seem to be having trouble. I downloaded python-qt from the repitories and it seemed to install fine. But when I try to select python-kde3 and select 'apply', it just refreshs the package list and does nothing!
Heres what happens when i try to install it manually:

--------------------
paul@localhost:~ $ sudo apt-get install python-kde3
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
  python-kde3: Depends: python (< 2.4) but 2.4.1-0ubuntu2 is to be installed
               Depends: python2.3-kde3 but it is not going to be installed
E: Broken packages
paul@localhost:~ $
-----------------------------------

Anyone else tried to install this or have any idea what needs to be done?

---

### Post by WiLLiE on 2005-06-12
Same problem here.

No solution yet? Or do we need to get it from "Breezy"?

---

### Post by odrop on 2005-06-13
I've stressed over those packages for a long time also, but there is hope, hopefully.

Search the repositories for a package called 'python-dcop'.  Despite its name, it has a lot of the development stuff required for using python and kde together.  

I don't know if it has everything you need for running those scripts, but I've been using it to develop some of my own scripts for other things and it seems quite complete.

Until the other packages get fixed though, this seems like our best bet.

---

### Post by ltmon on 2005-06-13
The python-kde packages were broken on release.

See [here](http://linux.blogweb.de/archives/27-python-kde3.html) for a fix.  :)

---

### Post by !nkubus on 2005-06-13
WOW that's is great :) i was looking for this bug 1h ago :)

thank you very much

---

