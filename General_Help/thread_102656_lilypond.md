---
title: "lilypond"
date: 2005-12-12
forum: General Help
---

### Post by revgrndave on 2005-12-12
I went to install a guitar tablature program that depends on lilypond
not only will it never install, it won't uninstall the part it thinks it needs. 
i tried to show it not to install in kpackage manager, but when i update it still tries to get it.... :confused: 
i am sofa king con fused

---

### Post by Knomefan on 2005-12-13
Could you be a little more specific. What program are you trying to install, where from and what is the exact error.

Also, don't know if it is your problem, but lilypond is in the repos and a newer version is in backports.

---

### Post by miisterwright on 2005-12-21
hey revgrndave, I'm having the same exact problem, but I'm using Ubuntu 5.10. Sorry I don't have a soution yet but, for everyone else here's some info. 
The package was songwrite (I got it with synaptic.) It depends on lilypond, but lilypond never installs. heres what is get when a try to remove lilypond with apt:

root@ubuntu:/home/# apt-get remove lilypond
Reading package lists... Done
Building dependency tree... Done
Package lilypond is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/4736kB of archives.
After unpacking 0B of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 82702 files and directories currently installed.)
Preparing to replace lilypond-data 2.6.3-9~breezy1 (using .../lilypond-data_2.6.3-9~breezy1_all.deb) ...
Unpacking replacement lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

  I don't know if this is exactly your situation or not..let us know if you're getting something different.  Thanks in advance for the help.

---

### Post by miisterwright on 2005-12-21
ok  I got mine fixed thanks to a couple guys on another forum.  Here's the link:

[http://www.ubuntuforums.org/showthread.php?t=95511&highlight=lilypond](http://www.ubuntuforums.org/showthread.php?t=95511&highlight=lilypond)

---

