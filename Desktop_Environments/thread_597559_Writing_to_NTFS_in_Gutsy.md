---
title: "Writing to NTFS in Gutsy"
date: 2007-10-30
forum: Desktop Environments
---

### Post by TheValk on 2007-10-30
I regularly copy from an encfs encrypted folder to an NTFS Truecrypt container under Feisty with the latest ntfs-3g without problem.
Using Gutsy however, I get frequent Gnome crashes where sometime even CTR/ALT/BS fails and the reset button is the only out.
This results in a corrupted NTFS container and a boot into Windows XP and chkdsk /f to fix the file system.
I understand that the version of ntfs-3g supplied with gutsy is not the latest version.
Is this so and is it worth waiting for an update or should I try and update it myself?
What is the best way to go about it?
Just use Synaptic to uninstall and then build the latest from the ntfs-3g web site or is there a version somewhere in a depository?

---

### Post by Thyme on 2007-10-30
Hi TheValk,

I too use ntfs-3g and am really happy using it. With regard to your situation though, I would recommend first checking the [[COLOR="Blue"]getdeb.net[/COLOR]]("http://www.getdeb.net/") website and if your can't find a later package there then maybe try building the latest from source which you can find at linux.sofpedia.com (for example).

You should use synaptic and remove ntfs-3g before reinstalling it just to make sure that there are no traces of any problem configuration files etc .. I stand correct but I think the only dependency that ntfs-3g requires is fuse-libs (or just fuse) which you should reinstall as well (in which case you should remove it from within synaptic) and download a later version.

I'm not really should how to go about solving your problem but if you're not able to solve it, downloading a new version may help :)

---

### Post by TheValk on 2007-10-30
Thanks for that.
I think I'll give it a go.

---

### Post by TheValk on 2007-11-01
I thought I would try to update ntfs-3g to the latest version so I downloaded the version 1.1030 from the site.
I tried to compile it but get this error towards the end of the process.
--------------------------
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

--------------------------------

and at the end of the config.log

------------------------------

gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
configure:3083: $? = 0
configure:3090: gcc -V >&5
gcc: '-V' option must have argument
configure:3093: $? = 1
configure:3116: checking for C compiler default output file name
configure:3143: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:3146: $? = 1
configure:3184: result: 
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "ntfs-3g"
| #define PACKAGE_TARNAME "ntfs-3g"
| #define PACKAGE_VERSION "1.1030"
| #define PACKAGE_STRING "ntfs-3g 1.1030"
| #define PACKAGE_BUGREPORT "ntfs-3g-devel@lists.sf.net"
| #define PACKAGE "ntfs-3g"
| #define VERSION "1.1030"
| #define _GNU_SOURCE 1
| /* end confdefs.h.  */

-------------------------------

I'm quite new to all this so
anyone?

---

### Post by taurus on 2007-11-01
You need the build-essential package.

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by wkulecz on 2007-11-01
> You need the build-essential package.

Everytime this is the answer to a problem I'm left wondering why is Ubuntu the only Unix system I've ever encountered that can't compile C code out of the box?

--wally.

---

### Post by taurus on 2007-11-01
> **wkulecz said:**
> Everytime this is the answer to a problem I'm left wondering why is Ubuntu the only Unix system I've ever encountered that can't compile C code out of the box?

--wally.

It has been discussed since the first version of Ubuntu came out so I am not going to go into details.  Search for those thread if you wish.

---

### Post by TheValk on 2007-11-01
Thanks for that taurus. It looks like I hit a long standing problem that I should have found by searching the forums more diligently :rolleyes:

I have now compiled and built the package but not installed it because I am unsure as to whether it is safe to do so without uninstalling the current ntfs-3g package?

Does it matter, or will it just update where necessary?

Thanks for all the help.

---

### Post by TheValk on 2007-11-01
OK, ran make uninstall then make install and have the latest 1.1030 ntfs-3g running   :)
Sadly, fault still remains, gnome lockup and reboot needed to recover.  :confused:
What worked faultlessly in Feisty broken in Gutsy.
Cut to pieces on the bleeding edge once more......
Still have Feisty installed so I'll just drop to that when I need to copy between filing systems and hope that a future update fixes things.
Thanks to all who offered advice.

---

### Post by QCompson on 2007-12-19
Just wanted to say I have the same problem.

