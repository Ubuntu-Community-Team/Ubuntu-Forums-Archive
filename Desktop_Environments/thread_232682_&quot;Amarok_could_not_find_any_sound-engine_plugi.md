---
title: "&quot;Amarok could not find any sound-engine plugins.&quot;"
date: 2006-08-09
forum: Desktop Environments
---

### Post by ehamberg on 2006-08-09
After I upgraded to Amarok 1.4.1 ([http://kubuntu.org/announcements/amarok-1.4.1.php](http://kubuntu.org/announcements/amarok-1.4.1.php)), I can no longer start Amarok. It quits with this error message:

```

Amarok could not find any sound-engine plugins. Amarok is now updating the KDE configuration database. Please wait a couple of minutes, then restart Amarok.
If this does not help, it is likely that Amarok is installed under the wrong prefix, please fix your installation using:
$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ ./configure --prefix=`kde-config --prefix` && su -c "make install"
$ kbuildsycoca
$ amarok
More information can be found in the README file. For further assistance join us at #amarok on irc.freenode.net.

```

Updating the KDE configuration database does not help.
The installed packages are:
```

ii  amarok                                               1.4.1-0ubuntu1                          versatile and easy to use audio player for K
ii  amarok-engines                                       1.4.1-0ubuntu1                          output engines for the amaroK audio player
ii  amarok-xine                                          1.4.1-0ubuntu1                          xine engine for the amaroK audio player

```

Does anyone else have experienced this problem? Any suggestions on how to fix it?

---

### Post by orb9220 on 2006-08-09
Are you trying to compile the source? 

"$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ ./configure --prefix=`kde-config --prefix` && su -c "make install"

That is not required since you can install 1.4.1 thru synaptic.

And did you install all the neccessary codecs using Automatix or easy ubuntu?

You cannot just install amarok and go you also have to install the codecs which is not done with amarok.

And the link you gave is a dead link.

---

### Post by ehamberg on 2006-08-09
No, I installed it with apt using the repository on the linked page (I fixed the link).
I have the required codecs.

---

### Post by orb9220 on 2006-08-09
Well 1.4.1 is in synaptic as of yesterday now.

So you might want to do an uninstall and try synaptic.
I had a problem with installing the new 1.4.2 wolf alpha and had to  uninstall then installed from synaptic and all is working fine.

Good Luck

---

### Post by olavjunior on 2007-02-21
I have the exact same problem!

I installed Amarok thru synaptics. 

WHY???? (gxine and Rhythmbox plays flawlessly by the way)

EDIT: Solved. Look at this thread: [http://ubuntuforums.org/showthread.php?t=343295&highlight=sound-engine+plugins](http://ubuntuforums.org/showthread.php?t=343295&highlight=sound-engine+plugins)

---

