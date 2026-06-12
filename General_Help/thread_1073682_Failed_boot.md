---
title: "Failed boot"
date: 2009-02-18
forum: General Help
---

### Post by kittel on 2009-02-18
About half the time I choose to boot into Ubuntu i will be dropped into a shell with the message:

ata1: comreset failed (errno -32)

then other times it seems to boot normally.

Windows xp is the other OS in my dual boot.  This is more of a recent problem and had used ubuntu for over a month with no problems.  I have had no hardware changes that i can think of.

Any help would be appreciated, thank you.

---

### Post by cariboo on 2009-02-18
Which kernel are you using? to find out, open a Applications-->Accessories-->Terminal and type:

```
uname-a
```

there may be a bug in the kernel that affects your system.

Jim

---

### Post by kittel on 2009-02-18
2.6.27-11

i've tried all the kernels on the menu, and they all have the same problem.

I'm typing this from Ubuntu now.  It decided to load, but if i were to restart there is a 50-50 chance I would run into the same problem.

---

### Post by deeptooth on 2009-06-11
Exactly same problem.

```
ata1: COMRESET failed (errno=-32)
ata1: COMRESET failed (errno=-32)
ata1: COMRESET failed (errno=-32)
ata1: Reset failed, giving up
```After that it either repeats or boots normally.
Sometimes it gives different errors and exceptions but this is the recurring part.

It used to throw me in a rough command line while still spamming the error constantly instead of starting ubuntu but that problem seems to have vanished during my struggling with sound issues and it now eventually starts ubuntu.

It's frustrating tho because it makes booting up take more time than my windows used to.. And that's a sin.

I've read about people fixing this by disabling JMicron, but that would disable all IDE devices.
I've also read it's been happening a lot on P5K motherboards.
My motherboard, however, is not asus P5K but msi P7N Diamond.

Also all posts with detailed hardware info that I've read mentioned 500gb HDDs. In many cases in a "i just bought" context.

Well, I have 2 500gb  HDDs and this problem has been with me from the start of my ubuntu adventures.
That would be around 5 days so don't be too hard on me if I said something silly, please.

Oh, and I'm running kernel version 2.6.28-11.

---

