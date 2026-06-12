---
title: "Can't get 'sysv-rc-conf' to install"
date: 2006-01-21
forum: Desktop Environments
---

### Post by dodgeman79 on 2006-01-21
I would like to get 'sysv-rc-conf' installed to edit my startup and take off things I don't need. here is what I get;
```
root@WORKGROUP:/# sudo apt-get install sysv-rc-conf
Reading package lists... Done 
Building dependency tree... Done
Package sysv-rc-conf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sysv-rc-conf has no installation candidate

```

what do I need to install to get this to work?  I'm using this link [http://doc.gwos.org/index.php/Speed_up_boot](http://doc.gwos.org/index.php/Speed_up_boot).

---

### Post by slashem on 2006-01-21
Do you have universe in /etc/apt/sources.list ?

Read this:

[http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories)

Where it says hoary, change to breezy.

---

### Post by dodgeman79 on 2006-01-23
thanks for the link.   The repositories were the problem but I found a simpler method in the Synaptic Package Manager.  It works fine now and everything is up to date.

---

