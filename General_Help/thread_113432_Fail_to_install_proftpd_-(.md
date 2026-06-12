---
title: "Fail to install proftpd :-("
date: 2006-01-06
forum: General Help
---

### Post by Lindhardsen on 2006-01-06
Hi There!

I'm trying to install proftpd, but the installation fails with this error:
> proftpd:
 Depends: libssl0.9.8 (>=0.9.8a-1) but it is not installable
 Depends: proftpd-common but it is not going to be installed

I'm guite new to Linux, so I cannot really figure out what this means? Have I installed fome other stuff which conflicts with this libssl0.9.8 or what is the problem? 
And most important, how do I repair it?

Regards,

Jan

---

### Post by schilcha on 2006-01-06
I've checked the standard-repositories (ubuntu, universe, multiverse, ...). There I could only find libssl up to 0.9.7. So, most likely in the sources you configured, this version can't be found. 

You'll have to find it elsewhere... (some other repository or download it and install by hand)

---

### Post by Tottigoal on 2006-01-06
I had the same problem that I solved
using synaptics adding ALL the sources (see universe and multiverse).

Saluti dall'Italia e sempre Forza Roma.

---

### Post by Lindhardsen on 2006-01-07
The "problem" was a newer version of proftpd which was in an dapper repository that I'we added.

This version of proftpd obviously nedded a newer version of the ibsssl... Removing this repository temporary solved the problem.

Thanks for your feedback.

/Jan

---

### Post by desjazz on 2006-10-23
I am having a similar problem. I firstly could nto install proftpd via apt-get install as the program couldn't be found. I then eneabled additional repositories and this has now given me a new error message about broken packages.

The info I have is below: -

root@kemet:/etc/postfix/ssl# apt-get install proftpd proftpd-common ucf
Reading package lists... Done
Building dependency tree... Done
ucf is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  proftpd: Conflicts: proftpd-common
E: Broken packages


Can anyone help with this?

---

### Post by taurus on 2006-10-23
What if you only install proftpd without the proftpd-common since they both can't be installed at the same time, according to the error message!!!

Also, don't forget to run "apt-get update" before you install anything...

---

