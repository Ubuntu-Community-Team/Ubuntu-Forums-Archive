---
title: "default dpi is too HIGH"
date: 2009-12-13
forum: Desktop Environments
---

### Post by aa33002 on 2009-12-13
today I want to try ubuntu9.10 & Kubuntu 9.10
but there is something I never expect happened
the default dpi is too high for my LCD!!

My LCD can diplay 1280X1024 dpi screen and is still not enough!
I can't even  install the system
so I use Alternate i386 to install it
and when I get to the GDM
the problem is happened again!

I'm wondering why the dpi has to be so high
higher than 1280X1024?Is that really necessary?

anyway....is that any way I can solve this problem?
I can't even log in to desktop,so we have to solve this in text mode

please help me...I've been google for all night...


ps:

it make me think of the blur's song
she's so high
she's so high
she's so high....

---

### Post by Redache on 2009-12-14
Do you mean Screen Resolution? because DPI is something that is unrelated to a point.

This is probably a problem with your X configuration. 

[This]("https://wiki.ubuntu.com/X/Troubleshooting/Resolution") guide should help you with setting up Xorg.conf.

---

### Post by aa33002 on 2009-12-14
I just found the problem 
my HorizSync is out of rang
my LCD's HorizSync rang is 22-82
but ubuntu9.10 needs 92(?)

even when I try to install system
it still says it need HorizSync 92
is that really need so high?

---

