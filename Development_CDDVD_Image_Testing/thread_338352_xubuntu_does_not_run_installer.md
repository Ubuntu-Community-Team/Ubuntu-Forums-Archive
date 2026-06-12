---
title: "xubuntu does not run installer"
date: 2007-01-14
forum: Development CD/DVD Image Testing
---

### Post by tjotser on 2007-01-14
Hello, i downloaded and burned the latest feisty-desktop release.. horde 2 
Boots up fine but when i try to execute the installer , nothing happens !!?/](*,) 

I just gave up and am currently downloading the alternate installer-CD
Why s this happening ? is there something i should do or file a bugreport (never did that but i still have the CD ((RW)) ) :confused:

---

### Post by Henrik on 2007-01-14
Yes, filing a bug report here would be great: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+filebug](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+filebug)

Please read this page about how to upload a log file: [https://wiki.ubuntu.com/DebuggingUbiquity/AttachingLogs](https://wiki.ubuntu.com/DebuggingUbiquity/AttachingLogs)

It would also be useful to see output from the command line. Type 'sudo ubiqity' in a terminal yo get that. Thanks!

---

### Post by pochu on 2007-01-14
Hi Henrik.

You wanted to say ubiquity instead of ubiqity, didn't you?

Regards
Pochu

---

### Post by Henrik on 2007-01-15
Yep, sloppy fingers :)

---

### Post by tjotser on 2007-01-15
ubiquity after trying installer...
.
"""""""
ubuntu@ubuntu:~$ sudo ubiquity
Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 185, in <module>
    main()
  File "/usr/lib/ubiquity/bin/ubiquity", line 182, in main
    install()
  File "/usr/lib/ubiquity/bin/ubiquity", line 44, in install
    mod = __import__('ubiquity.frontend', globals(), locals(), frontends)
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 53, in <module>
    from ubiquity.debconfcommunicator import DebconfCommunicator
  File "/usr/lib/ubiquity/ubiquity/debconfcommunicator.py", line 22, in <module>
    import debconf
ImportError: No module named debconf
""""

Sorry ,i'm not registered yet with launchpad or i forgot/lost my passwd
hope this means something to someone either way.. good luck 
XUBUNTU rulezzzz  :mrgreen:

---

### Post by tjotser on 2007-01-15
I just tried my burnt alternat-installer cd and it just crashed on me giving me a blinking cursor but no result when entering commands, Maybe my hardware is not that greatly supported yet.. i'm on an old p3 666 256mb/133Mhz GfFX5200.. Also, whenever having tried either of the two cds, when falling back on my regular system, my internet (or network card) is misconfigured :-k

---

### Post by tjotser on 2007-01-15
ignore me, i'm going to retry and wait and see

The second alpha build (also known as "Herd CD") of Ubuntu 7.04 started to appear on Ubuntu mirrors last week and the release was formally announced today: "Herd 2 released. The primary focus during the time from Herd 1 has been the re-merging of changes from Debian and inclusion of new versions of applications. Notably, we have upgraded the kernel to 2.6.20. This is an early set of images, so you can expect some bugs. Among these are the following: the alternate i386 install CD takes a very long time (about five minutes) to do hardware detection on some machines; the desktop installer sometimes mounts the newly partitioned hard drive and then fails."

---

### Post by lugs on 2007-01-22
HOW TO FIX THIS BUG

it's pretty easy! I figured it out when I had the same bug installing the DVD of ubuntu feisty-2. Try this in a terminal ('alt + f2' then 'gnome-terminal')
```
sudo cp /usr/lib/python2.4/site-packages/debconf.py usr/lib/python2.5/site-packages/
```

The only problem is that the python language can't find the library debconf, and it's coz it's in a different directory, the version of the python language used by the installer is 2.5 and the library is in the 2.4 folder (I don't undestand why ubuntu has the 2 versions of python installed, but...)

did it help?

---

### Post by pochu on 2007-01-22
> **lugs said:**
> HOW TO FIX THIS BUG

it's pretty easy! I figured it out when I had the same bug installing the DVD of ubuntu feisty-2. Try this in a terminal ('alt + f2' then 'gnome-terminal')
```
sudo cp /usr/lib/python2.4/site-packages/debconf.py usr/lib/python2.5/site-packages/
```

The only problem is that the python language can't find the library debconf, and it's coz it's in a different directory, the version of the python language used by the installer is 2.5 and the library is in the 2.4 folder (I don't undestand why ubuntu has the 2 versions of python installed, but...)

did it help?
I think it has been resolved, so you should just download a new daily build.

Regards
Pochu

---

### Post by lugs on 2007-01-22
Let's hope so, but I won't dl that 4gb again... (I hope that's the only strange bug :P)

---

### Post by pochu on 2007-01-22
You can use the cd image instead of the dvd ;)

---

