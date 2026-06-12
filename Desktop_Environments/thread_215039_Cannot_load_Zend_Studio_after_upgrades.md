---
title: "Cannot load Zend Studio after upgrades"
date: 2006-07-13
forum: Desktop Environments
---

### Post by OneSeventeen on 2006-07-13
I just ran all the Ubuntu updates, and now I can't start the Zend Development Environment (Zend Studio).

If I try to launch it from the command line using ./:```
chris@gimli:~/ZendStudio-5.2.0$ ./Zend_Development_Environment
bash: ./Zend_Development_Environment: /bin/sh: bad interpreter: Permission denied
chris@gimli:~/ZendStudio-5.2.0$

```

Weird, huh?  similar stuff happens to other shell scripts that call perl and python...

Now, if I try to launch it with sh:```
chris@gimli:~/ZendStudio-5.2.0$ sh Zend_Development_Environment
Zend_Development_Environment: line 1708: /home/chris/Documents/Apps/Zend/ZendStudio-5.2.0/jre/bin/java: Permission denied
Zend_Development_Environment: line 1708: /home/chris/Documents/Apps/Zend/ZendStudio-5.2.0/jre/bin/java: Success
chris@gimli:~/ZendStudio-5.2.0$

```

If I try sudo sh, I get the same results as without sudo.

Any ideas?  Do I need to reinstall the Zend Studio?  If so, will I lose my projects?  Will I have to re-configure everything?  Do I need to uninstall it first?

---

### Post by OneSeventeen on 2006-07-17
I've found the solution, and the problem wasn't directly caused by the upgrades.  I mounted a spare partition as my Documents Folder (which is where ZDE is installed), and didn't give myself the proper permissions, I have since added execute permissions to the Documents folder, making my new line in fstab:```
/dev/sda2       /home/oneseventeen/Documents ext3 defaults,errors=remount-ro,user,exec,rw 0    1
```
It was previously:```
/dev/sda2       /home/oneseventeen/Documents ext3 defaults,errors=remount-ro,user 0    1
```
(note the absense of "exec,rw" in the original)

I have no idea how it worked in the past... maybe an update to fstab causes "defaults" to not include execute whereas in the past it was included... or perhaps I manually mounted the partition and hadn't rebooted sometime...

either way, it was caused by not having execute permissions on the volume, even though I had them on the file.  Kind of weird, but understandable.

Doh!

---

