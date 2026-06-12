---
title: "Synaptic manager error"
date: 2006-07-31
forum: Desktop Environments
---

### Post by kausbose on 2006-07-31
I am receiving the following error whenever I use the synaptic update manager. I need some advice to get a workaround. I am hitting walls everywhere :confused: Please please please help

E: mozilla-mplayer: files list file for package `mozilla-mplayer' is missing final newline

In terminal I get this error:

kbose@cray:~$ sudo apt-get remove mozilla-mplayer --purge
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  mozilla-mplayer*
0 upgraded, 0 newly installed, 1 to remove and 21 not upgraded.
Need to get 0B of archives.
After unpacking 1536kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing mozilla-mplayer (--purge):
 files list file for package `mozilla-mplayer' is missing final newline
Errors were encountered while processing:
 mozilla-mplayer
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


Please help me with the problem

Thank you!

---

