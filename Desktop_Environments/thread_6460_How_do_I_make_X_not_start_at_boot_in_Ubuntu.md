---
title: "How do I make X not start at boot in Ubuntu?"
date: 2004-11-28
forum: Desktop Environments
---

### Post by UnixDaemon on 2004-11-28
Okay, I went to my inittab file and changed the run level to 3 like I would do in slackware or another distro to stop it from starting X at boot, and well, that didn't do anything, just kept everything the same, so I was wondering how I would go about doing this in Ubuntu since things are configured slightly differently, I notice my X is much more stable when I run it this way, and I hate killing my X every boot and then starting X from the command line to get the same effect, any help would be great, thanks

---

### Post by scoon on 2004-11-28
Hey there, 

Keep inittab set to 3 and also do a man for update-rc.d.  You want to remove gdm or xdm from starting during boot. 

scoon

---

### Post by Magneto on 2004-11-28
[QUOTE=UnixDaemon]Okay, I went to my inittab file and changed the run level to 3 like I would do in slackware or another distro to stop it from starting X at boot, and well, that didn't do anything, just kept everything the same, so I was wondering how I would go about doing this in Ubuntu since things are configured slightly differently, I notice my X is much more stable when I run it this way, and I hate killing my X every boot and then starting X from the command line to get the same effect, any help would be great, thanks[/QUOTE]
 just like the /etc/rc.d directory in slack  the /etc/rc2.d /etc/rc3.d  etc directories contain the startup scripts for each runlevel- gdm starts x with ubuntu so remove execute permissions from s20gdm or whatever it is or  man update-rc.d

edit**left the window open too long before posting not tryin to be redundant

---

### Post by UnixDaemon on 2004-11-28
yep that did it, thanks guys ;)

---

### Post by simoncullen on 2005-08-25
I've got the opposite problem!  For some reason mine has stopped loading X at boot-- it just goes to a terminal and then startx.  But the annoying thing is that I've lost the options to suspend, reboot, etc, from the Gnome menu --System-->Logout.  I'm using Hedgehog.  Any ideas?

Thanks,
Simon

---

