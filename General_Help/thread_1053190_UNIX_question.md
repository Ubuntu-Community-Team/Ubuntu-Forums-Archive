---
title: "UNIX question"
date: 2009-01-28
forum: General Help
---

### Post by pgte3 on 2009-01-28
I am new to UNIX, and I am trying to run the following command:

/techsupp/OSP17864/usr/lib/ssh> ssh-keygen -t rsa
(rand child) Couldn't exec '/usr/lib/ssh/ssh-rand-helper': EDC5129I NO SUCH FILE OR DIRECTORY.
ssh-rand-helper child produced insufficient data

The program ssh-keygen is looking for ssh-rand-helper in a location that is does not exist (see below), how do I get the program ssh-keygen to find ssh-rand-helper in the location where it does exist (see below). A ln of some type?

/usr/lib/ssh> ls -a
. ..


/techsupp/OSP17864/usr/lib/ssh> ls -a
. .. IBM sftp-server ssh-askpass ssh-keysign ssh-rand-helper

---

### Post by cariboo on 2009-01-28
How did you install the openssh-server?

JIm

---

### Post by pgte3 on 2009-01-28
I installed and am trying to run OpenSSH on Unix System Services on a z/9 mainframe. It is a POSIX compliant Unix variant.

I installed OpenSSH (IBM ported tools) according to the install program directory provide by IBM.

I do not know why when running ssh-keygen it looks for ssh-rand-helper it the directory in my previous post.

I would like find a way for ssh-keygen to locate ssh-rand-helper from a different location.

---

### Post by pgte3 on 2009-01-29
Another response suggested:

su -
cd /usr/lib/ssh
ln -s where-ssh-rand-helper-is .

---

