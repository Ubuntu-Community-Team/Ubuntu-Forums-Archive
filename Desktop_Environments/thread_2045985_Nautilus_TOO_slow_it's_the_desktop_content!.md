---
title: "Nautilus TOO slow: it's the desktop content!"
date: 2012-08-22
forum: Desktop Environments
---

### Post by Manuel Cappello on 2012-08-22
After installing Ubuntu 12.04 on my ASUS 1225B all were ok, but just after one/two days suddenly Nautilus became very very slow, leaving me waiting for many seconds even for opening small folders with less than 10 files.

I'm not going to tell you all the tests i done (i tried switching from Unity to XFCE to Gnome to LXDE to Openbox, from Nautilus to Pcman to Thunar...)

At the end i understood that the cause were the big quantity of files i put on the desktop. I mean that i'm used to keep all my files on the desktop,
so it happened i had i.e. 5/10 main folders on the desktop, with some thousands files inside.

**The Nautilus problem literally and suddenly disappeared when i moved all the content of my desktop into the standard document folder in the Home folder.** So, it's clear that the problem i found were due to some hidden work that nautilus does with the conten of the desktop, maybe creating previews or colletcing some other kind of data... 

Manuel

P.S.
i guess the issue of the desktop content is even involved when the slowness of nautilus disappears using ```
gksu nautilus
``` (i mean the content of the root desktop is only a few files).

---

### Post by chenyzvariya on 2012-10-02
Hi, Manuel Cappello, I have the same problem as you but my Desktop folder is empty. How does that happened?

---

### Post by Manuel Cappello on 2012-10-04
Sorry, i guess i'm not able to help you.
May be, if you add some information about your situation, someone else will give you some suggestions....
manuel

---

### Post by Yehonal on 2013-03-22
> **chenyzvariya said:**
> Hi, Manuel Cappello, I have the same problem as you but my Desktop folder is empty. How does that happened?


hi there , i just would share my experience too..and the solution ( if you'll notice slow nautilus suddenly , when it wasn't before )

I'm on ubuntu 12.04 and nautilus 3.4.2 of course, that was really slow opening every kind of folders.

i've tried all solutions on the web:  removing hidden gnome folders from home, uninstalling applets, removing icons from the desktop and so on..


At the end i've reading somewhere that you can notice everything come back fast if you create a new user or just run nautilus using root, in fact it's true because your user could have some broken nautilus config files.

So here you are a simple solution: 

```
sudo killall nautilus
sudo apt-get install --reinstall nautilus
```

just reinstall nautilus , you won't lose anything, let's try it ;)

i hope it will be usefull for someone.

---

