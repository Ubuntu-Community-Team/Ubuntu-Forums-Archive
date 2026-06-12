---
title: "Optimizing the Kernel."
date: 2009-05-26
forum: General Help
---

### Post by Shibblet on 2009-05-26
I just recently tried Sabayon 4.1 Gnome.  I was told that it is a very customizable version of Linux, Gentoo based, and can be tuned specifically for your system.

I realized quite quickly that the reason Ubuntu is "Linux for Humans" is because Gentoo and Sabayon are NOT.  Don't get me wrong, they are great distributions for people who like to configure and tweak.  I personally get tired of that stuff after the first 2 hours.

***So, I know this might be another exercise in futility on my own part, but...***

Is there a way to tweak the Ubuntu kernel to perform better on an AMD Athlon Dual Core processor?

---

### Post by Tristanm1 on 2009-05-26
You could compile your own kernel. I take no responsibility for any problems resulting from that, though. There is some Ubuntu software that does not work without the standard kernel

---

### Post by Shibblet on 2009-05-26
> **Tristanm1 said:**
> You could compile your own kernel. I take no responsibility for any problems resulting from that, though.
No way dude!  You are completely to blame if something screws up!  ;)  Just kidding.

> **Tristanm1 said:**
> There is some Ubuntu software that does not work without the standard kernel
I was thinking more along the lines of some simple optimizations that can be done.  Getting rid of things that I won't use, i.e. Wireless drivers, Printers, Bluetooth, etc.

---

### Post by Tristanm1 on 2009-05-26
That would require compiling your own kernel.

---

### Post by Shibblet on 2009-05-26
Thanks for the quick reply... you must really want that responsibility.  ;)  

Last question... do you really gain that much of a performance increase by compiling your own kernel?

---

### Post by s3MA00RRNY on 2009-05-26
Getting rid of things you don't use won't help, because of the way the Ubuntu kernel is designed. Almost every part is blown out into modules, which are only loaded if necessary. One way to make your system faster though is to build in drivers that your system uses and disable the debugging features of the kernel.

---

