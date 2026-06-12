---
title: "UNRAR"
date: 2004-10-18
forum: General Help
---

### Post by tanari on 2004-10-18
how to extract .rar files?
i didn't find unrar package in ubuntu repository

---

### Post by Robin Mehner on 2004-10-18
add

```

deb http&#58;//archive.ubuntu.com/ubuntu/ warty multiverse

```

to your sources.list and you'll find unrar ;)[/code]

---

### Post by tanari on 2004-10-18
thanks

now working

---

### Post by londonbabs on 2007-01-11
yay, it works... thanks, it was blocking me for a while now...

---

### Post by Ramses de Norre on 2007-01-11
Why warty?? That's an incredibly old repo... Both rar and unrar are in the current dapper and edgy multiverse repos.

> ramses@Daedalus:~$ apt-cache policy unrar
unrar:
  Installed: 1:3.5.4-0.1
  Candidate: 1:3.5.4-0.1
  Versiontabel:
 *** 1:3.5.4-0.1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
        100 /var/lib/dpkg/status


---

### Post by usien on 2007-01-11
its amazing that this thread has 7,200+ views nd just 4 replies?:D

---

### Post by rowanparker on 2007-01-11
> **usien said:**
> its amazing that this thread has 7,200+ views nd just 4 replies?:D
I was thinking that.

And even more amazing that londonbabs looked through to find a 2 year old thread and bring it back up.

---

### Post by lynxus on 2007-04-05
Yee ha sorted me aswell.
 :)

---

### Post by Aberrix on 2007-05-02
This trick worked perfect for me! (on 6.06LTS) thanks again!

---

### Post by voidvoidpointer on 2007-07-31
Another solution written by [Ricardo Cabello Miguel]("http://ricardocabello.com/index.php?postid=247") is to
[LIST=1]
[*]Install **xarchiver** with Synaptic (note the final ***R***)
[*]Download both ***rar** and **unrar*** from [RARLAB]("http://www.rarlab.com/rar/rarlinux-3.6.b6.tar.gz") itself.
[*]Install both **rar** and **unrar** in **/usr/bin**.
[/LIST]

---

### Post by Meneldir on 2007-08-01
Another good reason for n00bs like me to stop using Windoze, except for gaming.. i think it's the only good thing to do there... correct me if I'm wrong!

---

### Post by strabes on 2007-08-01
> **Meneldir said:**
> Another good reason for n00bs like me to stop using Windoze, except for gaming.. i think it's the only good thing to do there... correct me if I'm wrong!

You forgot about getting spyware, viruses, and malware!

---

### Post by almightybunghole on 2007-08-08
x

---

### Post by almightybunghole on 2007-08-08
> Another solution written by Ricardo Cabello Miguel is to

   1. Install xarchiver with Synaptic (note the final R)
   2. Download both rar and unrar from RARLAB itself.
   3. Install both rar and unrar in /usr/bin.... or an even easier solution, in Feisty at least, is to just follow the steps in voidvoidpointer's post re. downloading rar/unrar and putting them in /usr/bin, then open the .rar archive in File Roller. 

Job done! :)

---

### Post by kzkirill on 2008-04-12
HI. I have the same problem - can't use rar.
I installed unrar through the Synaptic, but nothing changed. How do I use it?
Thanks everyone.

---

### Post by duncan.hawthorne on 2008-04-12
start a new thread about it kzkirill, dont ressurect old threads.

but install unrar from synaptic, and then doing right click>extract is what you want.
post in a new thread if you have problems, with as much details as possible

---

### Post by talin60_1 on 2008-05-14
Hello,

I've just installed unrar and tried to decompress a .rar file, with 92 other files whose extensions are from .r00 to .r91. It doesn't work since the very beginning, here is the output :

selim@selim-laptop:/media/sda5/Rapishare$ unrar e zry-okami.rar

UNRAR 3.70 beta 3 freeware      Copyright (c) 1993-2007 Alexander Roshal


Extracting from zry-okami.rar

Extracting  zry-okami.iso                                                
zry-okami.iso        - CRC failed
Unexpected end of archive

Extracting from zry-okami.r00


Extracting from zry-okami.r01


Extracting from zry-okami.r02

[...]

Extracting from zry-okami.r21


Extracting from zry-okami.r22

Unexpected end of archive

Extracting from zry-okami.r23


Extracting from zry-okami.r24

[...]

Extracting from zry-okami.r88

Unexpected end of archive

Extracting from zry-okami.r89


Extracting from zry-okami.r90


Extracting from zry-okami.r91

Total errors: 44

Thank you very much

---

### Post by fahadsadah on 2008-06-15
At the time he posted the warty repo, that was the current version of Ubuntu!
That's how old this thread is!

Why can we not let it rest in peace?

---

