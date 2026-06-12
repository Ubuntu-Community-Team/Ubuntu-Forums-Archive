---
title: "scp and ssh errors"
date: 2009-03-31
forum: General Help
---

### Post by Adversus on 2009-03-31
Hi,

since somewhere last week I started getting errors when trying to use scp or ssh:

```
sgvalcke@ronny:~$ scp -vvv test sgvalcke@genix:
Executing: program /usr/bin/ssh host genix, user sgvalcke, command scp -v -t .
command-line: line 0: Bad configuration option: PermitLocalCommand
lost connection

```

googling this one points in the direction of out of sync ssh and scp installations. Although something must have happened/changed I did not deliberately change anything to scp/ssh in the even not so near past.

rsync does work however:
```
sgvalcke@ronny:~$ rsync -e ssh -avzpt --rsync-path=/opt/csw/bin/rsync test sgvalcke@genix:
Password: 
building file list ... done
test

sent 120 bytes  received 42 bytes  46.29 bytes/sec
total size is 0  speedup is 0.00

```

ssh has also stopped functioning:
```
sgvalcke@ronny:~$ ssh uit1@ithildin
uit1@ithildin's password: 
Segmentation fault
sgvalcke@ronny:~$ ssh sgvalcke@rana
sgvalcke@rana's password: 
Segmentation fault

```

when I try to log in to a Solaris machine there is however no problem:

```
sgvalcke@ronny:~$ ssh sgvalcke@genix
Password: 
<text snipped>
sgvalcke@genix:~$

```

Ubuntu 8.0.4,
```
sgvalcke@ronny:~$ uname -a
Linux ronny 2.6.24-23-generic #1 SMP Mon Jan 26 01:04:16 UTC 2009 x86_64 GNU/Linux

```

I've checked with 2 colleagues, one has the same problems, the other does not. Relevant or not: we all three recently installed OO 3.0, using these instructions: [http://webupd8.blogspot.com/2009/03/install-openoffice-ubuntu-intrepid.html](http://webupd8.blogspot.com/2009/03/install-openoffice-ubuntu-intrepid.html). The colleague with the same issues is also on a 64 bit system.

I really have to get my ssh working again asap... :(

thanks in advance,

Sander

---

### Post by Adversus on 2009-04-01
Problem solved, using some of the steps listed here: [https://lists.ubuntu.com/archives/ubuntu-server-bugs/2008-October/006561.html]("https://lists.ubuntu.com/archives/ubuntu-server-bugs/2008-October/006561.html"): the chattr parts, along with moving the ssh and sshd executables away, doing apt-get clean and then reinstalling ssh-client (not removing and then installing because it kept insisting to then remove ubuntu-desktop as well) and ssh-server through the package manager.

---

