---
title: "vmware server install issue"
date: 2006-07-31
forum: Desktop Environments
---

### Post by vangheem on 2006-07-31
Hi, I'm trying to install vmware server, but every time I try to invoke the install script(./vmware-install.pl) I get this error.

```
 A previous installation of VMware software has been detected.

Failure

Execution aborted.

```

But I did "sudo apt-get remove vmware-player" and it is indeed not on the system.  However, I did find remnants of a previous install that wasn't from apt.  How do I get rid of the old vmware files so I can install the server product?  Is there anywhere that an uninstall script can be found?

---

### Post by Ziox on 2006-07-31
sudo aptitude purge vmware-player get rid off all the config files

---

### Post by vangheem on 2006-07-31
I've tried that and I'm still getting the same error.  I really don't understand why.  Rather cumbersome.  I didn't think an install would be this annoying.

I think when I installed vmware-player myself earlier I screwed up something.  I guess it isn't a huge deal.  I can still get vmware-player working again if I need it.  It is just that vmware server looks like a better program.

Any other ideas?

---

### Post by Ziox on 2006-07-31
yeah i have an idea, did you check you home/usrname directory for any VMware Hidden files? (Folders that start with a ".") hit Ctrl+H to see them

---

### Post by vangheem on 2006-07-31
I found I did have a ".vmware" directory in my home and I removed only to find this didn't help either.

Thanks for helping though.

---

### Post by XaeroDegreaz on 2006-08-30
Please read my other post. I have solved this same problem you have.

[http://www.ubuntuforums.org/showthread.php?t=236491&page=2](http://www.ubuntuforums.org/showthread.php?t=236491&page=2)

---

