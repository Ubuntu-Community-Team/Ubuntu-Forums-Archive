---
title: "can't remove 0 byte files"
date: 2009-03-25
forum: General Help
---

### Post by marcon00 on 2009-03-25
I got two exactly same files, in very the same folder that are not visible only in terminal. They somehow do now allow my system to boot,it asks for manual scan and it stops on this file.

B# ls -s
ls: cannot access Radoslaw Skowron.doc: No such file or directory
ls: cannot access Radoslaw Skowron.doc: No such file or directory
total 0
0 Radoslaw Skowron.doc  0 Radoslaw Skowron.doc
root@ubuntu:# 

# rm Radoslaw\ Skowron.doc 
rm: cannot remove `Radoslaw Skowron.doc': No such file or director

cant get rid of these files .. its soo annoying.. .. anyone ?

---

### Post by damis648 on 2009-03-25
Hm... try removing the folder maybe?
```
rm -r foldername
```

---

### Post by marcon00 on 2009-03-25
> **damis648 said:**
> Hm... try removing the folder maybe?
```
rm -r foldername
```

tried that too..nothing :\ even mv ...

---

### Post by evilaim on 2009-03-25
Yes, that would help.  Generally, you need to add flags for deleting files.  For directories, I usually just use: rm -rf foldername

It has stuck with me since I'm an old school user.  If you want to remove a file in a folder, just cd into the folder and remove it that way.

Good luck and I hope this helps.

-Evil

---

### Post by marcon00 on 2009-03-25
> **evilaim said:**
> Yes, that would help.  Generally, you need to add flags for deleting files.  For directories, I usually just use: rm -rf foldername

It has stuck with me since I'm an old school user.  If you want to remove a file in a folder, just cd into the folder and remove it that way.

Good luck and I hope this helps.

-Evil

and this is what my laptop got to say on that :
# rm -rf USB/
rm: cannot remove directory `USB': Directory not empty

let me see if everything is fine now.

brb


its a folder on my desktop called USB ..

but ... i tried -rf inside that folder , i specified that file.. and its gone now.

---

### Post by evilaim on 2009-03-25
Good to hear, but you don't need a / at the end of it...
you could always do: rm -rf USB/*
but generally rm -rf USB
would work great.

---

### Post by marcon00 on 2009-04-09
> **evilaim said:**
> Good to hear, but you don't need a / at the end of it...
you could always do: rm -rf USB/*
but generally rm -rf USB
would work great.

thanks.. but guess what, somehow they came back .. im so lost why this happens. I'm gonna hard format my Drives, see if there are any problems with the disk ( i need to format anyways )

sss2.docx
?? ?????.EXT                              ???? ??????? ???? ??????.txt
?? ?????.EXT                              ???? ??????? ???? ??????.txt
?? ?????.EXT                              ???? ??????? ???? ??????.txt
?? ?????.EXT                              ???? ??????? ???? ??????.txt
?? ?????.EXT                              ???? ??????? ???? ??????.txt
?? ?????.EXT                              ???? ??????? ???? ??????.txt


cant delete them .. again .. even with  -rf

---

### Post by eragon100 on 2009-04-09
Did you make those files or did they really "just appear"? It sounds like you got a virus. Which would be pretty bad, because it would be the first destructive, hard-to-remove virus for linux, ever :(

---

### Post by soltanis on 2009-04-09
It's probably not a virus. It sounds to me more like a file system problem, run as root

```

fsck -C / -r

```

To check your file system integrity. (assuming your suspect files are in your / partition)

EDIT.
And unmount the partition first.

---

### Post by dcstar on 2009-04-09
> **soltanis said:**
> It's probably not a virus. It sounds to me more like a file system problem, run as root

```

fsck -C / -r

```

To check your file system integrity. (assuming your suspect files are in your / partition)

EDIT.
**And unmount the partition first**.

Which means this **cannot** be done on a booted system.

Boot off a Live CD and do a check on the partition using the Partition Manager.

---

### Post by marcon00 on 2009-04-10
I'm soo not goin as to be first* having some kind of vii for linux, thank God it this is not the case. I believe i got some naughty vii from vista,was editing some files in MS and it all went weird. I couldnt even access properly my home/user folder , i had no permissions supposedly. 

I hardformated my drives, and checked for any bad sectors, all is clean.
now everything is working smooth, im gonna give it some more time see if they appear again, and check for possible reason if the problem is reproducible. and if its a windows vii, i will tell you what kind of vii it is, that is if i find the name , kaspersky did not detect anything.

thank you all for your support, will be back with updates.

---

