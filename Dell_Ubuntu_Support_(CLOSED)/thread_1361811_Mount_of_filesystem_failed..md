---
title: "Mount of filesystem failed."
date: 2009-12-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by BenW on 2009-12-22
Hello,

I recently installed ubuntu on my laptop as well as one of my teachers and we both have the same issue. I made a Dell Recovery CD from the guide in these forums and used that to install ubuntu on my laptop. My teachers just used the origonal cd. We both are using 9.10

So what do I do? My teacher already reinstalled Ubuntu on his laptop but I have some documents I need to get off before I can do anything.

Here is the error we are getting

```
Mount of filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
Give root password for maintenance
(or type Control-D to continue):
```

After I hit Control-D

```
mountasll start/starting
fsck from util-linux-ng 2.16
/dev/sda1 contains a file with system errors, check forced.
swapon: /dev/desk/by-uuid/s0d3f0fb-ea7c-4cd9-886e-ea4d8365f39f: swapon failed: Device of resource busy
mountall: swapon /dev/desk/by-uuid/s0d3f0fb-ea7c-4cd9-886e-ea4d8365f39f [778] terminated with statue 225
mountall: Problem activating swap: /dev/desk/by-uuid/s0d3f0fb-ea7c-4cd9-886e-ea4d8365f39f
/dev/sda1: Inode 7 has illegal block(s).

/dev/sda1: UNEXPECTED INCONSISTENCY RUN dsck MANUALLY
(i.e., without -a or -p options)
mountall: fsck / [776] terminated with status 4
mountall: Filesyystem has errors: /
init: mountall main process (775) terminated with status 3
Mount of filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
Give root password for maintenance
(or type Control-D to continue):

```

after I type in my root password
```
root@bens-laptop:~#
```

---

### Post by BenW on 2009-12-22
Nevermind I fixed it. I ran fsck and every time it asked me if I wanted something fixed I just hit Y.

So I know how to fix it, how do I prevent this problem from coming back?

---

### Post by ZaHACKieL on 2010-01-24
> **BenW said:**
> Nevermind I fixed it. I ran fsck and every time it asked me if I wanted something fixed I just hit Y.

So I know how to fix it, how do I prevent this problem from coming back?

I saw this on another post [http://greative.net/index.php/2010/01/solution-mount-file-system-failed-problem-ubuntu-910-karmic-koala/](http://greative.net/index.php/2010/01/solution-mount-file-system-failed-problem-ubuntu-910-karmic-koala/)

I also had that problem but I didn't use that solution. My problem was that my system date, somehow, changed by itself to a date in the past (to 2 years ago) so the last mount was dated in the future.

I changed the date to the current one and problem solved.

---

