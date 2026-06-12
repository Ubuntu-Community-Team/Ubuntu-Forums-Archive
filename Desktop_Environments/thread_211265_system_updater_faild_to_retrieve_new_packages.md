---
title: "system updater faild to retrieve new packages"
date: 2006-07-08
forum: Desktop Environments
---

### Post by rubso on 2006-07-08
hey guys, well i clicked on the system updater when it notified me about new packages update, then when i clicked "Install Updates" some of them can't be retrieved, "404 Not Found" take a look at this
> W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.2.1-0ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.2.1-0ubuntu1_i386.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.2.1-0ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.2.1-0ubuntu1_i386.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.2.1-0ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.2.1-0ubuntu1_i386.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.2.1-0ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.2.1-0ubuntu1_i386.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.2.1-0ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.2.1-0ubuntu1_i386.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecups/libgnomecups1.0-1_0.2.2-1ubuntu5.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecups/libgnomecups1.0-1_0.2.2-1ubuntu5.1_i386.deb)
  404 Not Found


W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/pmount/pmount_0.9.11-1ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/pmount/pmount_0.9.11-1ubuntu1_i386.deb)
  404 Not Found



any clue?

---

### Post by vem0m on 2006-07-08
seems the repositories are missing those files have you tried other repositories?

---

### Post by rubso on 2006-07-08
i think i can't , since the system updater is using its own repositories. ( i guess )

---

### Post by FredB on 2006-07-08
> **rubso said:**
> i think i can't , since the system updater is using its own repositories. ( i guess )

Erh... It looks like your repository is not fully up-to-date.

So wait a little time (say one hour or two) and you'll get the missing package.

](*,)

---

### Post by flu on 2006-07-08
The cupsys package is [COLOR="Red"]broken[/COLOR]. I tried to reinstall the cupsys package from the [main repository]("http://archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.2.1-0ubuntu1_i386.deb") but heres what I got:
```
sudo dpkg -i cupsys_1.2.1-0ubuntu1_i386.deb
Password:
(Reading database ... 137359 files and directories currently installed.)
Preparing to replace cupsys 1.2.1-0ubuntu1 (using cupsys_1.2.1-0ubuntu1_i386.deb) ...
 * Stopping Common Unix Printing System: cupsd                           [ ok ]
Unpacking replacement cupsys ...
Setting up cupsys (1.2.1-0ubuntu1) ...
 * Starting Common Unix Printing System: cupsd cupsd: Child exited with status 1!
invoke-rc.d: initscript cupsys, action "start" failed.
dpkg: error processing cupsys (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 cupsys

```
```
sudo /etc/init.d/cupsys restart
 * Restarting Common Unix Printing System: cupsd 
cupsd: Child exited with status 1!
```
I have to revert the updates to previous version to make cupsys work again. I downloaded the packages and installed it using dpkg manually instead using Synaptic as I gets confused when Synaptic wants to remove some packages. Anyway, problem solved.

The problem appears for computer configured for network printing because address masks with * are broken in this CUPS package (according to the [bug page]("https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/52390")). It is best not to update cupsys and its dependencies for those configured cups for network printing(its [COLOR="Green"]OK[/COLOR] for those didn't configure cups for network printing:) ) if available for now, until cupsys problem is fixed.

---

### Post by rubso on 2006-07-08
then, shall i ignore all the packages now? then reinstalling it via Synaptic next week or something.

---

### Post by flu on 2006-07-09
Take a look at this [thread]("http://www.ubuntuforums.org/showthread.php?t=211540") and cupsys [bug page]("https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/52390"). Looks like I'm not alone with the cupsys problem.

---

### Post by vem0m on 2006-07-09
repos go down or not always updated wait a bit and try again if for some reason after a day its still not working try a differant repo

---

### Post by philstovell on 2006-07-09
I've just clicked reload in Synaptic and now I'm getting this:

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Edit:

I checked the repositories, and not all were enabled. I enabled them all and checked each component (multiverse, etc) and now all (seems) well.

---

### Post by vem0m on 2006-07-09
Great so it was just a single repo problem :D

---

