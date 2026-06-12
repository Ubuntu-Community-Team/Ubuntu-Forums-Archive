---
title: "Unable to start some binaries"
date: 2009-02-21
forum: General Help
---

### Post by phenest on 2009-02-21
This is weird because it used to work ok. I recently reinstalled Ubuntu and get the same error (more or less) for 2 applications.

I installed lightscribe with the lightscribe drivers and the 4L app. When I try to run 4L, I get the error dialog:
```
Failed to execute child process "4L-gui" (No such file or directory)
```

If I try to run the 4L binary from a terminal, I get:
```
steve@precision:~$ cd /usr/4L/
steve@precision:/usr/4L$ ./4L-gui 
bash: ./4L-gui: No such file or directory
steve@precision:/usr/4L$ 

```

I also have super pi from doing benchmark tests and that gives the same error.

I don't understand.

---

### Post by taurus on 2009-02-21
While you are still in the /usr/4L directory, post the output of this command here.

```
ls -la
```

---

### Post by phenest on 2009-02-21
```
steve@precision:/usr/4L$ ls -la
total 6276
drwxr-xr-x  5 root root    4096 2009-02-17 13:28 .
drwxr-xr-x 12 root root    4096 2009-02-15 19:44 ..
-rwxr-xr-x  1 root root   60540 2006-08-10 14:20 4L-cli
-rwxr-xr-x  1 root root 6320572 2006-08-10 14:20 4L-gui
drwxr-xr-x  2 root root    4096 2009-02-17 13:28 doc
-rwxr-xr-x  1 root root    2562 2006-08-10 14:20 lacie_website.sh
drwxr-xr-x  2 root root    4096 2009-02-17 13:28 templates
drwxr-xr-x  2 root root    4096 2009-02-17 13:28 translations
steve@precision:/usr/4L$
```

---

### Post by taurus on 2009-02-21
How about

```
file 4L-gui
uname -a
```

---

### Post by phenest on 2009-02-21
```
steve@precision:/usr/4L$ file 4L-gui 
4L-gui: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.6, dynamically linked (uses shared libs), stripped
steve@precision:/usr/4L$ uname -a
Linux precision 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux
steve@precision:/usr/4L$ 

```

---

### Post by taurus on 2009-02-21
> **phenest said:**
> ```
steve@precision:/usr/4L$ file 4L-gui 
4L-gui: **[COLOR="Red"]ELF 32-bit LSB executable[/COLOR]**, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.6, dynamically linked (uses shared libs), stripped
steve@precision:/usr/4L$ uname -a
Linux precision 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 **[COLOR="Red"]x86_64[/COLOR]** GNU/Linux
steve@precision:/usr/4L$ 

```

Well, there you go.  You are running x86_64 but 4L-gui is a 32bit binary so unless you install those 32bit libraries (lib32) on your machine first, you won't be able to run those 32bit apps.

---

### Post by phenest on 2009-02-21
Doh! I have to admit that I haven't installed all the packages that I would normally on a fresh install as I can't always spare the bandwidth.

What package do I need?

---

### Post by phenest on 2009-02-21
I got it...
```
sudo apt-get install ia32-libs
```

Thanks for your help

Incidentally, I actually thought that the 32 bit libraries were part of the installation on 64 bit.

---

