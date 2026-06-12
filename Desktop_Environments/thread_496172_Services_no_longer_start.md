---
title: "Services no longer start"
date: 2007-07-08
forum: Desktop Environments
---

### Post by Elisei on 2007-07-08
hello:

i was doing 'something' in the etc directory & ended up deleting all rcX.d directories; i believe they've contained the start up scripts, cause now i have to manually start all services including gdm and some of the stuff is still not working; is there any way to recover the content of the deleted directories , if anyone knows please & thanks ?

p.s. : ive deleted them cause some 'really nice' VMware install tutorial suggested to do that, hehe; next time ill know;)

---

### Post by coffeecat on 2007-07-09
Most of the files are symbolic links to /etc/init.d. I was going to suggest that you fire up the live install CD, mount your root partition and copy all the contents of /etc/rc*.d from the live CD /etc to the hard disk /etc. I don't know whether that's feasible, BUT - have a look at this from the readme in one of those directories:

> The scripts in this directory are executed each time the system enters
this runlevel.

The scripts are all symbolic links whose targets are located in
/etc/init.d/ .

To disable a service in this runlevel, rename its script in this directory
so that the new name begins with a 'K' and a two-digit number, where the
number is the difference between the two-digit number following the 'S'
in its current name, and 100.  To re-enable the service, rename the script
back to its original name beginning with 'S'.

For a more information see /etc/init.d/README.I've got a right old mixture of K* and S* files so your setup is going to be somewhat different from the default. Have fun! :wink:

---

