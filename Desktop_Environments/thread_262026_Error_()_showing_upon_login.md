---
title: "Error (?) showing upon login"
date: 2006-09-21
forum: Desktop Environments
---

### Post by Jabbadahut on 2006-09-21
Hello fellow Ubuntu users.  I use the AMD 64-bit version of Ubuntu 6.06, and for awhile I've been getting the following message from the system after I login, as follows:

```


User's $Home/.dmrc file is being ignored.  This prevents the default session and language from being saved.

File should be owned by user and have 644 permissions.  User's $Home directory must be owned by user and not writable by other users.


```

I click on 'OK', and the desktop loads.  Everything seems to be working fine.  I might've done something that caused this message when I was configuring the system as I wanted it after I installed the OS, but I cannot remember what as it was a few weeks ago.

How can I resolve this 'problem' (if it is one), or is this something I shouldn't be concerned about?

---

### Post by sktx on 2006-09-21
Maybe your permissions are screwed up for the .dmrc file? Open up a terminal and enter....
```
ls -la |grep .dmrc
```
...and post the output here, if you would. :)


..*sktx*

---

### Post by Ramses de Norre on 2006-09-21
```
sudo chown `whoami`:`whoami` .dmrc && chmod 644 .dmrc
```

---

### Post by sktx on 2006-09-21
Yeah, what he said. :D

..*sktx*

---

