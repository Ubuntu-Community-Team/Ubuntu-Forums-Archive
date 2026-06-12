---
title: "Problem installing Wolfenstein Enemy Territory 2.55"
date: 2008-08-29
forum: Gaming &amp; Leisure
---

### Post by scalywag66 on 2008-08-29
slight little problem here so I hope I posted in the correct forum

...

I've downloaded and installed 2.60 & 2.56 with no problems.   I downloaded 2.55 because that version of W:ET has the servers my clan mostly plays on and a host of other servers that I am friends with and just prefer over 2.56.  However, I can't get the party started just yet on 2.55 because of an error.  As the uncompressing began, it halted a bit afterwards and gave me this reading:

> /root/.setup7016: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

after a bit of searching around I come across and try the codes:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall libgtk1.2-common
```

and I still get the same error reading.  Did I download the wrong version of W:ET 2.55?

Being that I'm still new to Ubuntu, I am at a loss as to what went wrong and how to fix the slight issue.

---

### Post by scalywag66 on 2008-08-29
damnit!!! 

I just found the thread on here about the same issue.  Haven't read through it just yet.

Sorry for reposting an old problem

---

