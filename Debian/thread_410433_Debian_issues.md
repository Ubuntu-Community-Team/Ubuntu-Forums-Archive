---
title: "Debian issues?"
date: 2007-04-15
forum: Debian
---

### Post by finferflu on 2007-04-15
Hi,
I have just installed Debian Etch, and as a new user, I'm having issues! I was wondering if this forum was appropriate to ask questions. My main problem is that I can't find any official Debian forum, so, since I have to look for unofficial ones, I prefer asking my favourite one. 

Thanks!

---

### Post by apunc1 on 2007-04-15
hello,
i cannot help you with etch, however, have you tried [http://debcentral.org/](http://debcentral.org/) and [http://forums.debian.net/index.php?sid=5eaf7d4533d2dacaa2b619e1f71bad0c](http://forums.debian.net/index.php?sid=5eaf7d4533d2dacaa2b619e1f71bad0c)

---

### Post by teaker1s on 2007-04-15
[http://forums.debian.net/index.php](http://forums.debian.net/index.php)

---

### Post by finferflu on 2007-04-15
Ok, so I guess I cannot ask questions here... Thanks for the links anyway :)

---

### Post by SishGupta on 2007-04-15
> **finferflu said:**
> Ok, so I guess I cannot ask questions here... Thanks for the links anyway :)

I don't see why you can't ask questions here. The problem is that most people here likely don't use debian etch or at least enough to help out. You will have much better luck getting answers to problems at forums.debian.net

---

### Post by finferflu on 2007-04-16
Well, it depends on the problem I think. I'll just post an example of my most recent problem. I'm trying to install wacom-kernel-source and I get:

```
# apt-get install wacom-kernel-source
Reading package lists... Done
Building dependency tree... Done
wacom-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up wacom-kernel-source (0.7.4.1-5) ...
/var/lib/dpkg/info/wacom-kernel-source.postinst: line 49: [: too many arguments
Warning: kernel headers don't match running Linux version.
Building wacom modules for Linux _CODE 13262 (this may take a few minutes)...dpkg: error processing wacom-kernel-source (--configure):
subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
wacom-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I don't think this is only-Debian related. I also prefer asking here because this is the most friendly community I know. I would like to start asking here, and if I don't get answerrs, going somewhere else, or maybe askng the more generic questions here.

---

### Post by mips on 2007-04-16
Stupid question but does your kernel version match the linux-headers version ?

---

### Post by ThinkBuntu on 2007-04-16
forums.debian.net is an excellent help forum. The members take pride in their advice and will help you through your problems.

---

### Post by finferflu on 2007-04-16
> **mips said:**
> Stupid question but does your kernel version match the linux-headers version ?
what do you think?

```
# uname -r
2.6.18-4-686
```

```
# apt-get install linux-headers-`(uname -r)` 
Reading package lists... Done 
Building dependency tree... Done 
linux-headers-2.6.18-4-686 is already the newest version.
```

---

### Post by mips on 2007-04-16
> **finferflu said:**
> what do you think?


I think they match ;)

---

### Post by rai4shu2 on 2007-04-16
Maybe it's not that simple. Granted, this is 64-bit, but here's mine:

```
$ apt-cache policy linux-headers-`(uname -r)`
linux-headers-2.6.18-4-amd64:
  Installed: 2.6.18.dfsg.1-12
  Candidate: 2.6.18.dfsg.1-12
  Version table:
 *** 2.6.18.dfsg.1-12 0
        500 cdrom://[Debian GNU/Linux 4.0 r0 _Etch_ - Official amd64 DVD Binary-1 20070407-12:15] etch/main Packages
        100 /var/lib/dpkg/status
```

---

### Post by finferflu on 2007-04-16
> **rai4shu2 said:**
> Maybe it's not that simple. Granted, this is 64-bit, but here's mine:

```
$ apt-cache policy linux-headers-`(uname -r)`
linux-headers-2.6.18-4-amd64:
  Installed: 2.6.18.dfsg.1-12
  Candidate: 2.6.18.dfsg.1-12
  Version table:
 *** 2.6.18.dfsg.1-12 0
        500 cdrom://[Debian GNU/Linux 4.0 r0 _Etch_ - Official amd64 DVD Binary-1 20070407-12:15] etch/main Packages
        100 /var/lib/dpkg/status
```
Sorry, I don't get your point... here's mine anyways...
```

# apt-cache policy linux-headers-`(uname -r)` 
linux-headers-2.6.18-4-686:
  Installed: 2.6.18.dfsg.1-12
  Candidate: 2.6.18.dfsg.1-12
  Version table:
 *** 2.6.18.dfsg.1-12 0
        500 http://http.us.debian.org stable/main Packages
        500 http://ftp.uk.debian.org stable/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by finferflu on 2007-04-17
Well, it seems like I have stubled in a bug, what a luck!

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=418008](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=418008)

---

### Post by mips on 2007-04-17
> **finferflu said:**
> Well, it seems like I have stubled in a bug, what a luck!

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=418008](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=418008)

It's one of those I would put down to bad luck...

---

