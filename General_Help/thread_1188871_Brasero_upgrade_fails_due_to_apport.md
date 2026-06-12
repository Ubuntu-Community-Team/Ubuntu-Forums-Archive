---
title: "Brasero upgrade fails due to apport"
date: 2009-06-16
forum: General Help
---

### Post by stoer on 2009-06-16
Hi all,
just allowed a general update, including an update of Brasero.
It failed due to a problem updating apport.

I liked this one:;)

apport - "automatically generate crash reports for debugging."

"would you like to rapport this bug?.... Yes"
Launchpad (logged in)
"Due to a problem launchpad is unable at this time....try again later"

You just know it's going to be one of those days, right?

Anyway, here's the code if anyone has the time to advise - much appreciate it.

Error:
```
E: /var/cache/apt/archives/apport_1.0-0ubuntu5.2_all.deb: subprocess new pre-removal script returned error exit status 2
```

Terminal:
```
:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  brasero
The following packages will be upgraded:
  apport
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/113kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package apport.
(Reading database ... 145552 files and directories currently installed.)
Preparing to replace apport 1.0-0ubuntu5 (using .../apport_1.0-0ubuntu5.2_all.deb) ...
 * Stopping automatic crash report generation: apport                           /etc/init.d/apport: 24: runlevel: not found
exit: 24: Illegal number: Stopping
invoke-rc.d: initscript apport, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
 * Stopping automatic crash report generation: apport                           /etc/init.d/apport: 24: runlevel: not found
exit: 24: Illegal number: Stopping
invoke-rc.d: initscript apport, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/apport_1.0-0ubuntu5.2_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/apport_1.0-0ubuntu5.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Jaunty Jackalope user.
Any ideas appreciated, 
cheers!

---

