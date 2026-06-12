---
title: "cant remove memprof"
date: 2005-12-16
forum: General Help
---

### Post by alingatong on 2005-12-16
I want to remove memprof but i can't. I installed memprof from synaptic. then i accidentally installed memprof again the version downloaded from debian site. i thought it will upgrade. but it did'nt. now i want to remove it but i get an error like this..

> ssdo@ssdo:~$ sudo apt-get remove memprof
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  memprof
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 1339kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 74813 files and directories currently installed.)
Removing memprof ...
/var/lib/dpkg/info/memprof.prerm: line 5: gconf-schemas: command not found
dpkg: error processing memprof (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 memprof
E: Sub-process /usr/bin/dpkg returned an error code (1)
ssdo@ssdo:~$


any ideas?

---

### Post by mikkelwe on 2005-12-16
I don't know why you're getting that error. However you could try

1) Reinstall memprof to make sure everything it provides is actually present, then remove it.
    sudo apt-get --reinstall install memprof && sudo apt-get remove memprof

2) Use brute force (be careful)
    sudo dpkg --force-all -r memprof

---

### Post by alingatong on 2005-12-16
I can't still remove memprof following your advice.anyway thanks for the ideas.

---

