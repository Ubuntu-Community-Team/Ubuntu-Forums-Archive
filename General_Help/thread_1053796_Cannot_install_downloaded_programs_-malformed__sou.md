---
title: "Cannot install downloaded programs -malformed  source list"
date: 2009-01-29
forum: General Help
---

### Post by seantm on 2009-01-29
Hi all, I realize  there are some variations of similar problems in the forums here but i've tried the soluitons offered without luck.
am running an I. Ibex install and am unable to install anything uisng synaptic or cmd line. when I try I get:

[I]E: Malformed line 55 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
[/I]

can anyone please advise how to resolve this?  thanks in advance! ;)

---

### Post by scragar on 2009-01-29
```
cp /etc/apt/sources.list ~/Desktop/sources.list
```
Please upload a copy of your sources list.

---

### Post by hyper_ch on 2009-01-29
you could use the tool in my sig to create a new sources.list

---

### Post by jrusso2 on 2009-01-29
Why change the whole sources.list when only one line is bad?  Just fix it.  But you might have some extra repos that are nice on yours?

---

### Post by seantm on 2009-01-29
Thanks --forgive the noobishness--but how to edit or fix the one line?

---

### Post by jrusso2 on 2009-01-29
It would help to see your list if you can post it.  The instructions were given earlier in the thread.

The problem seems to be in line 55.  Probably added a repo and didn't use the right format.  It should look like the other lines are far as where things are.

Always back up your sources.list either put a copy in another location like your /home or rename a copy and leave it in the same directory . Like sources.listbak Which is what I do so that I can just go in and rename it if I want to use the old one.

---

### Post by Boomhauer on 2009-01-29
you can easily get your list if you go to a terminal, applications>accessories>terminal, and enter in ```
cat /etc/apt/sources.list
``` then copy and paste everything that is returned here.

---

### Post by seantm on 2009-01-29
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe
deb-src [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe
deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe
deb-src [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
ahill@ahill-laptop:~$

---

### Post by scragar on 2009-01-29
Grr, this is why I wanted the file uploaded, instead of half a list.
```
cat /etc/apt/sources.list | head -n 60 | tail -n 10
```

And please use the forums [noparse]```
...
```[/noparse] tags.

---

### Post by seantm on 2009-01-29
**Ok --thanks for your patience---**

> **scragar said:**
> Grr, this is why I wanted the file uploaded, instead of half a list.
```
cat /etc/apt/sources.list | head -n 60 | tail -n 10
```And please use the forums [noparse]```
...
```[/noparse] tags.
ahill@ahill-laptop:~$ cat /etc/apt/sources.list | head -n 60 | tail -n 10
deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe
deb-src [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe
deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe
deb-src [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
ahill@ahill-laptop:~$ cat /etc/apt/sources.list | head -n 60 | tail -n 10
deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe
deb-src [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe
deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe
deb-src [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
ahill@ahill-laptop:~$

---

### Post by scragar on 2009-01-29
I'm assuming:
```
deb http://us.archive.ubuntu.com/ubuntu intrepid
```
is line 55, right?

No matter what that line was supposed to read I don't think it works at all.
```
gksu gedit /etc/apt/sources.list
```
Remove the line.

---

### Post by zvacet on 2009-01-29
I may be wrong but 

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) intrepid

looks wrong because it doesn't point to anything.

---

### Post by seantm on 2009-01-29
That was it! I edited it out and it's all working now... thnaks everyone for your time and patience...

---

