---
title: "Deleted user folder after mounting external hard drive"
date: 2009-06-09
forum: General Help
---

### Post by umeboshi80 on 2009-06-09
Hi!

I am not sure what I did, but the consequence was drastic. I wanted to gain write access to my external hard drive and searched the forum. One thread said to look for where the drive was mounted and I checked it with fdisk. The I did the following (following the instructions from the thread):

sudo mkdir /media/external
sudo mount -t auto /dev/sdb1 ./external

I got no error messages but when I cd to my home folder and then my user....IT IS EMPTY. I cannot start Nautilus, I cannot do ANYTHING.

Can anyone please tell me what happened and how i can fix it?

Very much appreciated (since in panic mode)...

Hadassa

---

### Post by nothingspecial on 2009-06-09
It looks like you`ve mounted your external drive to your home directory.

It sould be ```
sudo mount -t auto /dev/sdb1 /media/external
```

not sudo mount -t auto /dev/sdb1 ./external

This assumes you were in your home when you mounted it.

Post the output of ```
mount
```

---

### Post by umeboshi80 on 2009-06-09
Hi!

First of all: thanks for replying! Second, unfortunately I rebooted the computer and so
don't remember what the error messages were. Third, everything seems to be fixed now...i.e. I can access my folders...everything is there. Is it possible that I did not make any permanent change to permissions etc. (still cannot believe the happy outcome and trying to understand what my command actually did)? 

Thaaaaaanks!

---

### Post by nothingspecial on 2009-06-09
Hi, no problem.

There is nothing wrong with the commands in them selves

The problem is the directory you were in. If you had been in /media it should have worked no problem but I`m assuming you were in your home directory.

A full stop, dot, period (whatever you want to call it) is interpreted by bash (the terminal) as the directory you are in so ./ means where I am now.

I think you managed to mount your external drive to your home and you were actually viewing the contents of your external drive which I`m guessing was empty.

Of course I could be wrong (just cause I have a lot of posts doesn`t mean I`m an expert - you get counted when you ask a question as well !!)

When you rebooted the drive was unmounted and thus everything returned to normal.

Try to understand a command before you type it in. A while back a troll on these forums was posting a command that can nuke your entire system for real. And anyone can make a typo.

---

