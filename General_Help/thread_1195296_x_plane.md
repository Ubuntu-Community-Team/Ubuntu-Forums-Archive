---
title: "x plane"
date: 2009-06-23
forum: General Help
---

### Post by philcamlin on 2009-06-23
ok i want to try xplane on my ubuntu  machine

i have no idea how to do this and the linux one from x-planr.com doesnt work so im really confused 

can someone point me in the right direction to getting a deb file :popcorn:

---

### Post by xtjacob on 2009-06-23
This might help: [http://forums.x-plane.org/index.php?showtopic=21658](http://forums.x-plane.org/index.php?showtopic=21658)

---

### Post by Subban on 2009-06-23
Is the problem installing (unpacking a tar I think) it, or getting it to run?

---

### Post by philcamlin on 2009-06-23
where o i get it from caus ei got it aparently for linux and its a .exe so its not linux

where can i get it ??    :popcorn:

---

### Post by Subban on 2009-06-23
> **philcamlin said:**
> where o i get it from caus ei got it aparently for linux and its a .exe so its not linux

where can i get it ??    :popcorn:

[URL="http://dev.x-plane.com/update/installers9/X-PlaneDemoInstallerLinux.zip"]http://dev.x-plane.com/update/installers9/X-PlaneDemoInstallerLinux.zip
[/URL]

Ok, it was a zip not a tar.

---

### Post by philcamlin on 2009-06-23
what do i do after that :P

it says open with wine

---

### Post by xtjacob on 2009-06-24
First you have to do some stuff to get it to work:
1. Run sudo apt-get install libopenal1
2. If your on 64-bit run 
```
sudo ln -s /usr/lib32/libopenal.so.1 /usr/lib32/libopenal.so.0

```
3. Double click on the installer and it should run.

---

### Post by Zmrlzna on 2009-06-30
I'm getting the same problem to run the demo of X-Plane, when I try to open the file I get this message:

./X-Plane: error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory

I have installed libopenal1 and already tried with sudo ln -s... as said in the last message.

Some idea? Thanks for your help.

---

### Post by philcamlin on 2009-07-02
thnks i got it running

---

### Post by expressoshot on 2009-07-10
OK I've spent 2 hours forging threw these threads.. and finally for the first time I've decided to create my self a profile so that i can get this working. Here's my problem

When i double click on the X-plane DVD installer, Nothing happens. I've been to the page that tells you to download multiple OpenGl files and rename them etc...., but was not able to do any of that. What i need is a fool proof step by step description. As i seem to be "Terminal illerate" as well.

I feel like quite the new guy! 

Please help, before i take my chain saw to both the ubuntu disk as well as the x-plane disk.

Ubuntu 9.04 64bit
X-plane 9
Nvidia Graphics

---

### Post by opensourcederry on 2009-12-24
Try this link for error below.

error while loading shared libraries: libopenal.so.0: cannot open shared object file: No such file or directory

[http://www.ilovelinux.co.uk/xplane910-1.php](http://www.ilovelinux.co.uk/xplane910-1.php)

---

