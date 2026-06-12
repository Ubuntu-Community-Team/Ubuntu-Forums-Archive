---
title: "bad interpreter: permission denied"
date: 2005-04-15
forum: Desktop Environments
---

### Post by jcs296 on 2005-04-15
Hi, I'm trying to get a variety of scripts to work (some bash, ruby, python, etc), but every time I run a script I get an error such as:

$ ./test
bash: ./test: /bin/bash: bad interpreter: Permission denied

where the file 'test' is:
#!/bin/bash
echo test

a similar message occurs for python, ruby, and  other scripts. these programs are all on the path and I've made no odd changes that I can think of to any settings. /bin/bash exists and is executable for all users.  any help is greatly appreciated, thank you!

---

### Post by wfx on 2005-04-15
> where the file 'test' is:
#!/bin/bash
echo test 
nothing wrong.

do: 
chmod +x test
./test

---

### Post by dusu on 2005-04-15
If you only want the user (ie you) to be able to execute test, type
```
chmod u+x test
```

---

### Post by jcs296 on 2005-04-15
The script 'test' was executable, as were all the other scripts that I tried when I got the same type of error. 

$ ls -l
-rwxr-xr-x  1 jcs296 jcs296 49 2005-04-14 23:30 test
$ ./test
bash: ./test: /bin/bash: bad interpreter: Permission denied

Any thoughts?

---

### Post by speedman on 2005-04-15
Is the file system that the scripts are stored on mounted with the noexec option by any chance?

Example:

chris@i8500:~ $ mount
/dev/hda1 on / type ext3 (rw,noatime,errors=remount-ro)

If noexec shows up inside the brackets for the partition that your scripts are on as a mount option then that would explain your problem.


Regards,

SM

---

### Post by jcs296 on 2005-04-15
it is indeed mounted noexec...i didn't know about that.  
my /etc/fstab entry for the drive is:

/dev/sda1       /media/usbdisk  auto    rw,user,noauto  0       0

how do i make the scripts executable? change it to rwx,user,noauto ?

thank you very much for the help!

---

### Post by speedman on 2005-04-16
[QUOTE=jcs296]how do i make the scripts executable? change it to rwx,user,noauto ?[/QUOTE]

Nope.  Try this:

/dev/sda1       /media/usbdisk  auto    rw,users,exec,noauto  0       0

HTH


Regards,

SM

---

