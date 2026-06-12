---
title: "E1505 fans not working"
date: 2007-07-26
forum: Dell  Ubuntu Support
---

### Post by rscheckler on 2007-07-26
I own a Dell Inspiron E1505N and ever since I received it, I have not been able to get the fans to work correctly. From the factory the fans never turned on so I installed i8k hoping that I could at least gain some control over my fans. Now I can manually control the fans with i8kmon but I want to have it so the sensors will automatically turn on the fans when the sensors reach a certain temperature. No matter how much I try, I cannot get the fans to automatically turn on through gkrellm even when I set the temperature ranges through it. I am still semi-new to Linux so it might just be that I am missing something. Does anyone have any idea what is wrong? Thanks in advance!

---

### Post by Papi-KB7VGW on 2007-07-30
Hi.  Sorry that it has taken so long to respond.  Someone usually responds quickly even if it is just a bump.  I have i8kmon installed and working on my E1505 but it is not with GKrellM.  Do a search of the site for i8kmon.  It has a daemon to run and config the temps with.  Because it was written for dual fans it took some playing with the temp overlap to get it to work.  There was a very good HOWto that I followed but I lost the link.  Hope this helps.:)

---

### Post by Paul S on 2007-07-30
Why do you say fans (plural).  My E1505 has only 1 fan.  I don't think you have more than 1 fan either.  My fan has worked fine without i8k.  I use gkrellm to view my cpu temp and it's always less than 60 C (right now just 48.0C).  I have the nvidia 7300 video and it's temperature (also on gkrellm) is only 55.0C right now.  And the fan comes on and off and runs fine without i8k.

What temperature do you see?  Maybe you should contact Dell if you think it's not working.

regards,

---

### Post by NilsE on 2007-07-30
> **Paul S said:**
> Why do you say fans (plural).  My E1505 has only 1 fan.  I don't think you have more than 1 fan either.  My fan has worked fine without i8k.  I use gkrellm to view my cpu temp and it's always less than 60 C (right now just 48.0C).  I have the nvidia 7300 video and it's temperature (also on gkrellm) is only 55.0C right now.  And the fan comes on and off and runs fine without i8k.

What temperature do you see?  Maybe you should contact Dell if you think it's not working.

regards,
Some Dell systems have two fans (typically CPU and drive bay) but most laptops have only one fan.  In i8kmon it is fan 2 by the way. 

My laptop would get up to 60 C and believe me at that temp with it sitting in your lap it can be awful uncomfortable.  I use i8kutil to keep it down in the upper 20's/lower 30's and it is much more comfortable.  Plus I have to believe lower temps are better for the parts.

---

### Post by rscheckler on 2007-08-02
Yes, my E1505 does only have 1 fan. That was a mistake when I was typing this post out at work. I agree with you NilsE....I want my laptop to run alot cooler than most because the heat isnt good for the parts. Right now I am still looking at tweaking i8k to work with the single fan...but so far I havent had much luck. If anyone sees anything please let me know.

---

### Post by ianmac on 2007-08-02
The heat will do the most damage to the battery, so yes...  cooler is better :)

Ian

---

### Post by Papi-KB7VGW on 2007-08-02
Here is what my /etc/i8kmon look like and it seems to keep my notebook in the low 40's.  The low speed comes on at 40 and goes off at 30 which never really happens.  High speed is 50 down to 38.  The last 2 columns are for battery mode and I have messed with them yet.

set config(0)   {{- 0}  -1  40  -1  40}
set config(1)   {{- 1}  30  50  45  55}
set config(2)   {{- 2}  38  57  50  60}
set config(3)   {{- 2}  50 128  50 128}

---

