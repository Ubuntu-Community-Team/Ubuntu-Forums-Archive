---
title: "CPU Fan Going 100% 24/7"
date: 2006-02-10
forum: Desktop Environments
---

### Post by Trev0r269 on 2006-02-10
When I start up my computer, everything is normal but one thing. The CPU fan starts up normally, but never slows down. When I boot windows xp, the fan slows down once a log in. Is there a way I can get it to slow down like it does in XP?

I'm running Ubuntu 5.1 on an Intel P4. I'm not sure what else to include, and I apologise in advance for being a n00b.

---

### Post by byen on 2006-02-10
Im sure there are many solutions to this... but lets start with what worked in my case... Using the right kernel! Are you using the kernel that comes default or have you installed the kernel that is right for you? here is a [link]("http://www.ubuntuforums.org/showthread.php?t=85917") that might help you on getting the one that suits your processor (I think 686)
Hope this helps..I see this is your first post...Welcome to ubuntu and goodluck!

---

### Post by rfruth on 2006-02-10
FWIW Trev my BIOS (AMI on Intel board) can be set to control my fans (I have 3 of um, all in 'auto' mode) :)

---

### Post by Trev0r269 on 2006-02-10
[QUOTE=byen]Im sure there are many solutions to this... but lets start with what worked in my case... Using the right kernel! Are you using the kernel that comes default or have you installed the kernel that is right for you? here is a [link]("http://www.ubuntuforums.org/showthread.php?t=85917") that might help you on getting the one that suits your processor (I think 686)
Hope this helps..I see this is your first post...Welcome to ubuntu and goodluck![/QUOTE]

I was using the default kernal. So I went and got the right one. You were correct about 686. Thank you. I installed it and rebooted (made sure grub listed the right kernal #). The fan is still going strong. I appreciate the kind and fast reply. 

@rfruth
   So how do I fix the fan? (n00bstamp) :D

---

### Post by dcstar on 2006-02-10
[QUOTE=Trev0r269].......
@rfruth
   So how do I fix the fan? (n00bstamp) :D[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=34159&highlight=fan+control](http://ubuntuforums.org/showthread.php?t=34159&highlight=fan+control)

---

### Post by Trev0r269 on 2006-02-10
Thanks for all the fast answers. 

I'm stumbling through setting up lm-sensors right now. Once I get that all set up, I'll report back saying if it did the job.

---

