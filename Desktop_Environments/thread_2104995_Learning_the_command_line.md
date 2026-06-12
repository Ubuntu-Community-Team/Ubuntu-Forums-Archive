---
title: "Learning the command line"
date: 2013-01-14
forum: Desktop Environments
---

### Post by DMGrier on 2013-01-14
So I am slowly learning the command line, I did start on Ubuntu 8.04 but I only forced myself to learn simple things like installing and removing applications.

I picked up a copy of Ubuntu Unleashed and I am going going through the command line part and I know these thing seem simple but I cannot figure out how to do a pipeline? I have a English USA keyboard layout and was hoping I could get some help. Thanks guys.

---

### Post by eenofonn on 2013-01-14
it's usually "shift + \" right above the enter key which gives you a | which is displayed a bit different on the keyboard.

a good example of pipe "|" would be 

```

ifconfig | less

```

or something like 

```

cat /proc/meminfo | less

```

These are just simple examples but give you a good idea of what a pipeline does, piping the output of one command/program into another

---

### Post by DMGrier on 2013-01-14
Just gave it a shot, and it worked. Thanks man for the quick reply.

---

### Post by eenofonn on 2013-01-14
> **DMGrier said:**
> Just gave it a shot, and it worked. Thanks man for the quick reply.

Glad to hear it another fun little tool is ">"

which sends the output to a file:

```

cat /proc/cpuinfo > ~/cpuinfo.txt

```

that takes the output of "cat /proc/cpuinfo" and puts it into a new file in your home directory called cpuinfo.txt

---

### Post by DMGrier on 2013-01-14
awesome, I am working on it. I am trying to learn what I can since I am starting college classes this spring for a degree for network security. Just toured the campus and got very excited when I saw the security core classes is taught on Ubuntu machines.

---

### Post by eenofonn on 2013-01-14
> **DMGrier said:**
> awesome, I am working on it. I am trying to learn what I can since I am starting college classes this spring for a degree for network security. Just toured the campus and got very excited when I saw the security core classes is taught on Ubuntu machines.

Nice

---

### Post by tgalati4 on 2013-01-14
Add to an existing file:

```
ls > mydirectorylisting.txt; ls -la >> mydirectorylisting.txt
cat mydirectorylisting.txt
```

Common pipe commands that I use:

```
dmesg | more
dmesg | tail -50
ps -ef | more
dmesg | grep BogoMIPS
ps -ef | grep syslog

```

---

### Post by NikiNfOuR on 2013-01-15
I am new at command line myself!! if you haven't got this get this command line learning book that covers everything about terminal :)

[http://linuxcommand.org/tlcl.php]("http://linuxcommand.org/tlcl.php")

---

