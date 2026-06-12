---
title: "Run as SU always"
date: 2006-07-31
forum: Desktop Environments
---

### Post by Tyler5690 on 2006-07-31
I have Dapper installed on a virtual machine.  Security isn't an issue for me.  I was wondering if there is a way to run everything as SU all the time, so I don't have to keep entering my password. Is this possible?

---

### Post by jasutton on 2006-07-31
Well, the root account is disabled by default, however, it's not hard to set a password for it:

```
sudo passwd root
```

Once you do that, you should be able to login with the root account (which would have the effect of being su'd all the time).

You may also need to edit '/etc/gdm/gdm.conf' and set the 'AllowRoot=true' variable (this allows root to login to a graphical terminal), assuming you're using GDM as your login manager (default for Ubuntu).  If you're using KDM as your login manager (default for Kubuntu), you'll need to edit '/etc/kde3/kdm/kdmrc' instead and set the 'AllowRootLogin=true' variable.

---

### Post by ciscosurfer on 2006-07-31
I would first [read this]("http://www.tuxmagazine.com/node/1000148") to understand the difference between sudo and su.  

Here's [another one]("http://ubuntuforums.org/showthread.php?t=182983&highlight=run+su+background") for you.  And yet [another]("http://ubuntuforums.org/showthread.php?t=171677&highlight=run+su+background"), and [another]("http://ubuntuforums.org/showthread.php?t=25296&highlight=run+su+background").  

If security is not an issue, then here's a quick way to [fix your problem]("http://ubuntuguide.org/wiki/Dapper#How_to_use_.22sudo.22_without_prompt_for_password_.28not_secure.29") and [look here]("http://ubuntuguide.org/wiki/Dapper#How_to_explicitly_destroy_the_.22sudo.22_session") as well.

Here is info from Ubuntu documentation on being [root and sudo]("https://help.ubuntu.com/community/RootSudo").

If you'd like a quick and dirty way to run an x-term session as root, enter this in a terminal```
/usr/bin/gksu -u root /usr/bin/x-terminal-emulator
```Hope this helps! :D

---

### Post by ardchoille on 2006-07-31
If you run as su all the time, it's only a matter of time before someone breaks into your user account - or you end up downloading a file with a rootkit in it - then, it's quite easy for them to destroy the entire OS with:  rm -rf /

If the computer isn't connected to anything except the electical outlet, then it isn't much of a problem. But, if the computer is connected to any type of network, running as su all the time is sooner or later going to come back and bite you when you least expect it.

there's a reason that Ubuntu is setup the way it is.

---

