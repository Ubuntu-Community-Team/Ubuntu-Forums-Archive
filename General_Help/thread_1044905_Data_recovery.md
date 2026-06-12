---
title: "Data recovery"
date: 2009-01-19
forum: General Help
---

### Post by rene.olivo on 2009-01-19
Hello,

Im very green! so green I spark, so I thank you all in advance.

long story short: I used windows and it went "kaboom" and I inserted my live CD to save the files. I couldn't mount the disks (my fault) so I got a bit desperate (I know, I know...) and formated the partition where I had windows xp and most of my files to install ubuntu and use it as my main OS. Now I have 3 HD, a 23 GB one that I left as NTFS to save something very important I had there (I managed to save these files), 40 GB HD for UBUNTU and a formated 190 GB HD in NTFS, the 40GB and this one used to be my windows partition.

Now, the question is, is there any way to recover deleted/formated files in ubuntu? I have searched trough the web but I have only come across on how to mount windows disks :( mine is already fried (formated).

thanks for the help

---

### Post by iaculallad on 2009-01-19
You've mentioned searching the web for possible solutions, had you came across the [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") utility? 
I used it once when I desperately needed back our client's data on one of my server disk drive.

---

### Post by rene.olivo on 2009-01-19
Actually I have, Im not an expert and don't know if it linux installer can work on ubuntu, because there's none for ubuntu only linux ?!?!?

---

### Post by eatberrys on 2009-01-19
[http://ubuntuforums.org/showthread.php?t=1043909](http://ubuntuforums.org/showthread.php?t=1043909)

See if that helps any

---

### Post by iaculallad on 2009-01-19
> **rene.olivo said:**
> Actually I have, Im not an expert and don't know if it linux installer can work on ubuntu, because there's none for ubuntu only linux ?!?!?

You're absolutely wrong, Testdisk can be installed in Ubuntu (Linux in General). Had you tried doing the command below on your terminal?

```
sudo apt-get install testdisk
```

The command above will install the testdisk utility to your system.

EDIT: Online guide on how to use the testdisk utility can be found on this [link]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by linux_tech on 2009-01-19
Give testdisk and photorec a shot:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Detailed instructions for photorec
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

A good reference for data recovery::
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

You may also want to check out ntfsundelete

---

