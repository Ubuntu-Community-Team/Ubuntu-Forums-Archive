---
title: "Synaptic and Ubuntu software center crash"
date: 2012-06-22
forum: Desktop Environments
---

### Post by tdlam on 2012-06-22
Hi folks,
I have an issue with Ubuntu Software center and synaptic package manager...both crash soon after start up. When running Synaptic...I get the following error:

```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


```

I really dont need opera anymore so If I have to get rid of it thats ok but as I said right now I cant even get into Synaptic package manager or Ubuntu software center. 
Any one have any ideas?
Thanks in advance for you kind help.

---

### Post by tdlam on 2012-06-23
I just ran Apt-get update in terminal and got these errors as well...man what a mess...

```
Fetched 13.3 MB in 1min 47s (125 kB/s)                                         
Reading package lists... Error!
W: GPG error: http://deb.opera.com stable Release: The following signatures were invalid: BADSIG AAFF4A5B336064B5 Opera Software Archive Automatic Signing Key 2012 <packager@opera.com>
W: GPG error: http://archive.canonical.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.canonical.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG FC6FA5EB4357B38A Launchpad PPA for Arx Libertatis
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 94E58C34A8670E8C Launchpad PPA for Screenlets
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

---

### Post by oldos2er on 2012-06-23
Fix for mergelist: [http://ihaveapc.com/2011/05/how-to-fix-problem-with-mergelist-varlibaptlists-error-in-ubuntu-11-04/](http://ihaveapc.com/2011/05/how-to-fix-problem-with-mergelist-varlibaptlists-error-in-ubuntu-11-04/)

For BADSIG errors, see [http://maketecheasier.com/solve-badsig-error-in-ubuntu/2012/01/13](http://maketecheasier.com/solve-badsig-error-in-ubuntu/2012/01/13)

---

### Post by tdlam on 2012-06-23
Well that did the trick I really appreciate your time and effort. 
Thank you.
I will mark this post as solved. All the best to you.

---

### Post by oldos2er on 2012-06-23
You're welcome.

---

