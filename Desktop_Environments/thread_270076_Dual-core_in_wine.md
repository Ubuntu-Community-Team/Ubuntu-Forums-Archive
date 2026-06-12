---
title: "Dual-core in wine?"
date: 2006-10-02
forum: Desktop Environments
---

### Post by acordes on 2006-10-02
First of all, since I'm new around here and Ubuntu, let me congratulate you all about this truly magnificent forum and support granted here. I found the answers to 99% of my questions, and only this one remains :D

Basically, wine doesn't seem to be making use of my second processor/core (I'm running an AMD X2 Dual-Core), and this is critical to me since I am using a rendering program that greatly benefits from this. The rest of the operative system has successfully detected the processor architecture and has no problems with it whatsoever.

So the question is, does wine support dual cores? If so, is there any way of enabling support for the second processor? I am certain that the core isn't being used as I can only see one rendering thread (I could see both of them under Windows).

And that's it - this last detail is all I would need to be released from Windows, hehe 8)

Many thanks in advance!

---

### Post by acordes on 2006-10-04
Bump!

I know this one can be tricky but anything you can tell me would be of great help. I understand there's a SMP version of wine, or perhaps that's already integrated in the latest releases?

I'm really clueless about this and it's truly the final step I need to complete my transition to Ubuntu :-?

---

### Post by dyous87 on 2006-10-04
Are you sure that Linux even recognizes your dual processors because I have an Intel Core Duo and I'm not even sure how to find out if it does.

---

### Post by acordes on 2006-10-04
Yes, I am 100% sure of this because I can see both cores in the System Monitor panel. Plus, both of them show reasonable levels of activity under normal operation. However, if I run one single wined application, such as the renderer, only one processor is used.

And regardless of levels of activity, I am certain that wine is only using one processor because the wined application (which BTW is Cinema 4D) is only showing one thread while rendering!

---

### Post by kspn on 2007-08-07
Hi
I am wondering about the answer to this as well, primarily for gaming purposes.

I know that my system is recognising the Dual core CPU but I am fairly certain the only one core is being used for the games (Guild Wars)

---

### Post by kspn on 2007-08-09
I have done some checking on my system and when I launch Guild Wars one CPU hits 100% the other sits at idle!!!

Anyone know if it is possible to kind of -force link- the CPU's so that if I have a single threaded application I can spread the load across both CPU's in my system.

. . .

. . . .

. . . . . 

Actually that sounds next to impossible.

As another option anyone know how to configure WINE to run in dual Core Mode (SMP I think)

---

### Post by Eion on 2007-08-10
It wont even let me get wine, says that my system is not supported at this time. . .ect ect

Maybe a dualcore friendly release will come soon?:confused:

---

