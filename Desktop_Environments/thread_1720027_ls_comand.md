---
title: "ls comand"
date: 2011-04-02
forum: Desktop Environments
---

### Post by 71GA on 2011-04-02
Hello!

I know i can use ls comand to list files in folders other than current working directory like this:
```
ls /home/user
```
But where do i add aditional option to only list files that end with x?

---

### Post by matt_symes on 2011-04-02
Hi

> **71GA said:**
> Hello!

I know i can use ls comand to list files in folders other than current working directory like this:
```
ls /home/user
```
But where do i add aditional option to only list files that end with x?

Something along the lines of

```
ls /home/user/*x
```

Is that what you mean ?

Check out wild cards.

Kind regards

---

### Post by ankspo71 on 2011-04-02
Hi,
Try these commands:
```
ls /home/user | grep *x
```
But it doesn't work for me with hidden files (using ls -a), not sure why either.
Correction: I got it to work with hidden files... it was a typo error on my part.
```
ls -a /home/user | grep *x
```

Or you could use the find command instead
```
find /home/user -iname '*x'
```

Hope this helps.

---

### Post by 71GA on 2011-04-02
This isnt working for me... i dont get only files that end with x but other files as well.

---

### Post by wojox on 2011-04-02
You would have to use the "find" command.

---

### Post by matt_symes on 2011-04-02
Hi

Maybe i misunderstood you. I though you meant something along the lines of

```
matthew@matthew-laptop:~$ ls ~/test
aab  aabb  acc  ade
matthew@matthew-laptop:~$ ls ~/test/*b
/home/matthew/test/aab  /home/matthew/test/aabb
matthew@matthew-laptop:~$ ls ~/test/*e
/home/matthew/test/ade
matthew@matthew-laptop:~$ ls ~/test/*ab*
/home/matthew/test/aab  /home/matthew/test/aabb
matthew@matthew-laptop:~$ ls ~/test/ad?
/home/matthew/test/ade
matthew@matthew-laptop:~$ 
```

That is doing what i would expect.

Kind regards

---

### Post by 71GA on 2011-04-02
> **matt_symes said:**
> Hi

Maybe i misunderstood you. I though you meant something along the lines of

```
matthew@matthew-laptop:~$ ls ~/test
aab  aabb  acc  ade
matthew@matthew-laptop:~$ ls ~/test/*b
/home/matthew/test/aab  /home/matthew/test/aabb
matthew@matthew-laptop:~$ ls ~/test/*e
/home/matthew/test/ade
matthew@matthew-laptop:~$ ls ~/test/*ab*
/home/matthew/test/aab  /home/matthew/test/aabb
matthew@matthew-laptop:~$ ls ~/test/ad?
/home/matthew/test/ade
matthew@matthew-laptop:~$ 
```

That is doing what i would expect.

Kind regards

Weird i cant seem to make it work. Thank you anyway :)

---

### Post by 71GA on 2011-04-02
Oh wait wait it is working thank you.:guitar:

---

### Post by Copper Bezel on 2011-04-02
ankspo71, ls ignores hidden files unless you tell it not to, with -a. Now, that said, if I run

```
ls -a | grep -i x
```

I get every file that includes an x or an X, naturally. But that means that adding an asterisk, like *x, doesn't mean anything, because anything you drop into grep is assumed to be a part of a string - grep x actually means grep *x* already.

This one seems to work for me, though. 

```
find /home/user -iname '*x'
```

71GA, if you want it to not search recursively and instead list from just the present directory, you need to limit the depth:

```
find /home/user -iname '*x' -maxdepth 1
```

Edit: Apparently I took too long to figure that out and type my response. = )

---

### Post by 71GA on 2011-04-02
Thank you this is great info.

---

### Post by ankspo71 on 2011-04-02
> **Copper Bezel said:**
> ankspo71, ls ignores hidden files unless you tell it not to, with -a. Now, that said, if I run

```
ls -a | grep -i x
```

I get every file that includes an x or an X, naturally. But that means that adding an asterisk, like *x, doesn't mean anything, because anything you drop into grep is assumed to be a part of a string - grep x actually means grep *x* already.


Hi, and thanks.
The ls & grep commands I posted above no longer work for me 30 minutes after posting them (I tested them several times as I posted them too), and neither do any of the examples given by matt_symes. I think maybe I didn't make a typo after all... instead I must be encountering some odd bugs because I'm using Natty Beta. The <find /home/user -iname '*x'> command still works for me though.

---

### Post by matt_symes on 2011-04-02
Hi

> **ankspo71 said:**
> Hi, and thanks.
The ls & grep commands I posted above no longer work for me 30 minutes after posting them (I tested them several times as I posted them too), and neither do any of the examples given by matt_symes. I think maybe I didn't make a typo after all... instead I must be encountering some odd bugs because I'm using Natty Beta. The <find /home/user -iname '*x'> command still works for me though.

That's really odd. Can you post sample output ? 

That's the good thing about Linux though; always more than one way to do things ;) 

Kind regards

---

