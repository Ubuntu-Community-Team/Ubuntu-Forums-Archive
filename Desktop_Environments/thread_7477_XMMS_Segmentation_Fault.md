---
title: "XMMS Segmentation Fault"
date: 2004-12-07
forum: Desktop Environments
---

### Post by berma on 2004-12-07
Hi!

Does anybody have an idea why my xmms shows the following msg for me:
Segmentation Fault.

It has worked for me, but since today not.
Where can I found solution for this problem?

Thx

---

### Post by p!=f on 2004-12-08
I've seen updated XMMS package yesterday which might solve your problem. 
If not try to strace XMMS by:
```

sudo strace xmms

```
Post last 20 lines here.

---

### Post by gaaruto.2k80 on 2004-12-15
i have the same problem :(
do you have resolve this bug ?
bye

---

### Post by maus on 2004-12-15
[QUOTE=p!=f]I've seen updated XMMS package yesterday which might solve your problem. 
If not try to strace XMMS by:
```

sudo strace xmms

```
Post last 20 lines here.[/QUOTE]
 Also having the same problem, here's the end of the strace output:

```
old_mmap(NULL, 5588, PROT_READ|PROT_EXEC, MAP_PRIVATE, 9, 0) = 0xb689e000
old_mmap(0xb689f000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED, 9, 0) = 0xb689f000
close(9)                                = 0
mprotect(0xb689e000, 4096, PROT_READ|PROT_WRITE) = 0
mprotect(0xb689e000, 4096, PROT_READ|PROT_EXEC) = 0
mprotect(0xb68a0000, 7081984, PROT_READ|PROT_WRITE) = 0
mprotect(0xb68a0000, 7081984, PROT_READ|PROT_EXEC) = 0
mprotect(0xb6f91000, 380928, PROT_READ|PROT_WRITE) = 0
mprotect(0xb6f91000, 380928, PROT_READ|PROT_EXEC) = 0
munmap(0xb6fff000, 47091)               = 0
open("/dev/zero", O_RDWR)               = 9
mmap2(NULL, 1024, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE, 9, 0) = 0xb700a00 0
close(9)                                = 0
getpid()                                = 28080
mmap2(NULL, 688128, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x b67f6000
getpid()                                = 28080
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++

```

---

### Post by p!=f on 2004-12-15
Do you run Warty or Hoary?

---

### Post by gaaruto.2k80 on 2004-12-15
[QUOTE=p!=f]Do you run Warty or Hoary?[/QUOTE]

i have the same lines with sudo strace xmms
i am under hoary
all works except xmms :(
no xmms plugins installed

---

### Post by gaaruto.2k80 on 2004-12-16
after a dist-upgrade, it has resolv my problem
just do : 
- sudo apt-get update
- sudo apt-get dist-upgrade

patches has been installed, it work now

thanks for the channel #ubuntu on irc.freenode.net

---

### Post by Mr Frosti on 2005-07-20
I would try to run the following programs resulting in "Segmentation Fault" as the output on the terminal:

xmms
openoffice
ooffice -writer
3ddeskd

These were the applications that were running when I restarted xorg forcefully using the "Ctl + Alt + Backspace" keyboard sequence. It was after xorg restarted that I noticed this problem first occuring. 

Taking "gaaruto.2k80"'s suggestion, I ran the following commands:

```
sudo apt-get update
sudo apt-get dist-upgrade
``` 

This has resolved the issue that I was having with all programs. This saved me from an operating system reload!

---

