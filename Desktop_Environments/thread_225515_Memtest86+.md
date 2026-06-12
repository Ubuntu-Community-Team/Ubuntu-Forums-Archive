---
title: "Memtest86+"
date: 2006-07-29
forum: Desktop Environments
---

### Post by sodapopinski on 2006-07-29
Hello!  complete noob here.  I've been having fun with Ubuntu, and learning a lot!  when I installed Ubutnu last week I edited my menu.lst so that Windows is the primary boot (Although I've been spending much more time in Ubuntu this week...).  Anyway, last night I was messing around and updated a bunch of things using the Synaptic Package Manager.  Well, today now I have another boot option that I don't think was there before.  Ubuntu, Memtest86+.  It now is my default boot as it has taken the "4" spot that windows was in before, bumping windows to 5.  Not a problem to fix, I was just cusious if anyone could explain how this new boot option found its way into my menu.lst.  Should I be concerned?

---

### Post by fensirien on 2006-07-29
> Should I be concerned? No

Memtest86+ is an advanced memory diagnostic utility.

You most likely got it when the update-grub script was executed.

---

### Post by Herman on 2006-07-29
>  Memtest86+ is an advanced memory diagnostic utility.
You most likely got it when the update-grub script was executed. sodapopinski, I agree with  fensirien. Most installations already have memtest 86+ installed automatically already, but maybe yours was missing or not showing for some reason, and the update corrected the situation.

Memtest 86+ is a good thing. You can run it for a few hours if your computer is not working as well as it should. (For example, let it run all night while you sleep). It will tell you if one of your memory cards needs to be replaced.  For a breif introduction (by me), to Memtest plus, [*click here*]("http://users.bigpond.net.au/hermanzone/p15.htm#Memtest86").

---

### Post by sodapopinski on 2006-07-29
Thanks!  I am going to let it run tonight just to see what it does.

---

### Post by jgcamp99 on 2006-07-30
No, Memtest 86 has been there from day 1 of 6.06 LTS that I downloaded/installed around June 01, 2006.

BTW, running it, I guess can't hurt to familiarize yourself with it. But unless you are experiencing computer reboots or flakey unstable behavior, it's really unnecessary torture for your computer memory hardware to go thru.

---

