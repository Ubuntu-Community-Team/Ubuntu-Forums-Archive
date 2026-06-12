---
title: "aMSN TLS Problem"
date: 2006-06-16
forum: Desktop Environments
---

### Post by Kimm on 2006-06-16
I download and installed the latest aMSN (along with tcl/tk), to get antialiesed fonts.

Now aMSN wants to download tls, since it claims its not installed (amsn is intalled to /usr/local, tcl and tk is too).
But When I select Linux-x86 in the dialog this error popps up:

Error Installing TLS Module::
couldn't open socket:
connection refused

Anyone? :confused:

---

### Post by kinematic on 2006-06-16
had the same problem in fedora core 5(now i just use gaim).
got the tarball for the tls lib from soureceforge,put it in /lib and pointed amsn to it but it was a no go.
never was able to figure out how to solve the problem.

---

### Post by Kimm on 2006-06-16
I think I got it to download TLS now... (changing mirror in /usr/local/share/amsn/autoupdate.tcl).

It downloaded it and claimed that it installed correctly... then I click "Connect"... and the same thing happens again :S

I'll try amsn CVS...

---

### Post by Kimm on 2006-06-16
Its damned impossible...

SVN will download the plugin... but then claims to fail during installation.
I have also tried download it and installing it manually (acording to the way aMSN wants me to...). But to no avail.

I even tried telling aMSN where the tls plugin is located... but still, nothing :confused:

---

### Post by Kimm on 2006-06-16
Fixed!

I sneeked a peak at the aMSN FAQ and found out that TLS 1.5 was broken.

You need to find pkgIndex.tcl and replace "package ifneeded tls 1.5" with "package ifneeded tls 1.50", and thats it... anyoing huh?

---

