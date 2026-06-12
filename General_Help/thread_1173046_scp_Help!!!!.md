---
title: "scp Help!!!!"
date: 2009-05-29
forum: General Help
---

### Post by Psycho.mario on 2009-05-29
I am trying to copy all the files off my router(i don't really know why, i just want to study how it works without damaging it) using scp:
```
scp -r admin@192.168.1.1:\* .
```admin is the default user for my router. When i run this command, it asks me for the password and everything. But i get the error:
```
scp: No such file or directory
```I can ssh into the router successfully and view the files and stuff, but why can't i copy them? Thanks for any help

---

### Post by LeSaint on 2009-05-29
try scp -r admin@192.168.1.1:/*
[FONT=monospace]
Regards
[/FONT]

---

### Post by LeSaint on 2009-05-29
Apologies:

 scp -r admin@192.168.1.1:/* .

Dont forget the period ... :)

---

### Post by ActiveFrost on 2009-05-29
> /home/user/ - CORRECT
\home\user\ - WRONG

So, why you want to use \ instead of / ?

> IP:/* - CORRECT
IP:\* - WRONG

---

### Post by albinootje on 2009-05-29
> **LeSaint said:**
> 
scp -r admin@192.168.1.1:/* .

Dont forget the period ... :)

Indeed :)

But, for the OP, and in general, if you want to have all files, then don't use the * sign, but use this :
```

scp -r admin@192.168.1.1:/ .

```
The * sign will not copy the "hidden" files which start with a dot, in that current directory.

In this case, for copying / it doesn't matter, since there are usually no dot files in the root of /, but in general it is better to know how to use the * sign efficiently.

And, with scp you might want to skip copying /proc and /dev and /sys. If you really want /dev then tar it first, and copy the resulting tar file.

---

### Post by Psycho.mario on 2009-05-29
ActiveFrost: I didn't put that in the terminal, it was a typo. :oops:

Thanks for all the help, but nothing worked. I can't tar it then copy it because df tells me there is 0% free space. Whatever i try, i still get 
```
scp: No such file or directory
```

---

### Post by albinootje on 2009-05-29
> **Psycho.mario said:**
> ActiveFrost: I didn't put that in the terminal, it was a typo. :oops:

Thanks for all the help, but nothing worked. I can't tar it then copy it because df tells me there is 0% free space. Whatever i try, i still get 
```
scp: No such file or directory
```

Is there no disk space on the remote machine, or on your machine ?

Does this also fail :
```

scp -r admin@192.168.1.1: .

```

---

### Post by Psycho.mario on 2009-05-29
No, that fails too. It's the router which is out of space. I've got about 250GB free space.

---

