---
title: "install vanilla kernal patch help"
date: 2006-04-16
forum: Desktop Environments
---

### Post by zorlab on 2006-04-16
I know it is a bit  premature to begin re-compiling the kernel (right term?)have only newly experienced Ubantu.. and only having minor experience with terminal commands.
I tend to dive in...

 here is what I have begun to do:
[COLOR="Teal"]**apply a patch to the the official vanilla kernel sources. (which install) This patch gives you roughly 95% preemption, as compared to about 50% preemption without the patch.**[/COLOR] 
This is for improved Audio Editing performance.

Ref: [http://ubuntustudio.com/wiki/index.php/Breezy:Vanilla_Kernel_With_Realtime_Preemption](http://ubuntustudio.com/wiki/index.php/Breezy:Vanilla_Kernel_With_Realtime_Preemption)

I got all the way through  install kernel-packages with 2 errors.

```
In file included from drivers/net/skge.c:43:
drivers/net/skge.h:2477: error: duplicate member ‘hw_lock’
make[3]: *** [drivers/net/skge.o] Error 1
make[2]: *** [drivers/net] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.15.6-rt21'
make: *** [stamp-build] Error 2

```

In the walk through  the next step was 
[B]"Once that is complete with no errors, you can then install the new deb packages"
[/B]

Ignoring the errors I tried the next step but cannot go further,  the file **[COLOR="Teal"]*2.6.15.6-rt*.deb[/COLOR]**
_is not there._

Is there something to do?  something I missed?  or should I crawl back to baby steps and leave this to another time? :-k :-D :-D

---

### Post by zorlab on 2006-04-17
I feel unworthy,:-| :( 
Bump

---

