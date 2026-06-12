---
title: "AC adapter and battery die in a few days of each other."
date: 2009-03-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by joshuabuild on 2009-03-19
8.10 Dell Inspiron 6400/e1505 

I know this is more of a hardware issue with Dell but I'm trying to figure out if this is an isolated incident or if I should start shopping at System76 for laptops?. A week ago (after two years of ownership) My Dell started telling me that my Battery is "broken" and needs to be replaced. Not a big deal. I know batteries have a half life due to the limitation of the technology but the AC power cord as well? All in a matter of a week? 

I get the warning for the AC at boot stating that the "ac power adapter cannot be determined-you must re-seat the connection". And it went on to say "Your power adapter may make your machine run slow.". 

 WTFrackk is this!? Slow? It made the machine run almost at a crawl, I couldn't even connect to the Internet via wireless....

Electronics are not perfect, I know. This one mind you has been cared for, sat on a desk and never really used the friggin battery! I paid almost two grand for this Laptop I think I should have gotten a bit more out of it before I started seeing issues like this. I don't know I guess I'm just disappointed in Dell. I bought this Dell to support Ubuntu sales. If there is no reasonable solution for this I'm heading over to System76 for sure.

---

### Post by kvroose on 2009-09-14
Hi,

Might be a bit late to answer to your post, but who knows... I also have this issue and have not solved it yet. But I know the cause, that's one part;

Dell built a system in their adapters so the dell computers can only be used with dell adapters.... it's a three way cable instead of the normal 2-way cable. But, here comes the tricky part: if this third (safety)cable is broken, the computer does not recognise the adapter... and you get the message that your system will not charge..

---

### Post by tgalati4 on 2009-09-14
Batteries do start to fail at the 2-year point.  Ever seen a 2-year warranty on a battery?  If a cell shorts out resulting in lower voltage--and lower CPU speed to compensate--then the A/C adapter has to put out more current to make up the power difference.

Let's say you have a 55 watt power adapter and your computer burns 55 watts.  Let's say your average good battery voltage is 12VDC.  There's 4.58 amps of current running through those foreign-produced mosfets.

2 years later, your battery drops a cell and now you are only putting out 10VDC.  Now your laptop still wants to consume 55 watts (power=voltage*current).  So now you have 5.5 amps running through the adapter.

I bet your adapter was getting toasty before it failed.  High current will burn up electronics.  So, no it is not surprising that your adapter failed shortly after the battery warning.

If you want higher-quality internals, you would look at System76 or older IBM Thinkpads.

---

### Post by joshuabuild on 2009-09-15
> **kvroose said:**
> Hi,

Might be a bit late to answer to your post, 

Yeah.. I sold the system a while back at a real loss, three hundred bucks. I'm not dissatisfied with Dell nor with their hardware providers. As it was pointed out by a close friend, I was lucky to get two solid years out of this machine. Either way, Thank you Dell and Ubuntu. I still buy the Ubuntu Dells with out hesitation. 

Cheers!

---

### Post by joshuabuild on 2009-09-15
> **tgalati4 said:**
> 

I bet your adapter was getting toasty before it failed. 

.

No, not so much, I kept everything out in the open on a desk and I had good air flow in the room. It was slightly warm to the touch but only after I had the laptop on battery for a while. But either way you're right, heat is our enemy and things do fail. I was way angry at the time of the posting; I know you can understand. Thanks for the breakdown though..

Cheers!

---

### Post by Whiffle on 2009-09-15
> **tgalati4 said:**
> Batteries do start to fail at the 2-year point.  Ever seen a 2-year warranty on a battery?  If a cell shorts out resulting in lower voltage--and lower CPU speed to compensate--then the A/C adapter has to put out more current to make up the power difference.

Let's say you have a 55 watt power adapter and your computer burns 55 watts.  Let's say your average good battery voltage is 12VDC.  There's 4.58 amps of current running through those foreign-produced mosfets.

2 years later, your battery drops a cell and now you are only putting out 10VDC.  Now your laptop still wants to consume 55 watts (power=voltage*current).  So now you have 5.5 amps running through the adapter.

I bet your adapter was getting toasty before it failed.  High current will burn up electronics.  So, no it is not surprising that your adapter failed shortly after the battery warning.

If you want higher-quality internals, you would look at System76 or older IBM Thinkpads.


I don't think your thinking is correct here.  The battery does not power the laptop while the AC adapter is plugged in.  In fact, the AC adapter is capable of charging the battery and running the laptop at the same time, which requires more power than running just the laptop.  If what you say is true, then even with the laptop plugged in, the battery would eventually die, and that doesn't happen.


My best guess is that the battery may have shorted internally, causing it to be low resistance and draw much much more current than the AC adapter is designed for.  Did the battery get hot at any point?  

Anyway, my T43 is getting close to 4 years old now, works perfectly :)  Although the battery doesn't have nearly the capacity it once did...

---

### Post by joshuabuild on 2009-09-17
> **Whiffle said:**
> 
  Did the battery get hot at any point?
Nope, not at all.  

> **Whiffle said:**
> Anyway, my T43 is getting close to 4 years old now, works perfectly :)  Although the battery doesn't have nearly the capacity it once did...

Lucky *******!

---

### Post by linux_tech on 2009-09-18
Battery life can be anywhere from 1-4 years, depending on the battery and how you use it.  
Powertop can help you minimise the computer's electrical power consumption
[http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)

---

### Post by joshuabuild on 2009-09-19
> **linux_tech said:**
> Battery life can be anywhere from 1-4 years, depending on the battery and how you use it.  
Powertop can help you minimise the computer's electrical power consumption
[http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)

Thanks for the link I'll check it out. If it pans out I'll pass it along.

Cheers!

---

