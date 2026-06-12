---
title: "help, i hosed my apt !"
date: 2006-08-08
forum: Desktop Environments
---

### Post by nephish on 2006-08-08
ok, i did a stupid thing. i installed jedit from the repositories. But then, i downloaded the jedit (newer, test release) .deb. not thinking that it may not be compatible.
so it messed up on install, now i cannot remove it, or the old version.
here is what i get.
```

dpkg -i jedit_4.3pre6_all.deb
dpkg: requested operation requires superuser privilege
nephish@bitsbam:~$ sudo su
Password:
root@bitsbam:/home/nephish# dpkg -i jedit_4.3pre6_all.deb
(Reading database ... 92556 files and directories currently installed.)
Preparing to replace jedit 4:04.03.06.00 (using jedit_4.3pre6_all.deb) ...
Unpacking replacement jedit ...
dpkg (subprocess): unable to execute old post-removal script: No such file or directory
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new post-removal script: No such file or directory
dpkg: error processing jedit_4.3pre6_all.deb (--install):
 subprocess new post-removal script returned error exit status 2
dpkg (subprocess): unable to execute new post-removal script: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 jedit_4.3pre6_all.deb
```


then, if i try to get rid of it...```

dpkg -r jedit
dpkg: error processing jedit (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 jedit
```

or ```

dpkg -P jedit
dpkg: error processing jedit (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 jedit
```

anyone know how to get me outta this? apt is hosed till i get this fixed
thanks

---

### Post by nephish on 2006-08-08
ok, fixed. You know they say search before you ask, i did not search long enough. The fix to this, and i suppose many other problems with goofy packages can be found [here]("http://ubuntuforums.org/showthread.php?p=1356454#post1356454")

---

