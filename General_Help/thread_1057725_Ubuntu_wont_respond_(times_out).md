---
title: "Ubuntu wont respond (times out?)"
date: 2009-02-02
forum: General Help
---

### Post by catolh on 2009-02-02
Hello there.

I've been having some trouble with my Acer Travelmate 280. The laptop works fine with windows xp, but i want to try out Ubuntu 8.10 and see if this is a better desktop environment for me.

But when i installed ubuntu, it looked like everything just stopped, or paused until i hit a key or touched my touchpad. Then i saw some activity. (I actually let it install overnight, went to bed at 89% and it was 90% when i got back 6 hours later). Since it werent finished, i quickly touched my touchpad and the install started to do something again.

Ubuntu also acts like this when i boot it up, i have to either touch some keys or the touchpad to get it started.

But it wont log into desktop.

Is this a known problem with some laptops? Or is it just that my laptop isnt compatible with ubuntu?

It would be awesome if someone had some experience with this, or even a solution for me.

Thanks a bunch in advance!

Cato

---

### Post by 73ckn797 on 2009-02-02
I will assume that you have searched the forums with your computer model or symptom as a key word?

---

### Post by catolh on 2009-02-02
> **73ckn797 said:**
> I will assume that you have searched the forums with your computer model or symptom as a key word?I have tried searching both on google and here without any spesific results.

Although there might be answers hidden inside long threads. Ill try to have a read now. But thanks for the quick reply though.

edit:

After a quick read, i've come to figure the solution to be the: noapic irqpoll noirqdebug options.
But i dont really understand how to add this to grub after i've already installed ubuntu. I mean, people are telling me to hit F6, but this doesnt work on Grub bootup. I have tried to edit the lines in the Grub installation by appending just the words, and a "-" + the word. (uuid 86069jibberish959 noapic irqpoll noirqdebug)

Any ideas?

---

### Post by catolh on 2009-02-02
Bump

Can someone tell me how to add "noapic irqpoll noirqdebug" to my grub config? I edited the first line wich said "uuid <bunch of numbers>" and added them behind it. But when i then hit "b" to boot it, it only said file not found.

I am sorry for being such a newbie :o

---

