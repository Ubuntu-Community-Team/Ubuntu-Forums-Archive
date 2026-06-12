---
title: "Cannot execute binary file I own and have permissions on?"
date: 2009-06-01
forum: General Help
---

### Post by Julian David Pitt on 2009-06-01
I have read many posts on this issue and after trying all of them I still have the same issue. I  have a distributed computing app at /home/julian/Folding/fah6. I have run chmod a+x on it and confirmed I am the owner. I just keep getting cannot execute binary file. Are there any specific packages that I need as I seem to have libc6 and linux32 libraries   installed. Here is the output of some commands that may help in diagnosis:
```
ls -alt
drwxr-xr-x  4 julian julian  4096 2009-05-29 15:20 Folding
julian@julian260:~$ cd Folding
julian@julian260:~/Folding$ pwd
/home/julian/Folding
ls -l
-rwxrwxrwx 1 julian julian 912040 2009-01-29 02:53 fah6
-rwx------ 1 julian julian 139883 2009-05-27 12:03 FAH6.02-Linux.tgz
drwxr-xr-x 2 julian julian   4096 2009-05-29 09:42 Folding6
drwxr-xr-x 2 julian julian   4096 2009-05-29 09:43 Folding624
-rwx------ 1 julian julian  68492 2007-07-16 19:02 mpiexec
julian@julian260:~/Folding$ ./fah6
bash: ./fah6: cannot execute binary file

```

Please respond if you have any idea what is going wrong here and thanks for doing so.

---

### Post by mhgsys on 2009-06-01
This really isn't my specialty, so forgive me if I'm way of here,
But ehmz, 
Arn't you also suppose to unpack the FAH6.02-Linux.tgz?

---

### Post by Julian David Pitt on 2009-06-01
Hi and thanks for responding. I downloaded the tgz file and unpacked it into my Folding directory. The binary works fine on my laptop but refuses to play on three other machines, your ideas are appreciated.

---

### Post by lisati on 2009-06-01
> **Julian David Pitt said:**
> Hi and thanks for responding. I downloaded the tgz file and unpacked it into my Folding directory. The binary works fine on my laptop but refuses to play on three other machines, your ideas are appreciated.

I spotted the fah6 file in the directory listing but nothing obviously wrong comes to mind from the info provided.

---

