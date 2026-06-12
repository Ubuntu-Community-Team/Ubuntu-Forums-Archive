---
title: "need help about redirection operator"
date: 2009-02-11
forum: General Help
---

### Post by vasudev on 2009-02-11
Hi

When try to execute following command on my terminal

**$ sudo cat myfile1.txt > myfile2.txt**

if gives the following error....

[COLOR="Red"]bash: myfile2.txt: Permission denied[/COLOR]

can anybody please rectify this problem...

thanks in advance

---

### Post by otrojake on 2009-02-11
Instead of using sudo to execute the command, just log in as root to do it.  Just do ```
su
```
to log in as root and then ```
cat myfile1.txt > myfile2.txt
```

That should work.

---

### Post by Old *ix Geek on 2009-02-11
You don't have 'write' permission in the directory you're in.  If you change the destination directory of the file, e.g. to your home directory:

```
$ sudo cat myfile1.txt > ~/myfile2.txt
```

it should work.  CAUTION: If there's already a file named **myfile2.txt** in your home directory, this will OVERWRITE it.

---

### Post by geirha on 2009-02-11
When you do "sudo cat ..." only the cat command is run with elevated privileges. The shell still runs as your user, and it is the shell that interprets the redirections, thus your user needs to have write access to the file (or the directory if the file doesn't already exist)

To write to the file with elevated privileges, you can use tee.
```
cat myfile1.txt | sudo tee myfile2.txt
# or shorter
sudo tee myfile2.txt < myfile1.txt

```
Note that tee outputs the input both to standard output and to the file you specify. If you don't want the file's content shown on standard out, redirect it to /dev/null
```
sudo tee myfile2.txt < myfile1.txt > /dev/null
```

---

### Post by vasudev on 2009-02-11
Thanks to all of you.... its worked :)

---

