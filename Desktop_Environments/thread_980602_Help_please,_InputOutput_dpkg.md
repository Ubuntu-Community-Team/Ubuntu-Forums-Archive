---
title: "Help please, Input/Output dpkg"
date: 2008-11-13
forum: Desktop Environments
---

### Post by PureKaoz on 2008-11-13
No matter what i do, if i try to chat a program (xchat or pidgin) etc. or even download updates i get this error....
dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/available': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)


could really use some help im new to ubuntu just installed today, like it so far.

---

### Post by AbtZ on 2008-12-11
Hi,

I got the same error message as you when trying to install or remove programs with apt-get, after enabling a third-party repository.

I found the solution in [this thread]("http://www.linuxquestions.org/questions/linux-software-2/inputoutput-error-dpkg-sub-process-usrbindpkg-returned-and-error-code-2-443352/")

Simply run the command
```
sudo dpkg --clear-avail
```
(NOT --clea**n**-avail as the author of the thread says). This should solve your problem. :)

---

### Post by mipesom on 2011-12-15
> **AbtZ said:**
> Hi,

I got the same error message as you when trying to install or remove programs with apt-get, after enabling a third-party repository.

I found the solution in [this thread]("http://www.linuxquestions.org/questions/linux-software-2/inputoutput-error-dpkg-sub-process-usrbindpkg-returned-and-error-code-2-443352/")

Simply run the command
```
sudo dpkg --clear-avail
```
(NOT --clea**n**-avail as the author of the thread says). This should solve your problem. :)
You saved my life [OK, at least my Ubuntu install ;) ]! Thanks!

---

