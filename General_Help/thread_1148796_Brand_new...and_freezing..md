---
title: "Brand new...and freezing."
date: 2009-05-04
forum: General Help
---

### Post by sweet_regina on 2009-05-04
So I've recently switched to Ubuntu exclusively after a multitude of security problems with Windows and though I am happy to have made the change, my computer freezes constantly. Mostly, it will happen while using Rhythmbox but it always occurs when I'm also running Firefox. I have very little experience with Ubuntu as I inherited this computer from a friend and am increasingly frustrated with how often I am having to restart. I don't know quite where to begin even trying to diagnose this problem. Please help if you can. Thanks!

---

### Post by freonchill on 2009-05-04
hardware?

---

### Post by kryptikos on 2009-05-04
Diagnosing something like this can be difficult without seeing the box. This could be something small such as the box just needs more memory to run effectively, or it could be major as the motherboard is going bad. 

Some questions to get you started and maybe get more people interested to lend a hand are:

* what type of computer did you inherit? Brand, model, processor type, amount of memory?

The brand and model should be listed/stamped on the case. To discover your amount of memory open up a terminal (**Applications -> Accessories -> Terminal**) and when that opens type the command **free**. Copy and paste the output here. To find your process...from the same terminal type the command **less /proc/cpuinfo** and print out the information here. 

* How long does your computer run before freezing? Can you duplicate the freezing with any other programs or just by leaving the computer running for a while? 

* Post the contents of /var/log/messages here (again from the terminal) **cat /var/log/messages**

That may help people begin to assist with diagnosing what's going on.

---

### Post by xrecar on 2009-05-04
First of all, Hello and welcome to the forums.
Freezing may be caused by different causes as stated previously.

Do you have on hand or close to you the computer specs?
Is it a custom computer or a brand one (Dell, HP, etc)?
I'd like to know the specs or the model number please.
Also, which version of ubuntu did you install?

---

### Post by sweet_regina on 2009-05-04
unfortunately it's a custom so there's not much i can report on the specifics of the computer. i'm running 8.10. from what i understand, there weren't any problems with the computer in its old home. i do have xp installed on a separate drive. thanks for your help!

---

### Post by xrecar on 2009-05-04
8.10, ok. 
Go to System > Administration > System Monitor. Then click on the system tab

There you should be able to see the following:

Ubuntu:
-----
-----
-----

Hardware:
-----
-----
-----

System Status:
-------------

The lines are for what will show up when you go there. Can you post it here?

---

### Post by sweet_regina on 2009-05-04
Ubuntu : release 8.10 (intrepid)
             kernel linux 2.6.27-11-generic
             gnome 2.24.1

Hardware: memory: 2.0 GiB
                processor 0 : AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
                processor 1 : AMD Athlon(tm) 64 X2 Dual Core Processor 4000+

System Status: Available disk space: 78.0 GiB

---

### Post by xrecar on 2009-05-04
Thanks.
Ok, so at a first glance I don't think it's a resources issue, it shouldn't freeze with that hardware. It is capable of running ubuntu very well.

How long does it take to freeze? 
Is it exclusively with rhythmbox and firefox?
Did you make the ubuntu install yourself or it was there when you received the computer?
In case you made the install, do you have notice of it being the x64 version?

---

### Post by sweet_regina on 2009-05-04
it depends...sometimes it runs without a freeze for a day or so but when i'm active i can restart every hour. for example, i was using only firefox (without rhythmbox) for about five hours and it froze just as i tried to refresh this page a few minutes ago. prior to that, after a restart, it froze in about 30 minutes. it will often freeze, too, on more media heavy sites (wherein the sound may cease to work, as well...though i suspect that's a whole different issue).
i didn't do the install myself so i went into this pretty blind. i haven't any knowledge of it being the x64 version.

---

### Post by xrecar on 2009-05-04
hmm, I recall going through some of those problems on 8.04 but not on 8.10 with the updates, and since you didn't do the install yourself I'm not a 100% sure if a misconfiguration is causing this.

Are you using firefox 2 or firefox 3?
Do you keep your system up to date with the automatic updates?

edit:
when ubuntu boots up, does half of the screen show up brown?
Or have you ever had any problem when shutting down (taking a long time after you've logged out, for example)?

---

### Post by sweet_regina on 2009-05-05
i'm using firefox 3. i made some updates to the computer last night and so far things seem to be running smoothly (and faster, it seems). if i return from work and see that it has frozen again, i'll let you know. thank you for all your help!

---

### Post by xrecar on 2009-05-05
Excellent! Glad to know that the updates helped.
I'll stay tuned.

---

