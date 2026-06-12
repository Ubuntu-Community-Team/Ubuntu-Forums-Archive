---
title: "Apt-Get problem when attempting to install unstable software"
date: 2006-07-12
forum: Desktop Environments
---

### Post by ktneely on 2006-07-12
Hi there, I cam across [Apt-Pinning for Beginners ]("http://jaqque.sbih.org/kplug/apt-pinning.html") today while trying to figure out how to install the newest version of Wyrd on my new Ubuntu server.  I followed the steps, and did an "apt-get -t unstable install wyrd" I messed something up and the system gives me the following error:


>   libc6: Depends: tzdata but it is not installable
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-15 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


And does this for all packages I have tried, like, say, fetchmail.  If I follow its instructions and use the '-f' switch, it looks like it wants to reinstall pretty much the entire system, which I am not a fan of.


> 
ktneely@piglet:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  a2ps adduser alsa-base alsa-utils apache2 apache2-common apache2-mpm-prefork ... and on and on until:
  xaw3dg xfsprogs zip zlib1g zlib1g-dev
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libc6 (due to apt) libgcc1 (due to apt) libstdc++6 (due to apt) ... and on and on until: initscripts (due to sysvinit) tar util-linux lsb-base (due to util-linux) libslang2 (due to util-linux) zlib1g (due to util-linux)
0 upgraded, 0 newly installed, 378 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 607MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'


Any ideas how to get back to the place I was before?  Currently, I have removed the entries for unstable in the apt-sources.list and removed the preferences file, but I am pretty much unable to install anything via apt-get now.

thank you,
K

---

### Post by ktneely on 2006-07-12
I had been looking at this for hours, and of course I solve it within minutes of posting the question.  I figured out how to downgrade packages from this excellent response to a somewhat similar problem to mine:

[http://www.ubuntuforums.org/showpost.php?p=1164182&postcount=5](http://www.ubuntuforums.org/showpost.php?p=1164182&postcount=5)

Using that technique, I tried to downgrade libc6, but failed.  Then, I noticed that the libc6 package wanted its other packages to downgrade along with it, so I did this:

ktneely@piglet:~$ sudo apt-get install libc6-dev=2.3.6-0ubuntu20 libc6-i686=2.3.6-0ubuntu20 libc6=2.3.6-0ubuntu20

and it worked like a charm. 

Hope my solution helps someone else.

---

