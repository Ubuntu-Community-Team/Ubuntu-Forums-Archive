---
title: "Issue With OpenOffice.org Starting"
date: 2006-08-02
forum: Desktop Environments
---

### Post by GreenHawkIA on 2006-08-02
I'm not sure what exactly happened to my copy of OpenOffice.  Now, when I start it up the program (any of them - Writer, Base, etc) maxes out my CPU cycles and never starts, no matter how long I leave it.  I have to kill it by hand and it is really really slow to do, but it never shows an error message.  It worked fine prior to about two weeks ago, but I can't tell if anything I installed changed it because I use it intermittently.  I tried to remove & reinstall it both with apt-get reinstall and apt-get remove --purge.  The same problem occurs after both of those.  A quick Google & search of the forum reveals nothing.  I never had the quickstarter up & running.  I use AbiWord now for word processing, but I need to get access to .ppt files, etc.  Any suggestions:
My system:
Dell Latitude D505
Ubuntu Dapper Drake
Intel Celeron M 1.4 Ghz

---

### Post by fourchannel on 2006-08-02
In Synaptic, have you tried completely removing OO2 and then reinstalling it?

You might try strace to see if you can spot some permission or loading problem. ```
strace /usr/bin/oobase2
``` 
Have you completely determined that it wont start, or is just really really slow. Like trying to open OO2 before going to bed and seeing if it's still loading the next day?

Some parts of OpenOffice use Java. Have you installed a new JRE or uninstalled it or something?

Other than that I really don't know.

what does ```
/usr/bin/oobase2 --version
``` output?

---

### Post by GreenHawkIA on 2006-08-02
I have not done anything with Java.  When I input your code I get a no such file or directory error, but the version I have installed is 2.0.2-2ubuntu12.1.  I did it via Synaptic once, just to see if I could get any different results - but that's all I got.  As to not starting up - I did not leave it overnight, but I let it run for about 4 hrs one time.  Any other suggestions?

---

