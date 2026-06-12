---
title: "wodim blocking, won't exit"
date: 2009-03-03
forum: Desktop Environments
---

### Post by twinspop on 2009-03-03
I right-clicked an ISO to burn to a disc

I inserted a blank when it asked

It then proceeded, but another popup asked what i wanted to do with the inserted blank disk (as if I had randomly inserted it without prompting). I clicked cancel.

Preparing to burn was up for over an hour before I tried to stop it

The /dev/scd0 device is blocking (I think) wreaking havoc on vmware

I cannot kill the 2 wodim processes running


Anyway to recover?

intrepid x86_64

user@host:~$ lsof | grep scd0
wodim      2163      user    3u      BLK               11,0                5296 /dev/scd0
wodim      2246      user    3u      BLK               11,0                5296 /dev/scd0

---