### Post by ankspo71 on 2011-04-02
> **matt_symes said:**
> Hi
That's really odd. Can you post sample output ? 
That's the good thing about Linux though; always more than one way to do things ;) 
Kind regards

Sure can.:D

```
james@Kubuntu-Natty:~$ ls | grep x
adcx.txt
test.123x
tux
txa
xero
xyz
james@Kubuntu-Natty:~$ ls /home/james/x?
ls: cannot access /home/james/x?: No such file or directory
james@Kubuntu-Natty:~$ ls /home/james/ux?
ls: cannot access /home/james/ux?: No such file or directory
james@Kubuntu-Natty:~$ ls /home/james/?ux
james@Kubuntu-Natty:~$ ls /home/james/*ux
james@Kubuntu-Natty:~$ ls /home/james/*x
/home/james/test.123x
/home/james/tux:
james@Kubuntu-Natty:~$ ls /home/james/?x
ls: cannot access /home/james/?x: No such file or directory
james@Kubuntu-Natty:~$ ls ~/?ux
james@Kubuntu-Natty:~$ ls ~/?x
ls: cannot access /home/james/?x: No such file or directory
james@Kubuntu-Natty:~$ ls ~/*ux
james@Kubuntu-Natty:~$ ls ~/*ux*
james@Kubuntu-Natty:~$ ls ~/ux?
ls: cannot access /home/james/ux?: No such file or directory
james@Kubuntu-Natty:~$ ls ~/*x
/home/james/test.123x
/home/james/tux:

```

---

### Post by matt_symes on 2011-04-02
Hi

```
matthew@matthew-laptop:~$ ls /bin
bash     bzfgrep       chown                 dbus-uuidgen   ed          gzexe     lesskey   mktemp      nc.openbsd        openvt    rm          sleep      touch            ypdomainname  zmore
bsd-csh  bzgrep        chvt                  dd             egrep       gzip      lesspipe  more        netcat            pidof     rmdir       static-sh  true             zcat          znew
bunzip2  bzip2         cp                    df             false       hostname  ln        mount       netstat           ping      rnano       stty       ulockmgr_server  zcmp
busybox  bzip2recover  cpio                  dir            fgconsole   ip        loadkeys  mountpoint  nisdomainname     ping6     run-parts   su         umount           zdiff
bzcat    bzless        csh                   dmesg          fgrep       kbd_mode  login     mt          ntfs-3g           plymouth  sed         sync       uname            zegrep
bzcmp    bzmore        dash                  dnsdomainname  fuser       kill      ls        mt-gnu      ntfs-3g.probe     ps        setfont     tailf      uncompress       zfgrep
bzdiff   cat           date                  domainname     fusermount  less      lsmod     mv          ntfs-3g.secaudit  pwd       setupcon    tar        unicode_start    zforce
bzegrep  chgrp         dbus-cleanup-sockets  dumpkeys       grep        lessecho  mkdir     nano        ntfs-3g.usermap   rbash     sh          tcsh       vdir             zgrep
bzexe    chmod         dbus-daemon           echo           gunzip      lessfile  mknod     nc          open              readlink  sh.distrib  tempfile   which            zless
matthew@matthew-laptop:~$ ls /bin/*r
/bin/bzip2recover  /bin/dir  /bin/fuser  /bin/mkdir  /bin/rmdir  /bin/tar  /bin/ulockmgr_server  /bin/vdir
matthew@matthew-laptop:~$ 
matthew@matthew-laptop:~$ ls /bin/g*p
/bin/grep  /bin/gunzip  /bin/gzip
matthew@matthew-laptop:~$
matthew@matthew-laptop:~$ ls /bin/nt*g?*
/bin/ntfs-3g.probe  /bin/ntfs-3g.secaudit  /bin/ntfs-3g.usermap
matthew@matthew-laptop:~$ ls /bin/nt*g?p*
/bin/ntfs-3g.probe
matthew@matthew-laptop:~$
matthew@matthew-laptop:~$ ls /bin/z??r*p
/bin/zegrep  /bin/zfgrep
matthew@matthew-laptop:~$ ls /bin/?a?
/bin/cat  /bin/tar
matthew@matthew-laptop:~$   
```

As you say, maybe a bug in natty ?

Kind regards.

---

### Post by ankspo71 on 2011-04-02
Hi Again.
Okay, your command examples are working as expected again. I rebooted and everything is working better than it was before. I think I have found my mistake for my ls & grep command too, and that it requires 2 or more characters when using wildcards with grep.
```

james@Kubuntu-Natty:~$ ls | grep x
adcx.txt
test.123x
tux
txa
xero
xyz
james@Kubuntu-Natty:~$ ls | grep *x
<no output>
james@Kubuntu-Natty:~$ ls | grep ux
tux
james@Kubuntu-Natty:~$ ls | grep *ux
tux
james@Kubuntu-Natty:~$ ls | grep 23x
test.123x
james@Kubuntu-Natty:~$ ls | grep *23x
test.123x
james@Kubuntu-Natty:~$ ls /home/james | grep *ux
tux
```

But as someone said the * isn't necessary anyways.

---

