---
title: "Dell Studio 1557 wireless problems revised"
date: 2010-09-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by i have to use this os on 2010-09-15
Hello Ubuntu users!
I have to write a lot of numerical programs for the university and I use a Linux os like most programmers do. A couple of weeks ago I bought myself a Dell Studio 1557 with a build in dell wireless card and this well known, but still mysterious f2 wireless key. Furthermore, I am using the Ubuntu 10.04 64 version and I am dual booting, because I have Windows7 on another partition.
 I read several threads about this topic but I still cannot fix my problem.
So here it is:

most of the time the wireless function is out grayed and cannot be activated

sometimes the laptop can connect via wireless to a network but it cannot send any data - it just indicates that a connection is established - but it is not.

As I wrote above I tried a lot of things pressing the wireless key for 3 seconds after you log in and sometimes the machine tells me that it is made up an wireless connection  but it did not received or send any data. 

I disabled the energy saving mode in Windows to avoid any complications presented in two or more posts.

I installed the Broadcom STA driver as proposed by the hardware update manager.
I tried it with the b43-fwcutter driver but it failed to work, too.

The situation  seems to be a little bit weird since so many people have/had this problem, so many suggestions have been made but nothing seems to work for all users writing in those threads.
Any kind of clear and not to complicated advice is highly appreciated!

---

### Post by mörgæs on 2010-09-16
Welcome to the forum.

Please tell which card you are using and what you have tried to make it work.

Have you installed all bugfixes to 10.04 using a wired connection?

---

### Post by i have to use this os on 2010-09-16
Hi!
It's a Dell wireless 1397 mini-card with broadcom BCM4315 chip. There is a whole thread about it. Although, I think that more than one problem is discussed there->  **     [COLOR=#980101][B][ubuntu]**[/COLOR] Dell Wireless 1397 WLAN Mini-Card[/B] (of course did I read it before I started my thread) **. **I updated my Ubuntu a couple of times via  Ethernet. I checked the bmwcl-kernel-source and bmwcl-modaliases packages. I tried to use the b43-fwcutter driver as well as the STA driver. 
Sometimes, my computer can detect all available wlan networks! But it doesn't send any data as I can see in the system monitor.

Ok I should have checked this earlier but I found out that this is definitely some kind of encryption problem. I tried to connect to a friends wlan network and we disabled the password.
It start to work. I should rephrase the problem to:

[B]Wlan adapter cannot connect to an secured network
[/B]And there still the problem that once I disabled the wlan I cannot activate it before I reboot the system.

---

### Post by mörgæs on 2010-09-17
Have you also seen this thread? Especially post 53.

[http://ubuntuforums.org/showthread.php?t=1390979](http://ubuntuforums.org/showthread.php?t=1390979)

---

### Post by i have to use this os on 2010-09-17
The first post states that this is a thread for people who have chipsets wich are nor supported by b43
but mine are. I have a 2.6.32 kernel  which should work with my chip set although they recommend the 2.6.33 kernel. Sadly, I have no idea how to change the kernels or the header files or whatever I have to do.
But thank you very much for your time. Maybe things will change after the 10.10 release...

---

