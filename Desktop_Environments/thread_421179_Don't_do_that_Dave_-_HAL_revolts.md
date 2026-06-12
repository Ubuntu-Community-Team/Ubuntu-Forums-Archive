---
title: "Don't do that Dave - HAL revolts"
date: 2007-04-24
forum: Desktop Environments
---

### Post by koshatnik on 2007-04-24
Heya,

Whenever i fire up my laptop when im not connected to the internet, it takes ages to load to desktop, and for apps to open. I get a HAL failed to initialize error and my zip stick doesn't work. Very inconvenient when I'm with a client in a cafe and I need to show them some work!

How can I get around this? HAL is mass storage right? Why does it need an internet connection to initialize? 

Thanks

---

### Post by pebo on 2007-04-24
[hardware abstraction layer (HAL)]("http://en.wikipedia.org/wiki/Hardware_abstraction_layer")Sorry, can't help with your problem though...:)

---

### Post by koshatnik on 2007-04-24
Help.

:)

---

### Post by koshatnik on 2007-04-24
Ok, just done it again - if ubuntu cannot connect to the internet while boot into GDM, I get this HAL error and the desktop takes an age to load up. Very very annoying.

---

### Post by tomski on 2007-04-25
have you tried to reintall the hal or the complete os

---

### Post by koshatnik on 2007-04-25
> **tomski said:**
> have you tried to reintall the hal or the complete os

Yep, done both things. Still does it. Something in the boot process is clearly relying on an internet connection. Completely weird.

---

### Post by Lord Illidan on 2007-04-25
I've noticed this too on my father's laptop and my computer. Somehow, they are more responsive when connected to the internet. 
For curiosity, is Automatic Service Discovery enabled on your system under Network Settings?

---

### Post by Seq on 2007-04-25
I'm at work right now, so I'll have to check when I get home to confirm, but I think the problem may be network initialization.

I'm pretty sure network gets initialized before HAL, and I think that X/GDM starts before the entire init process is complete. It is possible that your network card is waiting for a DHCP response, and before it times out and continues on to load HAL, you log into your desktop. A simple test would be to wait about 60 seconds before logging in.

If the above is the cause, then switching to using Network Manager to handle your wired card may be a solution (I do this on my laptop).

---

### Post by koshatnik on 2007-04-25
> **Lord Illidan said:**
>  
For curiosity, is Automatic Service Discovery enabled on your system under Network Settings?

Nope. :) 

Thanks for the suggestions so far. Will leave it for awhile before logging into GDM, see if that helps.

---

### Post by Lord Illidan on 2007-04-26
I've also noticed that on my father's laptop at least, gdm is extremely slow when there is no wifi enabled..it takes like 5 minutes to log into GNOME...and when connected it is near instantaneous..

---

### Post by koshatnik on 2007-04-26
> **Lord Illidan said:**
> I've also noticed that on my father's laptop at least, gdm is extremely slow when there is no wifi enabled..it takes like 5 minutes to log into GNOME...and when connected it is near instantaneous..

Mine isnt quite as long as that, but its a good few minutes. I'm surprised more people haven't reported this as a problem.

---

### Post by tomski on 2007-04-26
i wonder if it its during the boot process i seem to recall from breezy (when you would see the list at boot) doent ubuntu try to synch time to ntp.ubuntu.org or a similar server that provides ntp so you may need to try to disable that 

just a thought mind but worth a check

---

### Post by Lord Illidan on 2007-04-26
> **tomski said:**
> i wonder if it its during the boot process i seem to recall from breezy (when you would see the list at boot) doent ubuntu try to synch time to ntp.ubuntu.org or a similar server that provides ntp so you may need to try to disable that 

just a thought mind but worth a check

Hmm, will try that...but that is at boot process, right? The issue is not at boot time, but loading gdm and normal applications.

---

