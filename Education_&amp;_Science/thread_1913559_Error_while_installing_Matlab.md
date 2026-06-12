---
title: "Error while installing Matlab"
date: 2012-01-22
forum: Education &amp; Science
---

### Post by bjarkith on 2012-01-22
Hey, I'm trying to install Matlab 2010a for my engineering class but I always get the same error about a needed font for the xsetup when I try to install it.

```
john@doe:/media/MATHWORKS_R2011A$ sudo ./install
./install: 1156: /lib64/libc.so.6: not found

Extracting ftp files . . . [please wait]
Extracting matlab.common
Extracting matlab.glnxa64
Finished extracting ftp files.
Starting installer ...
-------------------------------------------------------------------

    The following messages were written to standard error
    while running 'xsetup' the X Window System version
    of 'install'.

        xsetup: Unable to load required font.

-------------------------------------------------------------------

```

I'v tried to install more fonts and googling the problem but I admit my defeat and come here, has anyone encountered this problem and if so how did he overcome it?

With thanks in advance!

---

### Post by entropy1 on 2012-01-22
Notice the first error is that libc.so.6 was not found.  The fix you need depends on which version of Ubuntu you are running.  For 11.04, I found the following posted on the web some time back.  For 64-bit Ubuntu,```
sudo ln -s /lib64/x86_64-linux-gnu/libc-2.13.so /lib64/libc.so.6
``` and for 32-bit Ubuntu, ```
sudo ln -s /lib/i386-linux-gnu/libc-2.13.so /lib/libc.so.6
```

You may need slightly different commands for other versions of Ubuntu; e.g., 11.10.

---

### Post by Claus7 on 2012-01-22
Hello,

I haven't faced your issue, yet from the info you provide I can see that:
./install: 1156: /lib64/libc.so.6: not found

EDIT:Follow *entropy1* advice!

forget this one:
so I guess that you have to install something that will cover this dependency. My humble opinion would be to go to synaptic, write this missing library, and install the corresponding libraries and then try anew the installation.

Regards!

---

### Post by bjarkith on 2012-01-23
I've been googling which fonts i need to download, but cant find any information about that. Does anybody know what i need to install?=)

---

### Post by entropy1 on 2012-01-23
You could try installing:

ttf-mscorefonts-installer

and

ttf-ubuntu-font-family

I don't know if that will help.  But you still need to fix the "/lib64/libc.so.6: not found" error

---

### Post by Paddy Landau on 2012-01-23
> **bjarkith said:**
> I've been googling which fonts i need to download, but cant find any information about that. Does anybody know what i need to install?=)
Did you do as instructed in [post #2]("http://ubuntuforums.org/showthread.php?p=11632672#post11632672")?

If not, please do so. If you have, please indicate your new problem.

---

### Post by bjarkith on 2012-01-23
Hey, tanks for the replies, I managed to get passed the libc error by chaning the installer to the correct directory of the libc file but the font problem still persists, I have installed both the ubuntu fonts and mscorefonts that you mentioned above but still get the font error.

---

### Post by MaWiSo on 2012-08-23
> **entropy1 said:**
> Notice the first error is that libc.so.6 was not found.  The fix you need depends on which version of Ubuntu you are running.  For 11.04, I found the following posted on the web some time back.  For 64-bit Ubuntu,```
sudo ln -s /lib64/x86_64-linux-gnu/libc-2.13.so /lib64/libc.so.6
``` and for 32-bit Ubuntu, ```
sudo ln -s /lib/i386-linux-gnu/libc-2.13.so /lib/libc.so.6
```

You may need slightly different commands for other versions of Ubuntu; e.g., 11.10.

I tried this on 12.04 and it still gives me the same error !!

---

