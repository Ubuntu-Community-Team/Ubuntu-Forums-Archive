---
title: "Bug in xpenguins-applet causes crash of panel"
date: 2006-08-31
forum: Desktop Environments
---

### Post by gotgenes on 2006-08-31
Hi guys,

I'm experiencing a bug similar to [Debian Bug 364590]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=364590"). The bug was closed out of apathy on the part of the filer, but I'd like to reopen the bug. I was wondering if any others are experiencing/can reproduce this bug on their Ubuntu machine. There appears to have been one earlier report of this on the forums: [http://ubuntuforums.org/showthread.php?t=199665]("http://ubuntuforums.org/showthread.php?t=199665")

During installation of the xpenguins-applet, I get the following error message:
```
Setting up xpenguins-applet (2.1.1-2) ...
I/O warning : failed to load external entity "/var/lib/scrollkeeper/(null)/scrollkeeper_cl.xml"
```

Anybody else get this?

P.S. If you want to try it, set up a script on your Desktop called killpenguins.sh like the following:
```
#!/bin/sh
killall xpenguins-applet
```
Then
```
$ chmod +x ~/Desktop/killpenguins.sh
```

This way you can get your panel back, as you won't be able to use Alt + F2 to access any commands. An alternative is to put a launcher to the terminal on your Desktop and just launch the terminal from there.

---

### Post by divdiv on 2006-10-08
Thanks for your post it saved me a lot of time. I never even saw one penguin, just a crippled panel. I don't know if i'll ever love penguins the way I used to.

---

### Post by TheeMahn2003 on 2006-11-09
> **gotgenes said:**
> Hi guys,

I'm experiencing a bug similar to [Debian Bug 364590]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=364590"). The bug was closed out of apathy on the part of the filer, but I'd like to reopen the bug. I was wondering if any others are experiencing/can reproduce this bug on their Ubuntu machine. There appears to have been one earlier report of this on the forums: [http://ubuntuforums.org/showthread.php?t=199665]("http://ubuntuforums.org/showthread.php?t=199665")

During installation of the xpenguins-applet, I get the following error message:
```
Setting up xpenguins-applet (2.1.1-2) ...
I/O warning : failed to load external entity "/var/lib/scrollkeeper/(null)/scrollkeeper_cl.xml"
```

Anybody else get this?

P.S. If you want to try it, set up a script on your Desktop called killpenguins.sh like the following:
```
#!/bin/sh
killall xpenguins-applet
```
Then
```
$ chmod +x ~/Desktop/killpenguins.sh
```

This way you can get your panel back, as you won't be able to use Alt + F2 to access any commands. An alternative is to put a launcher to the terminal on your Desktop and just launch the terminal from there.

I have faced the same issue prior had to kill x and scrap my .session file to get back in however it works perfectly w/o the use of the applet in a terminal xpenguins or create a launcher must be a bug in the applet.  I have both that 1 and xsnow running at the same time will be nice for christmas I love eyecandy a little odd however both recognizes twinview but walk up the inside edge of both monitors.

---

