---
title: "Dell Inspiron 1564 Core i3"
date: 2010-04-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by IleaCristian on 2010-04-28
Hello!

Recently I bought a Dell Inspiron 1564  Intel Core i3 , 3GB Ram etc. and it has Intel HD Graphics (which as I found out it's some technology integrated in the processor, without having the trouble of installing another separated graphics card).

Anyway, I installed Windows 7 (32) and it works great. Of course, not as great as ubuntu would run. I tried to install ubuntu 9.10 (32 bit) but after the option menu, no matter what option I select, the screen turns black (even when I want just to test without installing anything). The HDD LED flickers a bit but after a while nothing happens.
 
Some forum users have suggested to install the beta 10.04 so I did (the 32 bit version). It worked fine for a while BUT: it had  some issues.  After a while the system freezes ( but as weird as it may seem, the radio stream doesn't stop playing  :P ). Also when several programs ware running, the system was a bit laggy.  So I stopped working on ubuntu because it was becoming annoying.

My questions for you:

Is there any chance that the new release(10.04) will work well on my laptop?

Is there any stable ubuntu release working good for my laptop?

If there is no ubuntu release that can work on my laptop, is there any LINUX release working on my laptop?

...and sorry for my bad english and long boring post.

---

### Post by IleaCristian on 2010-04-29
Somebody? :(
bump

---

### Post by Si2100 on 2010-04-30
Hi, 

I've got a Dell Studio 1558.

which yesterday i instaled 9.10 ubuntu. 

but now i've updated the system to 10.4... although i have got no sound atm

---

### Post by mikewhatever on 2010-04-30
There was an xserver memory bug in 10.04. Please update your system, it's been a while since Lucid was in beta.

---

### Post by IleaCristian on 2010-07-10
I installed the latest release (64bit) and I still have problems. 
Usually sometimes the left click of my mouse stops working suddenly and sometimes I can't type. 
I updated ubuntu several times until now  but I still have the problem.

---

### Post by yaseenes on 2010-07-11
> **IleaCristian said:**
> I installed the latest release (64bit) and I still have problems. 
Usually sometimes the left click of my mouse stops working suddenly and sometimes I can't type. 
I updated ubuntu several times until now  but I still have the problem.

hi IleaCristia
i have a same dell 1564 like u.i installed ubuntu 10.04 without any problem.just a wireless problem.
but i haven't seen any hang or etc. i installed 32 bit version.i think you should install 32 version because your processor is not AMD.try 32 bit version. i hope your problem will be solved.

---

### Post by YEEH on 2010-07-13
Hi, 

I have a 1564 with Core i5 and I had some issues when I first installed the 64bits Ubuntu 10.04, like running slow and using the poor graphic like mad. But after having installed the latest kernel(2.6.34), all the issues seem to be solved completely. Maybe you should try that.

---

### Post by malikkabanis on 2010-09-14
[FONT=Times New Roman][SIZE=3]Hey friends,[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I bought also same dell 1564 i3 4GB ram..[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I use ubuntu 32 bit. I works fine.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Now I want to install kernel 2.6.34 on my laptop.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]And my doubt is simple..[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I use ubuntu 32 bit so which kernel should I install kernel 2.6.34 amd64 or kernel 2.6.34 i386??[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]because some says dell 1564 i3 is 64 bit laptop and I have windows 7 64 bit also on my laptop works fine.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Help plz.[/SIZE][/FONT]

---

### Post by teh603 on 2010-09-16
> **malikkabanis said:**
> [FONT=Times New Roman][SIZE=3]Hey friends,[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I bought also same dell 1564 i3 4GB ram..[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I use ubuntu 32 bit. I works fine.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Now I want to install kernel 2.6.34 on my laptop.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]And my doubt is simple..[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I use ubuntu 32 bit so which kernel should I install kernel 2.6.34 amd64 or kernel 2.6.34 i386??[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]because some says dell 1564 i3 is 64 bit laptop and I have windows 7 64 bit also on my laptop works fine.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Help plz.[/SIZE][/FONT]
Use the i386 kernel, which is the 32-bit one. You don't want to use the AMD64 kernel unless everything you're running is AMD64. As you just said, however, you're running i386, so stick to that kernel.

---

### Post by malikkabanis on 2010-09-17
[FONT=Times New Roman][SIZE=3]I will be thankful if somebody explain me how to get our Dell 1564 wifi working.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Every time I install new kernel and boot to new kernel wifi is broken.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]And I spent many days searching googling doing as said..[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]But I fail..[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Please explain me simple process of getting our wifi working.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Dell 1564 i3 4GB[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]-- wifi Broadcom.[/SIZE][/FONT]

---

### Post by iisr on 2010-12-03
Hi. In one of your posts you said the cabled connection for internet was working. I have a dell 1564 with ubuntu 10.04 a similar configuration as yours(you mentioned it). I have a problem with the wired connection. Please help me out.

---

