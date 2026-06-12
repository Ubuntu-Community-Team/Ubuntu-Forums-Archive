---
title: "[SOLVED] Konqueror won't start"
date: 2008-11-30
forum: Desktop Environments
---

### Post by sofasurfer on 2008-11-30
When I start konqin terminal I get this...

```

daryl@ubuntu:~$ konqueror
trying to create local folder /home/daryl/.kde/share: Permission denied
trying to create local folder /home/daryl/.kde/share: Permission denied
trying to create local folder /home/daryl/.kde/cache-ubuntu: Permission denied
trying to create local folder /home/daryl/.kde/cache-ubuntu: Permission denied
trying to create local folder /home/daryl/.kde/cache-ubuntu: Permission denied
trying to create local folder /home/daryl/.kde/cache-ubuntu: Permission denied
trying to create local folder /home/daryl/.kde/tmp-ubuntu: Permission denied
trying to create local folder /home/daryl/.kde/tmp-ubuntu: Permission denied
trying to create local folder /home/daryl/.kde/tmp-ubuntu: Permission denied
trying to create local folder /home/daryl/.kde/tmp-ubuntu: Permission denied
trying to create local folder /home/daryl/.kde/tmp-ubuntu: Permission denied
trying to create local folder /home/daryl/.kde/share: Permission denied
konqueror(7986): Failed to lock file "/home/daryl/.kde/cache-ubuntu/kpc/kde-icon-cache.lock" , last result = 2 
konqueror(7986): Couldn't create index file "/home/daryl/.kde/cache-ubuntu/kpc/kde-icon-cache.index" 
trying to create local folder /home/daryl/.kde/share: Permission denied
trying to create local folder /home/daryl/.kde/share: Permission denied
trying to create local folder /home/daryl/.kde/share: Permission denied
trying to create local folder /home/daryl/.kde/share: Permission denied
trying to create local folder /home/daryl/.kde/share: Permission denied
trying to create local folder /home/daryl/.kde/share: Permission denied
trying to create local folder /home/daryl/.kde/cache-ubuntu: Permission denied
trying to create local folder /home/daryl/.kde/cache-ubuntu: Permission denied
trying to create local folder /home/daryl/.kde/cache-ubuntu: Permission denied
trying to create local folder /home/daryl/.kde/cache-ubuntu: Permission denied
trying to create local folder /home/daryl/.kde/tmp-ubuntu: Permission denied
trying to create local folder /home/daryl/.kde/tmp-ubuntu: Permission denied
trying to create local folder /home/daryl/.kde/tmp-ubuntu: Permission denied
trying to create local folder /home/daryl/.kde/tmp-ubuntu: Permission denied
trying to create local folder /home/daryl/.kde/tmp-ubuntu: Permission denied
trying to create local folder /home/daryl/.kde/share: Permission denied
kdialog(7988): Failed to lock file "/home/daryl/.kde/cache-ubuntu/kpc/kde-icon-cache.lock" , last result = 2 
kdialog(7988): Couldn't create index file "/home/daryl/.kde/cache-ubuntu/kpc/kde-icon-cache.index" 
trying to create local folder /home/daryl/.kde/share: Permission denied
trying to create local folder /home/daryl/.kde/share: Permission denied
trying to create local folder /home/daryl/.kde/share: Permission denied
trying to create local folder /home/daryl/.kde/share: Permission denied


```
And then this message pops up...

Configuration file "/home/daryl/.kde/share/config/knotifyrc" not writable.
Please contact your system administrator.

I've tried uninstalling and reinstalling with no improvement.

---

### Post by p_quarles on 2008-11-30
Can you post the output of this?:
```
ls -lh ~/.kde/
```
That will display the permissions of the directory causing trouble, and hopefully lead to a diagnosis.

---

### Post by sofasurfer on 2008-11-30
daryl@ubuntu:~$ ls -lh ~/.kde/
ls: cannot open directory /home/daryl/.kde/: Permission denied

daryl@ubuntu:~$ sudo ls -lh ~/.kde/
[sudo] password for daryl: 
total 16K
drwx------ 3 root root 4.0K 2008-11-30 02:27 cache-ubuntu
drwx------ 6 root root 4.0K 2008-11-29 20:35 share
drwx------ 2 root root 4.0K 2008-11-30 02:38 socket-ubuntu
drwx------ 3 root root 4.0K 2008-11-30 02:33 tmp-ubuntu

Ok, I bet your going to say I need to change permissions on this directory.  But I have installed konqueror many times, with no trouble. Why did it install with the wrong permissions this time?

By the way, there is no /home/daryl/.kde/share/config/knotifyrc. Or is the problem that because of permissions, /knotifyrc can not be created?

---

### Post by p_quarles on 2008-11-30
> **sofasurfer said:**
> Ok, I bet your going to say I need to change permissions on this directory.
Yes. Try:
```
sudo chown -R `whoami` ~/.kde
```

> But I have installed konqueror many times, with no trouble. Why did it install with the wrong permissions this time?
On that count, I am as puzzled as you are.

---

### Post by sofasurfer on 2008-11-30
Ok, I mage myself owner of ./kde and gave myself all read/write access and applied it to all subfolders. That fixed my problem. 
Still wanna know why it happened though.

---

