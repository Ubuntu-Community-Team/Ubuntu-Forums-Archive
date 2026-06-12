---
title: "Audacity - Glibc Error"
date: 2006-06-11
forum: Desktop Environments
---

### Post by Celerimo on 2006-06-11
Hi, i have a problem with the audio editing program Audacity. It only works for a fistful of operations and then crashes. 

This is the output on the console:
```
simon@celerimo:/mnt/h/backup$ audacity
*** glibc detected *** free(): invalid pointer: 0xb68fc008 ***
Aborted
```
I searched the net for the problem but it seems that I am the only one who has this problem.
There was only one who had problems with too less diskspace but I have definetly no problem with this.

So my question is this: Did anybody else also have this problem and possibily solved it?
If not I will post it as a bug.

Thanks for your support.

---

### Post by antivert on 2006-06-15
I'm having the same error with VMware Workstation 5.5.0 build-18463.

---

### Post by antivert on 2006-06-15
Could be related to SCIM if you're using it for foreign language input! I'm going to try uninstalling SCIM a bit later :\

EDIT: This thread: [http://ubuntuforums.org/showthread.php?t=145644&highlight=scim](http://ubuntuforums.org/showthread.php?t=145644&highlight=scim) has information on fixing vmware, it was definitely SCIM causing my problem. Perhaps a similar fix can help you? 

But, SCIM doesn't seem to hurt my audacity install, so you may have some other glibc problem!

---

