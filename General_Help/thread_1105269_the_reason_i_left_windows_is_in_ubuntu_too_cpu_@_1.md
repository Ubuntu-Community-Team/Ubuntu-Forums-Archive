---
title: "the reason i left windows is in ubuntu too? cpu @ 100%"
date: 2009-03-24
forum: General Help
---

### Post by shateredsoul on 2009-03-24
Hi .. so I've been having problems with my cpu being used almost at 100%.  When I start up my computer I let it boot everything I gave it some time and opened up the system monitor.. it started at 4% good... then it started going up to 20% and then 40% and pretty much goes back between these two before even having opened up any programs.  Opening firefox pushes it to about 60 or 70%, The computer's ram usage in system monitor stays ast about 500 mb of the 2 gigs.. is there anyway I can use this remaining ram to help out the cpu and speed up my apps?

How can I check what programs/processes are using cpu? system monitor says that most of my processes are sleeping

---

### Post by philinux on 2009-03-24
Try the command 

```
top
```

from a terminal

If you have a dual core processor press the number 1 key to see both.

---

### Post by shateredsoul on 2009-03-24
xorg seems to be using a lot of my cpu.. is it something I need?

---

### Post by philinux on 2009-03-24
What are your pc specs?

system>admin>hardware drivers. See if any available. 

Maybe turn visual effects off if pc specs not up to the job.

System>prefs>appearance>visual effects >none

This is my output from top.PC not doing anything.

---

### Post by mhgsys on 2009-03-24
xorg is your graphical interface, your desktop etc

I think you might wanna keep it/

---

### Post by 3Miro on 2009-03-24
> **shateredsoul said:**
> xorg seems to be using a lot of my cpu.. is it something I need?

xorg is the visual environment, you need it in order to use any graphics. Don't kill it.

---

### Post by shateredsoul on 2009-03-24
Is there a way to limit cpu usage for xorg? woudl that be a bad idea? I did search for this.. but kept getting threads with ppl who had problems on macs with cpu spikes... which is similar to what I'm having, but they were told that it was normal.  Is it normal to have xorg goign up to 50% when you aren't using any programs?

---

### Post by philinux on 2009-03-24
> **3Miro said:**
> xorg is the visual environment, you need it in order to use any graphics. Don't kill it.

Disabling visual effects **does not get rid of xorg**. A user would have to uninstall xorg manually then you would not have a gui.

Visual effects are just compiz eye candy but can eat resources.

---

### Post by jminker on 2009-03-24
> **philinux said:**
> 
Maybe turn visual effects off if pc specs not up to the job.

System>prefs>appearance>visual effects >none


philinux makes a good suggestion here. I can tell you that turning visual effects off makes a big difference on my older PC. It's one of the first things I do each time I install the latest Ubuntu.

---

### Post by HermanAB on 2009-03-24
Well, you paid for the CPU, so why are you against using it?

If it needs to run at 100% to get something done, you probably should let it.

Cheers,

Herman

---

### Post by shateredsoul on 2009-03-24
Turning off visual effects helped a lot! The problem I had was on an older pc.  I guess my older pc had trouble with it.  Thanks! for all the suggestions and very helpful support!

---

### Post by hal10000 on 2009-10-15
There is a package [COLOR="Red"]cpulimit[/COLOR] which can limit the cpu usage of a process

---

### Post by elliotn on 2009-10-15
check ur system temperature, mine have a temperature problem if its too hot it reaches 100% easy.

---

### Post by kavon89 on 2009-10-15
This thread is really old guys.

---

