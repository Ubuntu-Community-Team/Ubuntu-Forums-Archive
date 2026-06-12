---
title: "Two Errors at Startup"
date: 2005-12-09
forum: General Help
---

### Post by nrwilk on 2005-12-09
I get these two errors at startup:

[[IMG]http://img204.imageshack.us/img204/3469/snapshot10jt.png[/IMG]](http://imageshack.us)

The ksplash error has to do with the KDE splash screen, which doesn't come up until after I've clicked the "close" button on the error.  When it does come up, it's only for a small bit, as KDE is already running by then.  I've no idea what kaccessrc is.

Any ideas to fix the issues?

the two files in question are both owned by root, and do not have any write permissions.  Should I just enable write permissions for root on the files?

---

### Post by claydoh on 2005-12-09
you will want to change the ownership of these files to your user

```
sudo chown -Rv <username>:<usrname> /home/<username>/.kde
``` will change the ownership of all the config files in ~/.kde
or to use Konq, try
```
sudo kfmclient exec .
``` then browse to the files and change ownership by right-clicking on each file.

If that does not work, you can safely delete them and they will be recreated during the next login

---

### Post by nrwilk on 2005-12-09
thanks for the easy fix!  Is there a reason why some of them weren't owned by me by default?  What could I have done to change them (I didn't do it explicitly)?

---

