---
title: "Dead monitor on Desktop, how to access"
date: 2009-06-04
forum: General Help
---

### Post by theDaveTheRave on 2009-06-04
Hello All.

Sorry for the rather "cryptic" thread title, but it sums up what my problem is.

We recently moved, and the monitor on my desktop didn't survive the trip. I don't really want to have to buy a new monitor for the system just at the moment and was wondering if it is at all possible to access the system without one?

I know I could SSH, but I'm not sure SSH is set up on this system?

I believe that it is running debian, but don't aks me which one!

If I connect it up to the router will I be able to SSH to it - I will be able to determine the local IP address from information from the router.

In fact reading the above I get the feeling I'm going to be out of luck!

I may have installed SSH at some point in the past on this terminal, but if I set it to use a "key" will I be able to access it with my normal username and password?

Or am I best to just have a go and see.... which is what I will probably do over the weekend.

I know that I have data on this box I don't want to loose, and I have the disk partitioned up to keep things safe etc.

Your thought are appreciated

thanks in advance

David

---

### Post by mixmaster on 2009-06-04
Unless you have the thing set up to act as an ssh server (or even a telnet server) I think you are basically stuffed.  I don't know if debian installs/activates that by default.

Your router admin panels should be able to tell you the IP of the problem machine.

You could pick up a second-hand monitor cheap on fleabay if you have troubles.

---

### Post by hikaricore on 2009-06-04
You can find used crt monitors on auction sites and places like craigslist for super cheap.
You may just be better off doing something like this instead of buying a new one.

Also assuming you're talking about sshing to this box, how do you plan to do that without a monitor?

---

### Post by theDaveTheRave on 2009-06-04
> **hikaricore said:**
> 
Also assuming you're talking about sshing to this box, how do you plan to do that without a monitor?

I was going to do that from my laptop.

I think I did set up SSH on the system, but I'm not sure if I used a pgp key or some such (in which case I am probably stuffed as mixmaster says). If not, I should be able to access with username / password combo. And then bob is your mother's brother ;)

Or at least I hope that is what will work!

Can I throw in a live CD and SSH to that?? or is that again not a possibility? I'm sure that the desktop has a "preboot execution environment" but how do I access the bios without the monitor!?

Could I plug in the keyboard, power on and hit <ctrl.alt.del> and then access the bios from my laptop in some manner??

I'm grabbing at straws now, if you hadn't guessed!

otherwise I guess it is "wait until christmas" for doing an upgrade and getting mythBuntu onto the system (so as we can see some decent TV!).

Ah well... I guess for now all is curtains!

David

---

### Post by Chronon on 2009-06-04
If you have a TV then a VGA to TV adapter might help in the short term.

Here's one for sale for about $4: [http://www.brilliantstore.com/computer_monitor_accessories_dekcell_cpa_1268.html](http://www.brilliantstore.com/computer_monitor_accessories_dekcell_cpa_1268.html)

---

### Post by nebileix on 2009-06-04
Try using remote login from gdm on ur laptop(if running ubuntu as well.) There's option for u to login remotely to another system. 

U will need ssh for the secure remote connection. Or XDMCP.

---

### Post by theDaveTheRave on 2010-10-25
hello all,

sorry forgot to mark this one as now solved.

used an adapter so I could use my old TV.

and now we have a nice shiny new projector TV - so I have a 1.5m wide screen pc experience

:popcorn:

and it was  much  better value than a flat pannel of the same size (and much much much better value than a LED tv).

:guitar:


David

---

