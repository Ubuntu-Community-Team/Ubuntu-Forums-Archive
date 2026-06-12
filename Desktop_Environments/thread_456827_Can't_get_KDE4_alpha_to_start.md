---
title: "Can't get KDE4 alpha to start"
date: 2007-05-28
forum: Desktop Environments
---

### Post by schlesix on 2007-05-28
*** FIXED ***

Hi all,

I want to play a little bit with the KDE4 alpha on a spare Kubuntu Feisty system and have installed it, but I can't get it to start up because of a library problem. This is, what I've done so far:

I've added this repository to my /etc/apt/sources.list:
```
deb http://kubuntu.org/packages/kde4-3.90.1/ feisty main
```

I've installed this packages (all 3.90.1-ubuntu1):
kde4base, kde4base-data, kde4base-dev, kde4libs, kde4libs-data

I try to start KDE4 alpha from a xterm console with a script. This is the script:
```

#!/bin/bash
export LD_LIBRARY_PATH=/usr/lib/kde4/lib
export PATH=/usr/lib/kde4/bin/:$PATH
export KDEHOME=~/.kde4
/usr/lib/kde4/bin/startkde

```

When I do this, KDE4 gives me a message, that it couldn't start kdeinit4. This is the console output:

```

kapplymousetheme: symbol lookup error: /usr/lib/libstreamanalyzer.so.0: undefined symbol: _ZTVN6Strigi25StringTerminatedSubStreamE
Can't read description.txt file.
Link points to "/tmp/kde-gnome"
Link points to "/var/tmp/kdecache-gnome"
Link points to "/tmp/ksocket-gnome"
startkde: Starting up...
kdeinit4: symbol lookup error: /usr/lib/libstreamanalyzer.so.0: undefined symbol: _ZTVN6Strigi25StringTerminatedSubStreamE
startkde: Could not start kdeinit4. Check your installation.
Warning: connect() failed: No such file or directory
ksmserver: symbol lookup error: /usr/lib/libstreamanalyzer.so.0: undefined symbol: _ZTVN6Strigi25StringTerminatedSubStreamE
startkde: shutting down
Warning: connect() failed: No such file or directory
Error: can't contact kdeinit4!
startkde: Running shutdown scripts...
startkde: Done.

```

There seems to be a problem with the ibrary ibstreamanalyzer.so.0. It belongs to strigi, AFAIK. So, I've installed some strigi-packages in addition (all 0.5.1):
libstrigi0, strigi-client, strigi-daemon, strigi-utils.

This doesn't solve the problem.

Can anybody tell me how to fix this problem?

Thanks,
Thomas

---

### Post by schlesix on 2007-05-28
I've fixed it, it has been my own fault. There have been some leftovers from my previous playing with strigi on KDE 3.5.

---

### Post by xylometazolin on 2007-09-18
I've installed KDE4 beta2, but I post my problem here because I get the same error as schlesix.

I have installed the package: kdebase-workspace

Then I've tried to run some KDE4 apps:
```

$ export LD_LIBRARY_PATH=/usr/lib/kde4/lib
$ export KDEDIRS=/usr/lib/kde4
$ export PATH=/usr/lib/kde4/bin/:$PATH
$ export KDEHOME=~/.kde4
$ /usr/lib/kde4/bin/konsole
/usr/lib/kde4/bin/konsole: symbol lookup error: /usr/lib/libstreamanalyzer.so.0: undefined symbol: _ZN6Strigi15FileInputStream17defaultBufferSizeE

```

It doesn't matter what program I start, I always get the same error:
```

symbol lookup error: /usr/lib/libstreamanalyzer.so.0: undefined symbol: _ZN6Strigi15FileInputStream17defaultBufferSizeE

```

Any advice?

Thanks.

---

### Post by daniel2501 on 2007-10-09
How did you fix it? I get a little window that comes up when I try to run kde4 in a separate session: Couldn't start kdeinit4

---

