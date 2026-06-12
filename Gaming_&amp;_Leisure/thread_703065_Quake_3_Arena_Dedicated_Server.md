---
title: "Quake 3 Arena Dedicated Server"
date: 2008-02-20
forum: Gaming &amp; Leisure
---

### Post by sYn pHrEAk on 2008-02-20
Dapper Server 64bit.

This is probably just some general problem.  I've got Quake 3 installed (had to use linux32) and the pak file copied over.

But when I try to run any of the binary executables

```

q3user@machee:/usr/local/games/quake3$ q3ded
-bash: q3ded: command not found
q3user@machee:/usr/local/games/quake3$ ./q3ded
-bash: ./q3ded: No such file or directory
q3user@machee:/usr/local/games/quake3$ /usr/local/games/quake3/q3ded
-bash: /usr/local/games/quake3/q3ded: No such file or directory

q3user@machee:/usr/local/games/quake3$ ls -al q3ded
-rwxrwxrwx 1 q3user q3user 749504 Feb 21 04:41 q3ded

```

There is such file or directory. It's right there! :mad::mad::mad:

I have seen this before with other stuff but don't remember if or how I fixed it.  What is going on?  Is it because I'm running 64 bit server?

---

### Post by sYn pHrEAk on 2008-02-21
apt-get install ia32-lib*

it was a 64bit issue.  that command installs some 32bit compatibility libraries. did the trick. thanks to redf1sh in #ubuntu for this one

=D>:mrgreen::-D

---

