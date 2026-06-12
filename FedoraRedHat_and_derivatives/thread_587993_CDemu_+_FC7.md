---
title: "CDemu + FC7"
date: 2007-10-22
forum: Fedora/RedHat and derivatives
---

### Post by janschan on 2007-10-22
Hello,
There are some error when I tryed to install CDemu 0.8 on my Fedora 7.
They seemed like below:
> 
[root@localhost cdemu-0.8]# make
make[1]: Entering directory `/usr/src/kernels/2.6.22.9-91.fc7-i686'
  CC [M]  /root/cdemu-0.8/cdemu_core.o
  CC [M]  /root/cdemu-0.8/cdemu_mod.o
/root/cdemu-0.8/cdemu_mod.c: In function &#8216;cdemu_exit&#8217;:
/root/cdemu-0.8/cdemu_mod.c:198: error: too many arguments to function &#8216;invalidate_bdev&#8217;
make[2]: *** [/root/cdemu-0.8/cdemu_mod.o] Error 1
make[1]: *** [_module_/root/cdemu-0.8] Error 2
make[1]: Leaving directory `/usr/src/kernels/2.6.22.9-91.fc7-i686'
make: *** [default] Error 2

And my kernel:
> 
[root@localhost ~]# uname -a
Linux localhost.localdomain 2.6.22.9-91.fc7 #1 SMP Thu Sep 27 23:10:59 EDT 2007 i686 i686 i386 GNU/Linux


And when I install it on my another PC , it done well , its kernel is **2.6.21-1.3194.fc7**.

It's something in different kernel?

So what shall I do?

Thanks!

---

### Post by igknighted on 2007-10-23
What is this app?  What does it do?  Why does it need to build against the kernel source/headers?

---

### Post by drama1981 on 2007-10-23
> **igknighted said:**
> What is this app?  What does it do?  Why does it need to build against the kernel source/headers?

it appears its a kernal module. it simulates a cd drive/cd with simple cue/bin files. looks interesting.

[http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/)

---

### Post by janschan on 2007-10-23
> **igknighted said:**
> What is this app?  What does it do?  Why does it need to build against the kernel source/headers?

It's just like Virtual CD in Linux , as Daemon Tools for Linux .

You can find some details in [this]("http://cdemu.sourceforge.net/")!

---

### Post by igknighted on 2007-10-23
What's the point?  Why not just mount the iso image?  I didn't think you needed a program like this.

---

### Post by Antman on 2007-10-23
> **igknighted said:**
> What's the point?  Why not just mount the iso image?  I didn't think you needed a program like this.

It seems to mount Bin/Cue files too. I don't think you can directly mount a Bin/Cue file in linux without converting it to ISO first.

---

### Post by janschan on 2007-10-23
As we known , there are two ways to let us mount the bin/cue file(not limited by OS) .

1.Covert it to ISO file , then , mount it.(Just waste time and space)

2.Diretly mount it.

If we are in Windows , we can use Daemon Tools or other Virtual CD tools to directly mount it.

Now we are in Linux , So we must find a way to directly mount it . That's CDemu . 

In CDemu you can build a virtual CD-driver to mount bin/cue .

That's all .

In fact I came from China , I am not good at English , some words must not be correctly .

---

