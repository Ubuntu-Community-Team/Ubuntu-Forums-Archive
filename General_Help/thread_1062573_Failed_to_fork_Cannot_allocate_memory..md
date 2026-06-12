---
title: "Failed to fork: Cannot allocate memory."
date: 2009-02-07
forum: General Help
---

### Post by arnicainthemembrane on 2009-02-07
All of a sudden, with no reason or warning, my computer can no longer save any photos or even transfer them from the Home Folder to the desktop to be worked on. I'm told:

Unable to run plug-in "jpeg"
(/usr/lib/gimp/2.0/plug-ins/jpeg)

Failed to fork (Cannot allocate memory)

And when I try to save an image I worked on before this problem arose it says:

Saving '/home/arnica/Photos/2009/02/07/img_0477 (Modified in GIMP Image Editor).jpg' failed:

JPEG image plug-in could not save image

I made certain I had room left in the hard drive (14gig) and I even deleted several image files just in case they were "taking up room" needed for new images. It didn't help.

Any help appreciated... thanks.

---

### Post by bettlebrox on 2009-02-07
>Failed to fork (Cannot allocate memory)
All your available RAM and swap-space is used up. What does the output from the "free" command show?

---

### Post by vnt87 on 2009-02-09
I also ran into this problem just now. It was normal this afternoon but now it keeps displaying this 'Failed to fork' thing whenever I try to do something.

This is my 'free' output:

```

             total       used       free     shared    buffers     cached
Mem:       2072260    1292604     779656          0      39520     576980
-/+ buffers/cache:     676104    1396156
Swap:            0          0          0


```

I don't really get it but I suppose this means I don't have any swap space or something. How do I fix it?

---

### Post by bettlebrox on 2009-02-11
Looks like you have about 700MB free. It's possible that your hitting some process limits. What does 'ulimit -a' show?

---

### Post by woutervanvliet on 2011-12-05
Since a few weeks, I've been getting the same message a lot while executing basically anything on the commandline. For no reason I am able to find out. Is there anybody out there with a bid on what might be the problem.

I've included some info on my system. Any help is very much appreciated!

wouter@thriller:~$ uname -a
Linux thriller 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


wouter@thriller:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7929       6832       1096          0        805        837
-/+ buffers/cache:       5190       2739
Swap:         1609         41       1568


wouter@thriller:~$ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 63270
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 63270
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

wouter@thriller:~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

---

### Post by chrone on 2012-01-30
i also sometimes experience this bug when try to copy one file to another using the cp command via ssh.

>  free -m
             total       used       free     shared    buffers     cached
Mem:          7997       6404       1592          0        313       4273
-/+ buffers/cache:       1818       6179
Swap:         8184          0       8184


---

