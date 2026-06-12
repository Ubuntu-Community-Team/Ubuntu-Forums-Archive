---
title: "Mouse freezing after 2- 15 min on Ubuntu 10.10"
date: 2010-10-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by petibor on 2010-10-14
Hello,
My mouse keeps freezing after 2 to 15 minutes using Ubuntu 10.04 and 10.10(I was hoping that upgrading would solve the problem). I usually ise a logitech optical mouse, pretty much the basic model, and have tried with a different to be sure it was not a hardware problem. I have even tried with two mice plugged in, it somewhat delays the problem, since one of the two stops working before the other. Same thing for plugging the mouse in a different USB port, it just delays the problem. 
I have not found a solution browsing on the forum, I therefore ask for help!
I'm running on a dell Dimension C521 with AMD Sempron 64bit processor (quite old 2005)

Thanks!

---

### Post by mörgæs on 2010-10-15
Hi, welcome to the forum.

How does it work, if you boot the machine with a PS/2 mouse?

---

### Post by petibor on 2010-10-15
Like most newer dell desktops, my computer does not have a PS/2 connection. 
Maybe I could try with PS/2 to USB adapter. Coming back with feedback on this try.

---

### Post by petibor on 2010-10-16
Turns out that finally I do not own a PS/2 mouse. So no luck trying out that path to solve the problem. Any other ideas?

---

### Post by mörgæs on 2010-10-16
Then the memory will be a good first check. If you run memtest (might take all night), do you get any error messages?

---

### Post by petibor on 2010-10-16
I'm kinda noob... How shall memtest be done?

---

### Post by petibor on 2010-10-16
I found out by my self what memtest was, ran it and it found no errors. Meanwhile I also found out that if a mouse died in a port, the port would not recognise any thing after that, keyboard for example, as if it was not existing any more.

---

### Post by rapidrocket7 on 2010-10-16
I encountered this problem before, numerous times. Every time the same solution fxed it for me. Try adding noapic to the kernel. There are a few ways of doing this but I'm too busy to remember them. Hope I helped.:guitar:

---

### Post by JuliusRaphael on 2010-10-16
Im in the same situation as TS, same problem, also a Ubuntu noob. I found this thread: [http://ubuntuforums.org/showpost.php?p=9427926&postcount=1](http://ubuntuforums.org/showpost.php?p=9427926&postcount=1) which might help but I don't completly understand it. Maybe someone can help us with a step by step guide how to do everthing?

Thanks!

---

### Post by mörgæs on 2010-10-17
Hi Julius, welcome to the forum. 

I don't think it can get any more step-by-step. What exactly is going wrong, when you are following this guide?

---

### Post by JuliusRaphael on 2010-10-17
Hi! I misunderstood the other thread, however I managed to do what it said but it still doesn't work. Any Ideas?

---

### Post by petibor on 2010-10-17
> **JuliusRaphael said:**
>  I managed to do what it said but it still doesn't work. Any Ideas?

Same here!

---

### Post by JuliusRaphael on 2010-10-17
My problem solved when I updated the bios.

---

### Post by UbuNoob001 on 2010-10-20
> **JuliusRaphael said:**
> My problem solved when I updated the bios.

can you explain for us newbies? I am having the same problem: 
Dell Inspiron 1545 fresh install of 10.10, used to use 10.04 with no problems. 
Every 2 min or so, the tracpad/arrow freezes for about 15 seconds. Frustrating...
10.10 is beautiful but will have to revert w/o solution.

---

### Post by Kushman on 2010-10-21
I am also having the same problem. Started as an Ubuntu enthusiast and the ubuntu 10.10 is my first installation. Lots of problems, but first things first...the freezing mouse/touch-pad. Mine actually gets frozen from the start. I use touch pad on laptop. So I am forced to use the keyboard to navigate which is frustrating.
 
Seems that this is a recurring problem, from discussions with ubuntu users.
 
Hopefuly it will be laid to rest once and for all. It is just annoying.

---

### Post by djthree on 2010-10-25
Same problem.

I´m  HP Pavilion DV4-1425  wich UBUNTU 10.10

Touchpad freezes...

---

### Post by mörgæs on 2010-10-26
It would be easier to give an answer if people provided more background information. 

What has been tried until now? Memtest? Upgrading BIOS? Does it work when booted in 10.04? And so on.

---

### Post by novidan on 2010-10-27
Hi,

I have the same problem on my HP dv5-1000us laptop. My touchpad and usb mouse freeze instantly after I log in. I didn't encounter such a problem until now and i have been using ubuntu since 8.10 version.

After doing a little search it seems that there is a bug in the latest kernel release (version 2.6.35-22), but i haven't been able to get around it. Any suggestions???  

Thanks,
Dan.

---

### Post by mörgæs on 2010-10-27
You can change kernel in 10.10, but the easiest way to get around it is simply installing 10.04.

---

### Post by heron7 on 2010-10-28
I have had the same issue ,I have tried just about everything ,mind you that was while running windows but it's the same i'm guessing :If you have just done any partitioning recently. the only way i could fix it was removing all of windows & do a clean install of  the live cd Ubuntu extended . That's becuase I suck at cleaning up or setting up partitions . There are Plenty a tool to get you a picture of how & what is on your drive. Gparted comes to mind .

---

### Post by arju305 on 2010-11-03
Can you tell me "HOW YOU DID IT". actually i donot have that probem. But want to learn the way. This problem is mostly seen in ubunt 10.10 these days.
Run memtest.
Upgrade bios....
Does this solve the problem.

---

### Post by GJMY on 2010-11-11
Hi, i am new to Ubuntu and I have recently installed 10.10 on my **Dimension C521 Athlon 64 desktop**. (No partitions and no Windows). 
After reading all the forums I have **upgraded the bios** to the latest version, but this didn't solve the problem. I have tried using a **usb hub** which hasn't solved the problem either. 
I will try memtest later today and see if I can detect anything.
Does anyone have any other suggestions. It appears that this problem has been going on for about 4 years now. Someone must have found something by now!!

---

### Post by mörgæs on 2010-11-12
Hi, welcome to the forum.

> **GJMY said:**
> It appears that this problem has been going on for about 4 years now.

Maybe, maybe not. There have been mouse problems for several years, but this does not necessarily mean the same unsolved problem. Could be one mouse problem solved and a new appeared (a regression). 

Because of this, it is important to try a few older releases in a live boot for comparison. Have you tried 10.04.1?

---

### Post by petibor on 2011-01-20
Problem solved by updating the bios.

I had to reinstall windows to do sow since no executable version of the update were available for linux and it can't be runned through Wine. Works like a charm now though.

---

### Post by docmojo on 2011-05-09
Hi guys, I am a novice in these technical issues...

But faced this mouse freeze prob for a few days... Just struck me that, I had installed ClamAV prior to this glitch... So removed it from the system, and the problem seems to have disappeared... 

Do you'll have it installed too?

---

