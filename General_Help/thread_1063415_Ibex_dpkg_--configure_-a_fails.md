---
title: "Ibex dpkg --configure -a fails"
date: 2009-02-07
forum: General Help
---

### Post by flyingsliverfin on 2009-02-07
here is the error report

dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

could you tell me how to use logs? I have heard of them but don't know how to use them. I could post it here if I need to. 

thx

---

### Post by spiderbatdad on 2009-02-07
maybe this bug [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/279709](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/279709)
reinstall cups.
sudo dpkg -r --force-depends cups

---

### Post by howefield on 2009-02-07
Some success in this thread although it is pretty old.

[http://ubuntuforums.org/showthread.php?t=231752](http://ubuntuforums.org/showthread.php?t=231752)

---

### Post by flyingsliverfin on 2009-02-13
thank you.

I actually used the guide at [http://www.go2linux.org/problem-upgrading-debian](http://www.go2linux.org/problem-upgrading-debian).

for some reason it worked so now im happy

thx

---

