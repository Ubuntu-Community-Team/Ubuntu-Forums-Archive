---
title: "(Ubuntu 8.10) KERNEL PANIC when i'm downloading anything"
date: 2009-01-31
forum: General Help
---

### Post by DSTR on 2009-01-31
Hello.

I have problem with ubuntu 8.10. When i'm downloading anything (files by firefox, wget, apt-get) my system freeze and I can see an information:

> Kernel panic - not syncing: Fatal exception interrupt 

Moreover I can see on my laptop also blinking "Caps Lock" light. My system acts in this way only when i'm downlading something by internet (downlading files, watching films at youtube, etc).

I've checked logs and i've realised that ALWAYS before Kernel Panic it shows:

> 
Jan 29 23:47:32 arek-laptop kernel: [ 100.128016] wlan0: no IPv6 routers present

I've made also screenshot by my camera:

[[IMG]http://img292.imageshack.us/img292/72/p1000558resized2xs2.jpg[/IMG]](http://img292.imageshack.us/my.php?image=p1000558resized2xs2.jpg)
[[IMG]http://img292.imageshack.us/img292/p1000558resized2xs2.jpg/1/w640.png[/IMG]](http://g.imageshack.us/img292/p1000558resized2xs2.jpg/1/)

Thanks in advance for your help.

---

### Post by Piraja on 2009-01-31
This is just a shot in the dark from a non-tech ignoramus, but you might take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1052932&page=3"), posts #24-25.

---

### Post by DSTR on 2009-01-31
Thanks for instant answer, i've tried that solution but it doesn't work and I still have this problem.

Greetz,

DSTR

---

### Post by damis648 on 2009-01-31
What model wireless card do you have?

---

### Post by DSTR on 2009-01-31
I've checked it in lsusb and it shows:
> 
Bus 001 Device 004: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter

Any idea?

Greetz,

DSTR

---

### Post by kavon89 on 2009-01-31
If there are any other PCs on your network, see if you can transfer a file to and/or from it.

So you can browse websites and use Pidgin etc just fine, but if it comes to a stream or download it panics?

---

### Post by DSTR on 2009-01-31
> **kavon89 said:**
> If there are any other PCs on your network, see if you can transfer a file to and/or from it. 

When i'm trying to transfer file from other pc in my network my system also freezes and Caps Lock light is blinking but it crashes after longer time.

> **kavon89 said:**
>  So you can browse websites and use Pidgin etc just fine, but if it comes to a stream or download it panics?

Exactly.

---

### Post by DSTR on 2009-02-01
Has anyone the same problem with this wireless adapter?

---

### Post by DSTR on 2009-02-01
up!

---

### Post by bigbrovar on 2009-02-02
me think it could be a harddisk problem .. something seem to trigger the kernel panic when there is a disk activity which happens when you try to download or transfer file across network..

---

### Post by DSTR on 2009-02-02
Well, I've found the solution in other topics.

I had to install linux-backports-modules-intrepid package:

> sudo apt-get install linux-backports-modules-intrepid


After installation of this package my system runs correctly and there is no Kernel Panic when I'm using Internet.

Thanks very much for you help (especially for idea that cause of Kernel Panic can be problem with wireless adapter). :)

Greetz,

DSTR

---

