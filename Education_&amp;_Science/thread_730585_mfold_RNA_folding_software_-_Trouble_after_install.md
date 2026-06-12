---
title: "mfold RNA folding software - Trouble after install"
date: 2008-03-21
forum: Education &amp; Science
---

### Post by CrazyUbu90 on 2008-03-21
Hello, I recently installed the package [mfold 3.3.tar.gz](http://mfold.bioinfo.rpi.edu/download/) on my Ubuntu distro. It is a package used to predict RNA folding.

I have SSH access to an mfold server, in which mfold is installed under Redhat. The mfold on that server works fine.

However, when I try to use mfold on my local Ubuntu installation, I get an error like the following:
[IMG]http://img182.imageshack.us/img182/3636/errorscompactul2.png[/IMG]

I took a look at the mfold script, and it has a bunch of [COLOR="Red"]"echo -e"[/COLOR] commands within it. 

Is this a problem with the install itself? Or is it just a problem with some environment variable / shell configuration that I am unaware of?

I am out of ideas...I have been trying to fix it most of the day. Any help would be appreciated, as I am using this for my research, and would like to have a local copy installed for additional speed when doing massive amounts of data.

When mfold outputs files, it prefixes the files with "-e filename".

---

### Post by CrazyUbu90 on 2008-03-25
bump. Anyone?

---

### Post by zukerm on 2008-12-20
> **CrazyUbu90 said:**
> Hello, I recently installed the package [mfold 3.3.tar.gz](http://mfold.bioinfo.rpi.edu/download/) on my Ubuntu distro. It is a package used to predict RNA folding.

I have SSH access to an mfold server, in which mfold is installed under Redhat. The mfold on that server works fine.

However, when I try to use mfold on my local Ubuntu installation, I get an error like the following:
[IMG]http://img182.imageshack.us/img182/3636/errorscompactul2.png[/IMG]

I took a look at the mfold script, and it has a bunch of [COLOR="Red"]"echo -e"[/COLOR] commands within it. 

Is this a problem with the install itself? Or is it just a problem with some environment variable / shell configuration that I am unaware of?

I am out of ideas...I have been trying to fix it most of the day. Any help would be appreciated, as I am using this for my research, and would like to have a local copy installed for additional speed when doing massive amounts of data.

When mfold outputs files, it prefixes the files with "-e filename".

I am really sorry for this mess! My fault. The mfold script is an old and clumsy shell script (/bin/sh) written by me, a novice. It was never meant to be used as is, but merely as a prototype. 

The problem(s) described here are a result of updates/changes in Unix/Linux standards. Some solutions are:

Add

export _POSIX2_VERSION=0 

at the top of every script. (right after the 
#!/bin/sh
line. You probably don't need the "export" part, but it doesn't hurt. 

Another solution (works on my Mac) is to change from "sh" to "bash"

Top line of (every script) becomes:

#!/bin/bash

Both "fixes" should work.

By the way, I have replaced "mfold" with UNAFold, which is written to much higher standards. Download at:

[http://dinamelt.bioinfo.rpi.edu/download.php](http://dinamelt.bioinfo.rpi.edu/download.php)

You won't get identical results. The "UNAFold.pl" script replaces the "mfold" script. If you specify a temperature for RNA folding using this script, you will get the old version 2.3 rules, which I do not recommend unless you wish to fold at many temperatures and simulate melting. If you write your own scripts or use the raw C programs, the flag

--suffix=DAT

gives you the version 3.0 RNA rules. 

Sorry for the digression and really sorry that you wasted so much time. I will update immediately.

Michael Zuker

---

