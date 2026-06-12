---
title: "System time is always wrong."
date: 2008-02-24
forum: Desktop Environments
---

### Post by Darknite12 on 2008-02-24
Hello Everyone, 

I have run into this problem, that is terribly annoying.  My hwclock shows the correct time
```
$ hwclock
Sun 24 Feb 2008 08:41:34 AM EST  -0.957124 seconds
```

but my System time is incorrect.

```
$ date
Sun Feb 24 08:12:11 EST 2008
```

There no specific pattern to the time difference, the system time just lags behind.  The longer it goes without being corrected, the bigger the time difference is (it always lags behind, it never goes ahead or anything like that).  This leads me to believe that its not a Time Zone problem.  I have read other post that give some insight on the problem, [http://ubuntuforums.org/showthread.php?t=219340](http://ubuntuforums.org/showthread.php?t=219340).  But this has not resolved my issue. 

I have AMD Athlon 64 Processor 3200+ and have installed the Ubuntu 7.10 64bit kernel

```
$ uname -a
Linux cisco 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux
```

Previously I had installed the normal i686 kernel (not 64bit) and I did not have this problem.  This tells me that its not the BIOS clock,  (besides the motherboard is new)

I have edited the /etc/rcS so that the utc = no

```
TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=no
VERBOSE=no
FSCKFIX=no

```

Has anybody ran into this problem.  Please let me know.  Any help will be appreciated.

---

### Post by rapiscan on 2008-02-28
Hello,

This thread has a couple of suggestions: [http://ubuntuforums.org/showthread.php?t=673622](http://ubuntuforums.org/showthread.php?t=673622)

---

### Post by MasterJS on 2008-02-28
I think you need to change the time in the BIOS settings. Isn't that where the system gets the time from?

---

