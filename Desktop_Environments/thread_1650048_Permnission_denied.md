---
title: "Permnission denied"
date: 2010-12-21
forum: Desktop Environments
---

### Post by smss on 2010-12-21
Hi
How to fix this erorr:
bash: ./configure: Permission denied.
I'm trying to compile a program language C Plus Plus by the command . /configure.
 But I am faced with this error:
 bash:. / configure: Permission denied
 I had seen that person before the problem was resolved by ordering Chmd.
 Examples:
 chmd -R 777 [file name]
 This command does not work for me!
 And I think that should be the first command with other commands to install.
Or use this command before other commands require.

---

### Post by karthick87 on 2010-12-21
It is not chmd,it is chmod

```
chmod -R 777 [file name]
```

---

### Post by smss on 2010-12-21
Oh!
Ok!
 Typing mistake here and I apologize.
 I mean this is the chmod command does not work!

---

### Post by karthick87 on 2010-12-21
You can use sudo in-front of the command to get rid of that error..Or you have to change the owner of the file using chown.

Have a look at this [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

