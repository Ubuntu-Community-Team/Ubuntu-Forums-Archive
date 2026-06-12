---
title: "Quick CPU frequency scaling question"
date: 2009-04-28
forum: General Help
---

### Post by monkeyKata on 2009-04-28
Hello.  I scoured the forums for the answer to this but could not find it, so I wanted to post.

I'm running Jaunty on a laptop with an Intel Centrino Duo processor... so I've got two cpu's.  In system monitor they are listed as CPU 1 and CPU 2.  On the CPU frequency scaling applet, however, my choices for cpu's to monitor are betwen CPU 0 and CPU 1.  I just wanted to know how this worked... do I need to have two applets, one governing CPU 0 and the other governing CPU 1, to effectively control the speed of both processors?  I am curious because I remember reading somewhere that "CPU 0" actually accounted for both processors, though I'm not sure if this is correct.

Just wanted some clarification.  Thanks.

---

### Post by dcstar on 2009-04-28
> **monkeyKata said:**
> Hello.  I scoured the forums for the answer to this but could not find it, so I wanted to post.

I'm running Jaunty on a laptop with an Intel Centrino Duo processor... so I've got two cpu's.  In system monitor they are listed as CPU 1 and CPU 2.  On the CPU frequency scaling applet, however, my choices for cpu's to monitor are betwen CPU 0 and CPU 1.  I just wanted to know how this worked... do I need to have two applets, one governing CPU 0 and the other governing CPU 1, to effectively control the speed of both processors?  I am curious because I remember reading somewhere that "CPU 0" actually accounted for both processors, though I'm not sure if this is correct.

Just wanted some clarification.  Thanks.

You cannot separate the clocking of the cores of a single CPU, so it doesn't really matter which one is used.

If you actually had more than a single CPU, then you can clock them differently.

---

### Post by manuelb on 2009-04-28
In fact, it really depends on your processor specs: my notebook's Centrino Core 2 Duo DOES support independent cpu scaling, but my desktop doesn't.

---

### Post by monkeyKata on 2009-04-28
> **dcstar said:**
> You cannot separate the clocking of the cores of a single CPU, so it doesn't really matter which one is used.

If you actually had more than a single CPU, then you can clock them differently.

Ah so it's actually one cpu with two cores?

---

### Post by monkeyKata on 2009-04-28
> **manuelb said:**
> In fact, it really depends on your processor specs: my notebook's Centrino Core 2 Duo DOES support independent cpu scaling, but my desktop doesn't.

Might there be a way to check?

Right now I have two applets going, one for "CPU 0" the other for "CPU 1."  I have CPU 0 set to performance and the other set to on demand.  One setting does not seem to affect the other (each doing its own thing, performance at 100% and on demand at 50%).  Could this mean that my processor allows independent cpu scaling?

---

### Post by DracoJesi on 2009-04-28
> **monkeyKata said:**
> Ah so it's actually one cpu with two cores?

yep, they "talk to eachother better that way"

well unless your Intel and use the FSB lol, well even then...

@manuelb, really? thats neat, I've never heard of two cores being able to work together under two different frequencies...

I wonder why one would need to /want to do this anyway?

---

