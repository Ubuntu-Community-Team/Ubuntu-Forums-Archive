---
title: "Installing Marble Blast Gold in 10.10 64-bit"
date: 2010-10-19
forum: Gaming &amp; Leisure
---

### Post by steve19137 on 2010-10-19
Maybe some of you have never heard of Marble Blast. If not, I strongly encourage you to google it and watch a video. Its quite addictive. 

Anyhow, I'm, running 10.10 64bit, and Marble Blast Gold simply wont install, where as when i've installed 32bit to the same computer, it installs. 

Heres the terminal output when I run the .sh.bin install:

```
steve19137@steve-CQ61:~$ cd ~/Desktop
steve19137@steve-CQ61:~/Desktop$ ./MarbleBlastGold-1.4.1.sh.bin
Verifying archive integrity... All good.
Uncompressing Marble Blast Gold............................
This installation doesn't support glibc-2.1 on Linux / unknown
(tried to run setup.gtk)

This installation doesn't support glibc-2.1 on Linux / unknown
(tried to run setup)
The setup program seems to have failed on unknown/glibc-2.1


Detecting libc...
Binary file /lib/libc.so.6 matches
Detected: os=Linux, arch=unknown, libc=glibc-2.1

```

It clearly has something to do with glibc-2.1, but after that, I don't know what to do. Anyone?

---

### Post by Perfect Storm on 2010-10-20
Try with;
```
linux32 ./MarbleBlastGold-1.4.1.sh.bin
```

---

### Post by steve19137 on 2010-10-20
thanks! it worked perfectly! would that prefix work for pretty much everything, in theory, if i needed to have 32bit libraries?

---

### Post by Perfect Storm on 2010-10-20
Well, it's rarely you need it - more likely for old close source apps/games. Some might more than that like symblinks and old libs etc.

---

### Post by perishingflames on 2010-12-11
Hi, my name is Aaron and I am representing the Marble Blast Forums ([www.marbleblast.com](www.marbleblast.com))- I suggest you register an account to join the Marble Blast community!

Some members in the past have inquired about installing the game on Ubuntu, but atm we can't offer much help. Would one of you kindly post a short tutorial on how to install the game?

This is a double concern to us because we would like to offer full Ubuntu support with the "official"ish mod Marble Blast Platinum ([www.philsempire.com](www.philsempire.com)), and the upcoming PlatinumQuest. You can also read more about that on the forum, and I suggest you check it out yourself if you enjoy Marble Blast Gold! And of course, it's free.

Thanks.

---