Freezing and lockups copying files to truecrypt encrypted ntfs partition, and requires a hard reboot.  Occurs under gnome, xfce, and kde (not a big surprise... I too suspect ntfs-3g or truecrypt issue).

edit: almost forget... running Gutsy here on AMD 64 x2

---

### Post by szaka on 2007-12-19
> **QCompson said:**
> I too suspect ntfs-3g or truecrypt issue).

It's a bit more complex: [http://lwn.net/Articles/261626/](http://lwn.net/Articles/261626/) 

Some people indeed reported hangs with recent Ubuntu kernels if both NTFS-3G and TrueCrypt are used. I suggest to submit an Ubuntu kernel bug report, they should know what they changed in the newer Ubuntu kernels which causes these hangs. In the past TrueCrypt and NTFS-3G worked fine together.

---

### Post by QCompson on 2007-12-20
> **szaka said:**
> It's a bit more complex: [http://lwn.net/Articles/261626/](http://lwn.net/Articles/261626/) 

Some people indeed reported hangs with recent Ubuntu kernels if both NTFS-3G and TrueCrypt are used. I suggest to submit an Ubuntu kernel bug report, they should know what they changed in the newer Ubuntu kernels which causes these hangs. In the past TrueCrypt and NTFS-3G worked fine together.

Thanks for the reply, Szaka.  The page you linked to is complete garbley-gook to my non-programmer mind, but I will take your advice and submit a bug report.

And I agree, I've never had any problems using ntfs-3g and truecrypt together in the past.

---

### Post by tech9 on 2007-12-20
> **QCompson said:**
> Thanks for the reply, Szaka.  The page you linked to is complete garbley-gook to my non-programmer mind, but I will take your advice and submit a bug report.

And I agree, I've never had any problems using ntfs-3g and truecrypt together in the past.


what is this "garbley-gook" you speak of?

---

### Post by QCompson on 2007-12-20
> **tech9 said:**
> what is this "garbley-gook" you speak of?
For example (from the article):
> The patch does not try to directly track the amount of memory which will be used by each writeout request; instead, it tasks block-level drivers with accounting for the number of "units" which will be used. To that end, it adds an atomic_t variable (called available) and a function pointer (metric()) to each request queue. When an outgoing request finds its way to __generic_make_request(), it is passed to metric() to get an estimate of the amount of resource which will be required to handle that request. If the estimated resource requirement exceeds the value of available, the process will simply block until a request completes and available is incremented to a sufficiently high level.

I didn't mean to infer that the linked article doesn't make sense.  It just doesn't make sense to *me*.  I can only guess that there is some sort of memory-allocation problem.  I'll take szaka's word for it, since he undoubtedly knows much more about it than I do.

---

### Post by clove on 2007-12-26
Same problem here.  One thing I didn't see mentioned in previous posts is that (at least for me) the hang only occurs when trying to transfer a large file (a few GBs--not sure exactly where the break point is).

My backup routine consists of rsync'ing to an ntfs mounted truecrypt container on a removable drive.  I'm now unable to run my regular backups since upgrading to Gusty.

Hope this thread stays alive until a solution is found.

BTW I am also running an AMD64 X2.

---

### Post by skywalkin1138 on 2008-05-14
Hello, I wanted to chime in.  This is also a problem reading from an NTFS partition inside a TrueCrypt file and writing to an ext3 partitions inside a TrueCrypt file on Hardy Heron.  I'm going to get the latest ntfs-3g (1.2506) and see if it helps.

Regards

---

### Post by skywalkin1138 on 2008-05-15
Same problem exists writing to a TrueCrypt ext3 partition.  Tried to run a VMware instance from it and it started out okay, but after a few minutes it hung the system.  Only option was hard shutdown.

Did load the new ntfs-3g, btw.  Not sure if it helped when I was copying.  I only tried two files equaling ~6GB and it worked okay (from TrueCrypt ntfs to TrueCrypt ext3).  Happened to be a compressed files.  Was able to extract them (on the ext3) which worked okay, but as stated above, when I tried running a VM it hung.

Hope this helps.  Let me know if I can do anything to support.  System: Dell D610, Intel Pentium M 2.13GHz w/2GB (DDR2 533MHz) RAM.
O/S: Hardy Heron (Ubuntu 8.04)

---

