---
title: "synaptic package manager wont accept my user (that is sudo authorized) password :("
date: 2009-01-15
forum: General Help
---

### Post by kraymore on 2009-01-15
in Ubuntu synaptic wont accept my user that has administrative privileges password (can sudo) password, and i'm sure i've typed it correctly many many times.  i can however, use sudo apt-get update and sudo apt-get install/upgrade.  any ideas how i can adjust synaptic ?

---

### Post by estyles on 2009-01-15
It doesn't make too much sense...  you are typing the same password into the password box that comes up from synaptic as you are when you "sudo apt-get" from the commandline?  And the commandline works?

Try "gksu gedit" - that should pop up the exact same password box as what synaptic pops up, and see if it works.

Also, check your sudoers file.  I think it's located at /etc/sudoers, but that might be way off - not on Ubuntu now and can't check.  You might want to post the contents of that file, but make sure you eliminate anything in there that might be considered identifiable (I don't think there's anything too dangerous in there - just your username, but it doesn't hurt to check).

---

### Post by fragos on 2009-01-15
I assume by administrative privlidges you mean member of the "admin" user group. The user created during install is automatically a member of "admin". All other users must be manually added.

---

### Post by electrogeist on 2009-01-15
I was going to suggest the "wheel" group... however on my Ubuntu 8.04 install I don't seem to have a wheel group in /etc/group... was this renamed to "admin" group?

---

### Post by estyles on 2009-01-15
> **electrogeist said:**
> I was going to suggest the "wheel" group... however on my Ubuntu 8.04 install I don't seem to have a wheel group in /etc/group... was this renamed to "admin" group?

Yeah, I think that's right.  But if he's not part of the admin group, then he shouldn't be able to "sudo apt-get" either... That's why I'd like to see his sudoers file.

Also, if you can list the permissions on sudo, gksudo, and gksu, that might help as well.

Do "whereis gksu", etc., I'm guessing they're in /usr/bin, but I've never looked for them, so I don't know for sure.  Then do "ls -l /usr/bin/gksu" or wherever the actual location of them is.  If you can post your sudoers file and the output of "ls -l" for all 3 files, maybe it will shed some light on your problem?

---

