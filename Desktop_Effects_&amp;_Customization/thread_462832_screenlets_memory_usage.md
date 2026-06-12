---
title: "screenlets memory usage"
date: 2007-06-03
forum: Desktop Effects &amp; Customization
---

### Post by rax_m on 2007-06-03
hi 

Is anyone out there using screenlets and noticing the huge amount of memory it's using?
When I start it, it's using about 20MB.. but at some points it goes up to 100
That's without interacting with them or adding or removing any.. 

BTW I'm talking in particular about the screenletsd.py application.. 

Thanks
Rax

---

### Post by BeardlessForeigner on 2007-06-23
I've noticed this. Under system monitor a process called python gradually biuld up to 150 + mb memory used, and stopping screenlets kills this. I wonder if its any particular screenlet that causes it.

---

### Post by Inxsible on 2007-08-02
I notice this too. In fact i was about to start a new thread when I saw this.

Any solutions?

---

### Post by Inxsible on 2007-08-02
My current usage is 850 MB with python taking up 400MB

---

### Post by rax_m on 2007-08-07
I haven't seen any solutions.. I recently stopped using screenlets and started using conky instead.

---

### Post by FuturePilot on 2007-08-07
Same here. Looks like it's a python memory leak or something. I've seen python close to 100MB. At first I thought maybe python just used a lot of RAM but that's **a lot**

---

### Post by c.wilson on 2007-08-07
yep, same here  .. had to shut it down

---

### Post by Deco_21 on 2007-08-07
Yes, its a bug and its documented in the official page of screenlets 
[HTML]http://hendrik.kaju.pri.ee/screenlets/[/HTML]

Find the treath Memory Leak

---

### Post by prince_niceguy on 2007-08-12
I too have this problem. So, I generally kill screenlets in around 1 day or so and restart them. I am thinking of writing a cronjob to do the same :-)

---

