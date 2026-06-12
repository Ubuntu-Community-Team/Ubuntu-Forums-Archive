---
title: "Dell 1900 Ubuntu won't install"
date: 2007-07-16
forum: Dell  Ubuntu Support
---

### Post by scorgie on 2007-07-16
Hello there,

I recieved my brand new Dell 1900 this morning. It came with a Braodcom NetXtreme II gigabit NIC card :). The 6.06 versio of Ubuntu doesn;t like the card and thinks it is a firewire card. I have tried xseveral different ways to get around it. Saying YES this is what I want to use, NO this isn't what I'm going to use etc. The CD doesn't boot to anything but the install screen. 

Did the bit check sum thing and all is good.

Here is the wierd thing, I popped in my CD of the desktop version and no problem. The thing goes straight through tot he desktop.

Any ideas why the server version won't work. Should I try the 7.0 version on Ubuntu?

Thanks in advance

---

### Post by kc2keo on 2007-07-17
> **scorgie said:**
> Hello there,

I recieved my brand new Dell 1900 this morning. It came with a Braodcom NetXtreme II gigabit NIC card :). The 6.06 versio of Ubuntu doesn;t like the card and thinks it is a firewire card. I have tried xseveral different ways to get around it. Saying YES this is what I want to use, NO this isn't what I'm going to use etc. The CD doesn't boot to anything but the install screen. 

Did the bit check sum thing and all is good.

Here is the wierd thing, I popped in my CD of the desktop version and no problem. The thing goes straight through tot he desktop.

Any ideas why the server version won't work. Should I try the 7.0 version on Ubuntu?

Thanks in advance

I am a bit confused here. You want to install the 6.06 version of Ubuntu Desktop and it does not recognize your network card?

Try using the 7.0 version of Ubuntu like you said.

Not sure why the server version would not work. The server version uses a text-base ncurses installer so it should work. I installed the 7.04 version of it and it went fine for me. The servers been running for 3 days so far.

---

### Post by scorgie on 2007-07-17
Thanks for the reply.

Sorry for the confusion. I want to set up a RAID 1 configuration using Ubuntu server. Version 6.06 see's my gigabit network card as a firewire card and no matter how I answer the question the install hangs.

When I - just for a laugh - tried the desktop version, which I run my laptop on, the install went through fine.

So after my post I ran 7.04 and the install went ok. The problem with the 7.04 install was that it didn't see both of my SATA drives. Ug.

So now I'm giving 6.06 Alternate CD and have the same issues. 

Any thoughts?

---

### Post by arno_de_Parno on 2007-07-24
The network card thing is exactly the problem I'm having...

I use a Mandriva for some 20 months now, but I really need a server... I don't (already)  feel at home with the apt-get - Mandriva is rpm-based. So could anyone tell me **if** and **how** i can safely install LTS server and use the network package from the desktop version? 

I've been playing with the desktop LTS (on my private laptop)... and I really like what I see... I'm not a big disto-hopper but for a server I have no alternative ;)

---

