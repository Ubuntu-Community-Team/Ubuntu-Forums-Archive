---
title: "Sudo is causing segmentation faults"
date: 2009-04-25
forum: General Help
---

### Post by russianzilla on 2009-04-25
I was trying to copy an icon theme into the shared icons folder on the computer when nautilus crashed. Now running anything with sudo produces a segmentation fault. I already tried a few solutions such as purging samba and checking permissions on the sudo folder. The error logs have this in them following sudo nautilus:
```
[  295.387091] nautilus[3801]: segfault at bdb3263c ip b7cb1704 sp bfc30350 error 4 in libgtk-x11-2.0.so.0.1600.1[b7bb7000+3a9000]

```
What should I do? Would it be safe to purge/reinstall libgtk?

EDIT: It looks like the seg fault error only occurs with graphical apps like Synaptic and Nautilus. Command-line-only like apt-get is fine.

---

### Post by sceptre0 on 2009-04-25
If you can access synaptic try reinstalling all the dependencies for sudo.  I believe I had the same problem.  Reinstalling libc6 did it for me.  The other dependencies are libpam0g, libpam-modules, and sudo-ldap.

Edit: Try running Ubuntu in recovery mode if you can't access synaptic.

---

### Post by russianzilla on 2009-04-25
Unfortunately that didn't work. I did it through recovery mode, but libpam0g wouldn't reinstall so I didn't touch it and I still can't use sudo.

EDIT: Alright, so I messed around a bit and figured out that I can actually use command-line programs like apt-get. Anything graphical such as Nautilus, Synaptic or Gedit won't open up and give that error in the first post.

---

### Post by sceptre0 on 2009-04-25
Here is a list of dependencies that are common to those 3 programs.

libatk1.0-0
libcairo2
libglib2.0-0
libgtk2.0-0
liblaunchpad-integration1
libpango1.0-0
libx11-6
libxml2

This thread is what helped me with segmentation faults.  [http://ubuntuforums.org/showthread.php?p=6267442](http://ubuntuforums.org/showthread.php?p=6267442)  It was samba that was the problem for me.  Is there anything in your log file?  /var/log/messages

---

### Post by russianzilla on 2009-04-25
The log file has the same errors as the one in the first post.

So should I just reinstall those dependencies or purge them?

EDIT: Wow, so this is bizarre. I solved the problem. It turned out to be my icon theme. Strange. Oh well, thanks for the help!

---

