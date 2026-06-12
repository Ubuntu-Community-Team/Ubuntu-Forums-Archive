---
title: "Dell Inspiron 1525 Battery not charging (Ubuntu 10.04)"
date: 2010-04-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gggg-go on 2010-04-30
so my laptop has the dell power cord directly from dell and it will charge in windows vista, but when i drain the battery in Ubuntu 10.04 and then plug in the cord it will automatically say battery fully charged.

then i unplug again and the battery will of have the same loss of charge as when i last drained it. 

so is there going to be a fix from Ubuntu soon?

---

### Post by BrownHorse on 2010-05-02
I have exact same problem on my dell inspiron 1525. Atleast this makes me feel batter it can't be a defective Bat. Must be OS related issue. some1 plz helpppppppp :)

---

### Post by northking on 2010-05-02
I had this problem on my Inspiron 1525 when I had 64-bit Ubuntu. I also could not make wireless work. I then remembered I could not get a 64-bit driver for the Broadcom bcm43xx series wireless for 64-bit microsoft windows. Same for Ubuntu? So I installed the 32-bit Ubuntu. Wireless works perfectly and so does battery. Are you folks perhaps using 64-bit OS?

---

### Post by BrownHorse on 2010-05-02
> **northking said:**
> I had this problem on my Inspiron 1525 when I had 64-bit Ubuntu. I also could not make wireless work. I then remembered I could not get a 64-bit driver for the Broadcom bcm43xx series wireless for 64-bit microsoft windows. Same for Ubuntu? So I installed the 32-bit Ubuntu. Wireless works perfectly and so does battery. Are you folks perhaps using 64-bit OS?

I thought I had downloaded 32 bit version. I just ran uname -a command and here is the output

Linux xxx-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

Looks like I do have the right ver (32 bit)

---

### Post by BrownHorse on 2010-05-02
Hello all, this thread can be marked as RESOLVED.

I was finally able to get my battery to charge. Here is what I've done  to resolve my issue

1. I went to Bios set up and loaded Factory Default Settings4. 

2. Power off the laptop and also disconnected AC Adapter

3. Also reseated cable that goes from AC Adapter to wall outletW

4. Plugged everything back in and all of a suddent my battery is now  charging.

---

### Post by isbiyanto on 2010-05-18
> **BrownHorse said:**
> Hello all, this thread can be marked as RESOLVED.

I was finally able to get my battery to charge. Here is what I've done  to resolve my issue

1. I went to Bios set up and loaded Factory Default Settings4. 

2. Power off the laptop and also disconnected AC Adapter

3. Also reseated cable that goes from AC Adapter to wall outletW

4. Plugged everything back in and all of a suddent my battery is now  charging.

Not works for me (lenovo 3000 G410). but thank for advise

---

### Post by Foxyfabio on 2010-06-13
none of this works for me. 
AHHH!!!

i cant open aircraft manager.

---

### Post by ankanaan on 2010-12-22
I have a dell inspiron 1525

r2d2:~> cat /etc/issue
Ubuntu 10.04.1 LTS \n \l

r2d2:~> uname -a
Linux r2d2 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 10:14:11 UTC 2010 x86_64 GNU/Linux

Just bought a new 12cell battery from dell.  

When I try charging the battery Ubuntu says it is 31% charged, never more than that.  And if I unplug the charger it says I have 1h31m left.  I am now running the machine non-stop to see how long it will last and see if the battery is really not charging or if the system is reporting a wrong value.

cheers,

Antonio

---

