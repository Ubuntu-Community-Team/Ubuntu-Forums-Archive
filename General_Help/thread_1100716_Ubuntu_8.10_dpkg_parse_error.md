---
title: "Ubuntu 8.10 dpkg parse error"
date: 2009-03-19
forum: General Help
---

### Post by Elrusso on 2009-03-19
I'm new to Linux, so bear with me. I'm using Ubuntu 8.10 32-bit and I can't install any updates or new programs. I keep getting this error when I try to update:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

I know lots of people have gotten this error, but none of their fixes seem to work for me. I try the sudo command, but get this:

elrusso@elrusso-desktop:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0017' near line 1:
 newline in field name `#padding'
 
When I locate and open this "0017" file it does indeed have some issues, with the first 20 or so lines just a repeat of "#padding". But it won't let me modify the file.

Also, I can't open Synaptic without getting the same dpkg error message and it auto closes. I can't run the update manager without getting this error either. I've also tried multiple fixes from recovery mode, but nothing fixes it.

I've been spending days scouring forums to find the answer, but where solutions work for other people it doesn't work for me. I'm running Ubuntu 8.10 32-bit version with Gigabyte K8N Pro-SLI. This is dual booting with Windows XP Professional 32-bit.

Any help would be much appreciated.

---

### Post by Elrusso on 2009-03-19
This is the error I get when I try to install updates from the update manager:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

very strange stuff, not sure what to do. I have also tried to reinstall Ubuntu using the Live CD, and it wouldn't complete the install saying something along the lines of: "No root file system is defined. Please correct this from the partitioning menu." But I suppose that's a different issue. I couldn't find anything about just doing an OS repair with the Live CD similar to Windows XP.

---

### Post by fieroboom on 2009-03-19
> **Elrusso said:**
> This is the error I get when I try to install updates from the update manager:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


If your live cd adventure didn't botch your current install, then all you need to do is press ALT+F2, type this in:
```
sudo dpkg --configure -a
```
Then, click the checkbox that says 'run in terminal', and press enter.
That should fix the issue.
:D
-Paul

---

### Post by jwernecke on 2009-03-21
I get the same dpkg was interupted blah blah... i go into xterm type sudo dpkg --configure -a hit enter and it pops up with this parse error on update file 1048 when i go into the update file it is doing the same #padding about 300 times and i cant modify it or delete it.  What do I need to do to fix this issue.  Thanks guys

---

### Post by Endolith on 2009-04-07
I installed a LiveCD environment on a USB stick using [portablelinux]("http://rudd-o.com/new-projects/portablelinux").  Then it tried to upgrade, and the upgrade broke in the middle, probably from running out of disk space/memory? Now everything crashes, and it says ```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

``````
 ~> sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0182' near line 1:
 newline in field name `#padding'
```

---

