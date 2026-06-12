---
title: "Lotus Notes 8.5.2 on Ubunut 11.04 64 bit installation problems"
date: 2011-05-06
forum: Desktop Environments
---

### Post by memor2000 on 2011-05-06
Hi everybody,

I tried to install Lotus Notes 8.5.2 (deb package) on Ubuntu 11.04 64 bit. Unfortunately, Lotus is not able to complete the installation!
I googled and I found a guide on IBM forum (but for 10.04 release) and on [http://usablesoftware.wordpress.com/](http://usablesoftware.wordpress.com/) , I installed required dependencies (ia32lib, all getlibs, ecc) but I am not able to continue the installation.

I tried to install in different Ubuntu release. Here a summury:
- Ubuntu 10.10 64 bit: Lotus Notes and FP2 install and works fine
- Ubuntu 11.04 32 bit: Lotus Notes and FP2 install and works fine (also in Unity environment)
- Ubuntu 11.04 64 bit: Lotus Notes cannot install.

Here the output for command

```
sudo dpkg -i --force-all ibm-lotus-notes-8.5.2.i586.deb
```

```

dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 163396 files and directories currently installed.)
Preparing to replace ibm-lotus-notes:i386 8.5.2-20100811.1131 (using ibm-lotus-notes-8.5.2.i586.deb) ...
Unpacking replacement ibm-lotus-notes:i386 ...

dpkg: dependency problems prevent configuration of ibm-lotus-notes:i386:
 ibm-lotus-notes:i386 depends on gdb.
 ibm-lotus-notes:i386 depends on coreutils.
 ibm-lotus-notes:i386 depends on unzip.
 ibm-lotus-notes:i386 depends on bash.
 ibm-lotus-notes:i386 depends on procps.
 ibm-lotus-notes:i386 depends on grep.
 ibm-lotus-notes:i386 depends on sed.
 ibm-lotus-notes:i386 depends on libart-2.0-2.
 ibm-lotus-notes:i386 depends on libasound2.
 ibm-lotus-notes:i386 depends on libatk1.0-0.
 ibm-lotus-notes:i386 depends on libbonobo2-0.
 ibm-lotus-notes:i386 depends on libbonoboui2-0.
 ibm-lotus-notes:i386 depends on libc6.
 ibm-lotus-notes:i386 depends on libfontconfig1.
 ibm-lotus-notes:i386 depends on libfreetype6.
 ibm-lotus-notes:i386 depends on libgcc1.
 ibm-lotus-notes:i386 depends on libgconf2-4.
 ibm-lotus-notes:i386 depends on libgtk2.0-0.
 ibm-lotus-notes:i386 depends on libglib2.0-0.
 ibm-lotus-notes:i386 depends on libgnome2-0.
 ibm-lotus-notes:i386 depends on libgnomecanvas2-0.
 ibm-lotus-notes:i386 depends on libgnome-desktop-2 | libgnome-desktop-2-7 | libgnome-desktop-2-11 | libgnome-desktop-2-17.
 ibm-lotus-notes:i386 depends on libgnomeprint2.2-0.
 ibm-lotus-notes:i386 depends on libgnomeprintui2.2-0.
 ibm-lotus-notes:i386 depends on libgnomeui-0.
 ibm-lotus-notes:i386 depends on libgnomevfs2-0.
 ibm-lotus-notes:i386 depends on libglib2.0-0.
 ibm-lotus-notes:i386 depends on libice6.
 ibm-lotus-notes:i386 depends on libjpeg62.
 ibm-lotus-notes:i386 depends on liborbit2.
 ibm-lotus-notes:i386 depends on libpam0g.
 ibm-lotus-notes:i386 depends on libpango1.0-0.
 ibm-lotus-notes:i386 depends on libpng12-0.
 ibm-lotus-notes:i386 depends on libpopt0.
 ibm-lotus-notes:i386 depends on libsm6.
 ibm-lotus-notes:i386 depends on libstdc++6.
 ibm-lotus-notes:i386 depends on libx11-6.
 ibm-lotus-notes:i386 depends on libxcursor1.
 ibm-lotus-notes:i386 depends on libxext6.
 ibm-lotus-notes:i386 depends on libxft2.
 ibm-lotus-notes:i386 depends on libxi6.
 ibm-lotus-notes:i386 depends on libxkbfile1.
 ibm-lotus-notes:i386 depends on libxml2.
 ibm-lotus-notes:i386 depends on libxp6.
 ibm-lotus-notes:i386 depends on libxrender1.
 ibm-lotus-notes:i386 depends on libxss1.
 ibm-lotus-notes:i386 depends on libxt6.
 ibm-lotus-notes:i386 depends on libxtst6.
dpkg: error processing ibm-lotus-notes:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 ibm-lotus-notes:i386

```


Any idea?

Please, help me

Thanks a lot

---

### Post by cyrinda on 2011-05-09
Hi, exactly same problem here, anyone knows...?

---

### Post by memor2000 on 2011-05-10
Upgrading relase form 10.10 64 bit (with working Lotus installation) to 11.04 64 bit, make Lotus running (only some problem about library, but I think the solution is to re-link library for Notes).
Of course, this is NOT a solution, but only a waste-time-test.....

Hope someone has the solution.....

---

### Post by klemenmo on 2011-05-10
I found this on IBM site (OS support list for Lotus Notes 8.5.2)
[https://www-304.ibm.com/support/docview.wss?uid=swg27019218#Ubuntu%20Desktop](https://www-304.ibm.com/support/docview.wss?uid=swg27019218#Ubuntu%20Desktop)

---

### Post by memor2000 on 2011-05-10
Yes, I know. IBM supports Lotus Notes only on LTS release, but Lotus works on 8.10, 9.04, .. , 11.04 32 bit and 64 bit version (downloading ia32libs) except on 11.04 64 bit. I want to know if the problem about 11.04 64 bit is an easy problem to resolve or not. The output error is generic and not clear. Someone installed successfuly on last 64 bit release....

---

### Post by cyrinda on 2011-05-11
Hi, here is a solution:
[http://usablesoftware.wordpress.com/2011/04/05/lotus-notes-8-5-2-fp2-in-ubuntu-11-04-natty-narwhal-64bit-beta-1/](http://usablesoftware.wordpress.com/2011/04/05/lotus-notes-8-5-2-fp2-in-ubuntu-11-04-natty-narwhal-64bit-beta-1/)

on the end of page - edit CONTROL file

hohoho - ibm rulezzz for linuxers :confused:

---

### Post by memor2000 on 2011-05-11
Thanks a lot!!! :D:D
It works!
Only I cannot see the icons in file/modify/view/etc menù, but all seems to work.

Thanks a lot! :P

---

### Post by themiddaysun on 2012-06-22
This is kinda late to the game but may help others in the future.

[http://usablesoftware.wordpress.com/2012/05/04/install-lotus-notes-8-5-3-on-ubuntu-12-04-64bit/](http://usablesoftware.wordpress.com/2012/05/04/install-lotus-notes-8-5-3-on-ubuntu-12-04-64bit/)

---

### Post by sffvba[e0rt on 2012-06-22
> **themiddaysun said:**
> This is kinda late to the game but may help others in the future.

[http://usablesoftware.wordpress.com/2012/05/04/install-lotus-notes-8-5-3-on-ubuntu-12-04-64bit/](http://usablesoftware.wordpress.com/2012/05/04/install-lotus-notes-8-5-3-on-ubuntu-12-04-64bit/)

Thanks for the info...

*Thread **closed**.*


404

---

