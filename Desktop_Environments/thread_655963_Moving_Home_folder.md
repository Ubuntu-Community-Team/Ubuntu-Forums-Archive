---
title: "Moving Home folder"
date: 2008-01-02
forum: Desktop Environments
---

### Post by marcon00 on 2008-01-02
Hello there, i wanted to make sure how to move my home folder to new HDD, i got myself additional internal HDD for my laptop, and im storing all my documents and files there ... i was reading some tutorials, but i just want to make sure *since im bit new to linux envoirment* that everything will be done Correct..

SO in brief, i have Home FOlder on Sda3 and want to move it to sdb3 ... how can i do that ? and can somone elaborate commands ? for educative purpose :) i don't want to copy past it blindly.. thanks in advance ..

Marcel.:popcorn:

---

### Post by Tyke91 on 2008-01-02
I really have never done this before, but since the home folder *Should* be completely self contained (i.e. no critical system files should be there) I see no reason why you just can't copy/paste it over.

I've found that having a separate /home partition really helps in that respect, because I can do whatever I want with the install and still use the same home folder... upgrading from feisty to gutsy, or even installing another distro altogether are alot less painful.

---

### Post by marcon00 on 2008-01-02
Well thats the point, since i know im goin to mess-up my ubuntu i dont want to bother myself thinkin about home, my docs directory ... but as far as i know .. it doesnt take just copy paste, cuz i want to move it in a way Ubuntu will use it as my home folder :)

---

### Post by zekopeko on 2008-01-02
me thinks that you have to change it in /etc/fstab

could you post the output of 

less /etc/fstab

---

### Post by marcon00 on 2008-01-02
here u go ..
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=e9ecb15e-ed63-4a0a-852a-390c52511150 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=f267ed39-e6e6-47de-a3bf-4ddf63714de4 /home           ext3    defaults        0       2
# /dev/sda1
UUID=068C47278C47109B /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=10F967D93BFAFE09 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=3c340f47-7362-4649-ae90-dfc8235ddc19 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0 

```


EDIT: how u post code within a box? :p for future reference :)

EDIT2: ALright, added [code] box..

---

### Post by ~LoKe on 2008-01-02
**EDIT**: [here](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/) is the guide I followed long ago.


**Ignore the rest of this post if you follow the guide!**
Let someone correct me before you do this, but it should work...

Copy your /home folder to the new hard drive (/dev/sda3).  Then change your fstab from this:
> # /dev/sda7
UUID=f267ed39-e6e6-47de-a3bf-4ddf63714de4 /home ext3 defaults 0 2
to...
> /dev/sda3 /home ext3 defaults 0 2

Again, I'm not sure if that will work, but it *should*.

---

### Post by ~LoKe on 2008-01-02
> **marcon00 said:**
>  how u post code within a box? :p for future reference :)

You can use [cod******e]text[/co******de] which would output like this:
```
text
```

---

### Post by marcon00 on 2008-01-02
> **~LoKe said:**
> **EDIT**: [here](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/) is the guide I followed long ago.


**Ignore the rest of this post if you follow the guide!**
Let someone correct me before you do this, but it should work...

Copy your /home folder to the new hard drive (/dev/sda3).  Then change your fstab from this:

to...


Again, I'm not sure if that will work, but it *should*.
yeah i did read that Guide,just wanted to have second opinion from The Source ;)

---

### Post by kpkeerthi on 2008-01-02
I did this yesterday with some help from [this guide]("http://www.psychocats.net/ubuntu/separatehome"). But I had to change the ownership of my /home **sudo chown -R <login-name> /home/<login-name>** at last to get the whole thing working.

---

### Post by ~LoKe on 2008-01-02
> **marcon00 said:**
> yeah i did read that Guide,just wanted to have second opinion from The Source ;)
Yup yup, it works!  I'm 100% certain it's the guide I used and now I have /home on its own partition.

---

### Post by marcon00 on 2008-01-02
> **~LoKe said:**
> Yup yup, it works!  I'm 100% certain it's the guide I used and now I have /home on its own partition.
alright.. let me try .. be back when im done.. :) lets see how much trouble or not does it cause :)

---

### Post by ~LoKe on 2008-01-02
> **marcon00 said:**
> alright.. let me try .. be back when im done.. :) lets see how much trouble or not does it cause :)

Just make sure you follow it exactly.  Word for word.  If you see any kind of error, or make a mistake, post back here before proceeding.

---

### Post by marcon00 on 2008-01-02
okay , i guess it worked fine .. how can i know that home is on sdb6 now ? cuz it shows under filesystem home, but its mounted into that folder.. i want to know that its there... how can i do that ?

---

### Post by ~LoKe on 2008-01-02
> **marcon00 said:**
> okay , i guess it worked fine .. how can i know that home is on sdb6 now ? cuz it shows under filesystem home, but its mounted into that folder.. i want to know that its there... how can i do that ?

Type this into the terminal:
```
df -h|grep home
```
It should display something like this...
> [03:03:42 loke]$ df -h|grep home
/dev/sda1             220G  191G   19G  92% /home

---

### Post by marcon00 on 2008-01-02
Yup :) its all fine :D ... thanks a lot .. cheers.. and see u soon ;)

*PS: do u know anything about Grub loading stage1.5 problem ? cuz it hangs there sometimes.. i deleted 1.5 stage it now hands less often .. but still does.. any suggestions ??

---

### Post by ~LoKe on 2008-01-02
No problem.  Happy to help.

About the grub problem...please start a new thread in General Help so we can start with a clean slate.  I'll try to get to it.

---

