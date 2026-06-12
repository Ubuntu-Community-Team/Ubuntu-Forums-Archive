---
title: "data loss and testdisk"
date: 2008-12-18
forum: General Help
---

### Post by mish78 on 2008-12-18
Hi,
I was reinstalling XP because of a bug and thought I`d better unplug my free agent external hdd in case the hp re installation software formatted it. Unfortunately i did this in a moment of madness and unplugged it when it was on. Now xp will see it and tell me its not formatted and ubuntu wont see it at all via nautalus but will via test disk. My question is how to use testdisk to recover ( if poss ) all my files. From what i gather its mainly used for recovering filesystems. is this correct and is there other way you can suggest to recover my files.... I did try test king and the deepscan comes up with errors but take 24 hrs to get to 29%.

pls, any help or advise  appreciated

---

### Post by Polygon on 2008-12-18
what filesystem was on the external drive?

and also, i just checked the man page for testdisk, and it looks like the right program for the job

i just just do

sudo testdisk

enter your password 

select the log level (doesnt matter)

and then select the hard drive that you want testdisk to run on, and give it a go.

---

