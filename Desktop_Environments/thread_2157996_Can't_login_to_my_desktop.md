---
title: "Can't login to my desktop"
date: 2013-06-27
forum: Desktop Environments
---

### Post by FahadMKS on 2013-06-27
Hi,

I am using the Ubuntu 13.04 32 bit os on my Toshiba laptop. Now the problem is that I am unable to login to the desktop via GUI. The login screen to enter my password shows up and when I enter the password and go for it, the screen gets blank and goes back to the login window.

Please do help me with the issue.

Using an AMD processor.

---

### Post by android4682 on 2013-06-27
> **FahadMKS said:**
> Hi,

I am using the Ubuntu 13.04 32 bit os on my Toshiba laptop. Now the problem is that I am unable to login to the desktop via GUI. The login screen to enter my password shows up and when I enter the password and go for it, the screen gets blank and goes back to the login window.

Please do help me with the issue.

Using an AMD processor.

Can you log in via terminal? (ALT + F1)

---

### Post by FahadMKS on 2013-06-27
yes.. by pressing Ctrl +Alt+F1

---

### Post by steeldriver on 2013-06-27
Use Ctrl-Alt-F1, log in with your regular username and password, then type

```
ls -l ~/.{ICE,X}authority
```

Both files (if they exist) should be owned by you (not root) 

Another possible cause is if your home dir is not writeable by you

```
ls -ld ~
```

or if your home partition (or root partition, if you don't have a separate home) is full

```
df -h
```

---

### Post by FahadMKS on 2013-06-27
Typing the first command you gave me showed that both the files dispalyed was owned by myself.
(-rw------------ 1 username username 69324 JUN Time .Xauthority)

Using the ls -ld gave the reply
(dr-xr--r-- 39 username username 36864 jun Time)

---

### Post by Bashing-om on 2013-06-27
FahadMKS; Hi !

Wow, unusual and not at all the expected result.
However, I see that the directory is not "writable" !
my output:
> sysop@1304mini:~$ ls -ld ~
drwxr-xr-x 21 sysop sysop 4096 Jun 27 20:38 /home/sysop
sysop@1304mini:~$ 
So to change it such that you the "owner" may write to that disk:
```
chmod 755 /home/user-name/
```where user-name is your actual "user-name".
I do not think one wants to elevate one's privileges [sudo] in this instance as this is your home directory and using [sudo]may have unwanted side-effects... nor do you want to do this "recursively" as some files do -in your home directory- in fact belong to root. 
Hopefully will not have to go any deeper.

There is a reason that the directory's access rights are changed !
Is the disk full as steeldriver asked ?

And also lets see if the Xauthority variable is set.
```
 echo $XAUTHORITY
```

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

