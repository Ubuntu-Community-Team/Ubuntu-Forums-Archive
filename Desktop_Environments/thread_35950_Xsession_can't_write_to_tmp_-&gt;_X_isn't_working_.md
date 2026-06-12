---
title: "Xsession can't write to /tmp -&gt; X isn't working at all"
date: 2005-05-21
forum: Desktop Environments
---

### Post by kerinin on 2005-05-21
someone else has had the same problem i'm having ([here](http://www.ubuntuforums.org/showthread.php?t=18559&highlight=xsession+unable+write)), but the problem seems to be unresolved and the thread was closed, so i'm starting a new thread now that the problem has happened twice.

after installing some packages and other software and rebooting, i get an error message that reads "Xsession: warning: unable to write to /tmp; X session may exit with an error", and then it exits.  the error occurs just after loggin in, and happens regardless of which window manager i use (i've tried gnome, kde, and xfce).

my hard drive is pretty full, and according to [one person](http://www.svenkrahn.de/linux/my_debian/ar01s10.html) that's the problem, but i've deleted as much as i'm comfortable deleting (i'm still learning what all the files do) and it still doesn't work.

the specific packages i installed since the last reboot were azureus and a couple plugins (i2p i think), a few items from [this list](http://ubuntuguide.org) (J2SE, mozilla flashplayer, acroread, gparted, nessus, and rar), and the sun java packages as described [here](http://www.ubuntulinux.org/wiki/Java)

if anyone has any idea what's going on or how to fix it i'd really appreciate it.

thanks!

---

### Post by Xian on 2005-05-21
A couple of quick things;

* Clean out your apt cache with this command:
```
$ sudo apt-get clean
```

* Check for drive space with this command:
```
$ df -h
```

---

### Post by kerinin on 2005-05-21
[QUOTE=Xian]A couple of quick things;

* Clean out your apt cache with this command:
```
$ sudo apt-get clean
```

* Check for drive space with this command:
```
$ df -h
```[/QUOTE]
 i suspect that's the problem, my root partition is at 100%...

thanks!!!

---

### Post by theboatashore on 2006-06-24
I'm running Kubuntu Dapper on a Sony Vaio and I experienced this exact problem after using Automatix to install Azureus.  It's happened twice now.  The first time I solved the problem "Windows-style" and reinstalled the OS.  I'm keen not to do that again, well, because this is Linux and I shouldn't have to.

I get an additional message (when booting into Failsafe mode) not mentioned before:

[I]There was an error setting up inter-process communication for KDE.
The message returned by the system was:
Could not read network connection list
/home/michael/.DCOPserver_ronin__0
Please check that the "dcopserver" program is running.[/I]

I followed the previous post and found my root partition to be at 92% (with 237 MBavailable), so I can't see how a full root partition could be the problem.  I'm doing this after booting into Failsafe and running konqueror from the konsole, so I'm going to reboot now to see if clearing the cache made a difference.

*Note: I've just rebooted and it worked perfectly.  Could someone please explain how clearing the apt cache solved this problem?  Thanks for the advice.

---

