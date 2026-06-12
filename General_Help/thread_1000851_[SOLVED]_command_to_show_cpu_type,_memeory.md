---
title: "[SOLVED] command to show cpu type, memeory?"
date: 2008-12-03
forum: General Help
---

### Post by firsttimeuser on 2008-12-03
on solaris , there is a prtdiag command which is pretty handy to show what kind of cpu and memory are plugged in the box, what is the equivalent command in ubuntu to show these?

---

### Post by albandy on 2008-12-03
CPU:
cat /proc/cpuinfo
MEM:
cat /proc/meminfo

---

### Post by tarps87 on 2008-12-03
you can also use lshw
use lshw -C for a specific class
I belive this should list the cpu
```
lshw -C CPU
```

---

### Post by firsttimeuser on 2008-12-03
ah, thanks, exactly what I need,

One more noob question, when I run uname -a, I only get the kernal version, how can I tell which version I am running?

---

### Post by taurus on 2008-12-03
Which version you mean either 32bit or 64bit?

i686 = 32bit
x86_64 = 64bit

---

### Post by firsttimeuser on 2008-12-03
sorry I was not very clear. I mean which OS version I am running, 

In solaris, you can fire a uname -a, and it gives you what version of Solaris you are running, like solaris.2.7

---

### Post by scorp123 on 2008-12-03
> **firsttimeuser said:**
> how can I tell which version I am running? ... could it be you mean the version of the Linux distribution you're running? ```
cat /etc/lsb-release 
```

In my case this returns: ```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10" 
```

---

### Post by taurus on 2008-12-03
```
lsb_release -a
```

---

### Post by firsttimeuser on 2008-12-03
many thanks!  :D

---

### Post by scorp123 on 2008-12-03
> **firsttimeuser said:**
> uname -a Well, as "Linux" per se is just the kernel, "uname -a" on Linux will usually just return the version of the kernel. As the kernel does not and cannot really know on which distro it is being used various distros use various other ways where they place that info.

Some distros have a "lsb-release" file in the /etc directory. Other distros such as OpenSUSE might have a "suse-version" file there, or Red Hat used to have a "redhat-release" file in /etc, and so on.

Other distros such as Debian don't have such files per default if I am not wrong. But here it would be easy to check e.g. /etc/apt/sources.list .... the presence of such a file would strongly suggest that you're on a Debian-based system. Taking a look at that file would then reveal which distro it might be, e.g. Ubuntu "Intrepid Ibex" has the word "intrepid" written all over that file, whereas the previous releases would have the words "hardy", "gutsy" or "feisty" in there. Debian releases might have "lenny", "etch", "sid", "unstable" and so on.

---

### Post by firsttimeuser on 2008-12-03
thanks dude, you guys are really helpful!

:D:D:D:popcorn:
> **scorp123 said:**
> Well, as "Linux" per se is just the kernel, "uname -a" on Linux will usually just return the version of the kernel. As the kernel does not and cannot really know on which distro it is being used various distros use various other ways where they place that info.

Some distros have a "lsb-release" file in the /etc directory. Other distros such as OpenSUSE might have a "suse-version" file there, or Red Hat used to have a "redhat-release" file in /etc, and so on.

Other distros such as Debian don't have such files per default if I am not wrong. But here it would be easy to check e.g. /etc/apt/sources.list .... the presence of such a file would strongly suggest that you're on a Debian-based system. Taking a look at that file would then reveal which distro it might be, e.g. Ubuntu "Intrepid Ibex" has the word "intrepid" written all over that file, whereas the previous releases would have the words "hardy", "gutsy" or "feisty" in there. Debian releases might have "lenny", "etch", "sid", "unstable" and so on.

---

### Post by scorp123 on 2008-12-03
> **firsttimeuser said:**
> thanks dude, you guys are really helpful!
:D:D:D:popcorn: Feel free to hit that "Thank you" button ;)

---

### Post by firsttimeuser on 2008-12-03
here you go, :)

> **scorp123 said:**
> Feel free to hit that "Thank you" button ;)

---

