---
title: "Ubuntu 8.10 crashes"
date: 2008-12-28
forum: General Help
---

### Post by art_s on 2008-12-28
Hi all,

Basically the problem is that my Ubuntu 8.10 freezes, leaving CapsLock and ScrollLock flashing. I read it's called 'kernel panic' but that's as far as my knowledge goes. I tested the RAM and it was ok.

It happens just randomly, not necessary under heavy load.
I have turned off all the heavy graphical stuff like compiz, didn't help either. 

Could you please suggest what would be a way out? :)

Here's some basic info:

uname -a: 
2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

/var/log/messages:
[http://pastebin.com/m3a52648d](http://pastebin.com/m3a52648d)

Thanks!

---

### Post by art_s on 2008-12-28
bumping up...

---

### Post by art_s on 2008-12-29
Up again

---

### Post by fx78 on 2008-12-29
Seems you are using an intel wireless card, I had the same issues. With the same messages (bad scheduling from thread) repeated over and over again in /var/log/kern.log
There is a kernel update in intrepid-proposed that will fix this.

> Starting with 2.6.27-10 from intrepid-proposed this bug is fixed.
See [https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/286285]("https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/286285")

If this all adds up please see [https://wiki.ubuntu.com/Testing/EnableProposed]("http://https://wiki.ubuntu.com/Testing/EnableProposed") for instruction on how to use proposed

---

### Post by art_s on 2008-12-29
> **fx78 said:**
> Seems you are using an intel wireless card, I had the same issues. With the same messages (bad scheduling from thread) repeated over and over again in /var/log/kern.log

I don't think I've got that message in any of logs, though you right - I have intel wireless card.

---

### Post by fx78 on 2008-12-29
Can you try disabling the wireless using a key combo (if possible) and check if the crash still occurs ?

---

### Post by art_s on 2008-12-29
> **fx78 said:**
> Can you try disabling the wireless using a key combo (if possible) and check if the crash still occurs ?

Unfortunately wireless is the only connection I've got and disabling it is not an option, I do need this laptop to be connected all day long. 

Is there other way of finding out what's causing crashes? M.b. some other log files?

Thanks

---

### Post by fx78 on 2008-12-29
AFAIK there is no other way. We need to be sure that the wireless driver is indeed what is causing the problem (otherwise we are just guessing what's wrong and that can take a while :))

---

### Post by JDahl on 2008-12-29
Using kernel 2.6.27-11 from updates-proposed should fix this bug.

The bug is also mentioned here:
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

---

### Post by art_s on 2008-12-29
> **fx78 said:**
> AFAIK there is no other way. We need to be sure that the wireless driver is indeed what is causing the problem (otherwise we are just guessing what's wrong and that can take a while :))

Hm, it's interesting - I have left the laptop overnight with wireless card turned off (using the switch) and it didn't crash. 

However, every time I flick a switch, system freezes for couple of seconds, which is suspicious.

---

### Post by art_s on 2008-12-29
> **JDahl said:**
> Using kernel 2.6.27-11 from updates-proposed should fix this bug.

The bug is also mentioned here:
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

What's the process of updating the kernel to that proposed fix?

---

### Post by ollesbrorsa on 2008-12-29
You actually do not need to update your kernel. The relese notes linked to by JDahl clearly state that "*Users affected by this issue can install the linux-backports-modules-intrepid package, to install a newer version of this driver that corrects the bug.*". 

Hope that resolves your issues.

Br,
ollesbrorsa

---

