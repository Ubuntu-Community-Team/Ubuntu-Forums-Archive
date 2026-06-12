---
title: "Konqueror: error changing permissions of multiple files"
date: 2006-01-19
forum: Desktop Environments
---

### Post by MartinJ on 2006-01-19
This has been annoying me for a while, but haven't found a solution yet.  I'm using Kubuntu 5.10 with KDE 3.5.

If I try to change the file permissions for a single file using Konqueror I get an error message with the text "/home/msj/*filename*".  However, the permissions are changed correctly.

If I try to change the permissions for several files I get the same error message but only the file listed in the error message has changed permissions.  For example, I have testfiles1, 2 and 3.  I select them all, choose the new permissions, press OK and the error message shows "/home/msj/testfile3".  Testfile3 has new permissions but testfiles1 and 2 are unaffected.

Using chmod from the command line works perfectly.  Any idea how to fix this?

Thanks in advance.

---

### Post by MartinJ on 2006-01-26
Still haven't found a solution.

More details on this KDE-forum thread:
[http://www.kde-forum.org/artikel/14058/Problem-with-permission-in-kDE35.html](http://www.kde-forum.org/artikel/14058/Problem-with-permission-in-kDE35.html)

---

### Post by Divan Santana on 2006-01-27
Doesn't work for me either! I have to use chmod -R or chown -R when trying to change permission or ownership. Prob some bug...

---

### Post by MartinJ on 2006-02-01
Fixed by adding acl to the options for each partition in the /etc/fstab file.
```
/dev/hda2 / ext3 defaults,**acl**,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hda5 /home ext3 defaults,**acl**,atime,auto,rw,dev,exec,suid,nouser 0 2
```

---

