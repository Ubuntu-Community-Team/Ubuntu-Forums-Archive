---
title: "Ununtu Dapper v6.0.6.1 And memory Problems"
date: 2006-08-29
forum: Desktop Environments
---

### Post by dragonfixed on 2006-08-29
Hi this is dragonfixed i am new to linux some what. I have several problems with my build of ubuntu v6.0.6.1. 

1st: Xorg memory leak
2nd: Kde problems
3rd: swift fox memory problems

Here is my specs on the machine i am running deblin dapper on

dual p3 600Mhz 512meg ram updated to 80 gig westerndigital eide hard drive.  and a nvidia gforce 2 mx 32 meg of ram

My swap pertition is 3 gig

I am running kbuntu v3.5.2 and want to update to v3.5.4 

Kernel that i am running is 2.6.15-26.686 smp with the restricted modules for that kernel


Here is my problems listed out.

When i boot into the gui and get a kde login screen. i open up a command line terminal. and type in top

then i switch back to the gui and login.

then i go about what i want to do. i usually load a session of swiftfox. after about 30 min i see that the swiftfox become unresponsive. i check on the top program and notice that xorg is taking up 100 meg of my ram. i have to wait untill it coms down before i can do any thing. if i keep swiftfox running the xorg starts to consume a whole lot of my ram. it has consumed at least 600 meg of my main ram.  if i keep swiftfox running it also consumes at leats 150 meg of my main ram. if i close swiftfox down xorg dose not release the ram i have to sometime force kill the xorg process. I am getting verry tired of memory leaks and consumption that xorg dose and swiftfox. Is there any tweaks or commands or apt-get updates that i can do to make this problem go away. 


to reply to this message use [email]idealso00@gmail.com[/email]

---

### Post by rmjokers on 2006-08-29
Have you tried logging in and NOT using swiftfox for a while?  It is possible that the application itself is causing the memory leak.

---

### Post by dragonfixed on 2006-08-29
I have tried this and xorg still leaks memory 

> **rmjokers said:**
> Have you tried logging in and NOT using swiftfox for a while?  It is possible that the application itself is causing the memory leak.

---

