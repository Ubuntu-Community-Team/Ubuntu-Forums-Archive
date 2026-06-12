---
title: "Please, do only show usplash"
date: 2008-12-05
forum: Desktop Environments
---

### Post by ChrisBookwood on 2008-12-05
Hellow,

I have for about 2 weeks time, tried to find a solution to get my Ubuntu 8.10 installation to only show usplash while booting.
I know it's default procedure, but when I did the installation in first place, I changed it, and now I want to change it back.

I have tried to change different thing, I would suspect to do the job, but with no luck.

/boot/grub/menu.lst shows the following:
```
# kopt=root=UUID=09c88f95-3096-4575-a7c1-d144e820c115 ro quiet splash
```Now, I would believe it should work now, but for some reason it doesn't.

And by the way - it's not because I have forgot to do a update-grub;)

---

### Post by mtbsoft on 2008-12-05
Are you be getting the text appearing when the "Reading files needed to boot...     [ OK ]" message appears?  I've been experiencing this in Ubuntu for some weeks now, I suspect it is a bug but haven't had the time to investigate it further.

---

### Post by ChrisBookwood on 2008-12-05
Yes, it's that message i'm getting, where it lists what it is booting, instead of showing the usplash.

It might be a bug, but I know of many who have no troubles in getting it to show usplash instead of those messages.

---

### Post by ChrisBookwood on 2008-12-05
Come on ... there must be someone who can help me!

---

### Post by ChrisBookwood on 2008-12-05
Now I have tracked down which changes I have done to grub...

First I changed the *kopt* linie in /boot/grub/menu.lst, to make it show what happened behind the screen when booting up.

Some weeks later, I followed [this]("http://lifehacker.com/5098369/more-ubuntu-kung-fu") guide, to make my laptop boot faster.

And then I tried to make grub only show usplash when booting, as it does by default, by editing the *kopt* linie in /boot/grub/menu.lst, but as you may know, it didn't worked, and here I am today.

---

### Post by mtbsoft on 2008-12-05
I suspect the grub changes you made and the message appearing are pure coincidence.  This message is a fairly recent issue for me (a few weeks ago) and I also cannot get rid of them, irrespective of grub settings.  Until last week I was getting a usplash error regularly, this has gone now so people are working on this code - be patient and it'll be sorted soon enough.

---

### Post by ChrisBookwood on 2008-12-06
Well, that sounds at least as if it will get sorted some day.

---

### Post by kkkkdddd on 2008-12-06
Everything after # is a comment.

Have you tried 
```
kopt=root=UUID=09c88f95-3096-4575-a7c1-d144e820c115 ro quiet splash
```

instead of

```
# kopt=root=UUID=09c88f95-3096-4575-a7c1-d144e820c115 ro quiet splash
```
?

---

### Post by ChrisBookwood on 2008-12-06
> **kkkkdddd said:**
> Everything after # is a comment.

Have you tried 
```
kopt=root=UUID=09c88f95-3096-4575-a7c1-d144e820c115 ro quiet splash
```instead of

```
# kopt=root=UUID=09c88f95-3096-4575-a7c1-d144e820c115 ro quiet splash
```?

In menu.lst, that's not correct... ## is comments, and # is options that update-grub uses to generate the list at the end of menu.lst.

---

### Post by sunoccard on 2008-12-06
i got the same issue after installing a new usplash, which doesn't work. i tried reverting it, that didn't work, i even replaced the whole boot.lst and still didn't work, i hope they do something about this soon it doesn't give a very appealing look

---

### Post by RensoreK on 2008-12-10
I have recently been having this exact same issue but was unable to accurately describe it. But yes, the usplash shows for a little bit then is booted into terminal with Reading boot files ..... [OK] and all the loading services are displayed. So I guess its an issue with usplash?

---

### Post by mtbsoft on 2008-12-10
I'm inclined to think it is one of the background processes, shortly before the "Reading Files..." step since, occasionally, I have seen it go through cleanly.  Could be one of those is tripping usplash up, dropping it into terminal mode.  I have a number of other partitions available and will try testing to narrow it down over the Christmas break.

---

