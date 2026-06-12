---
title: "XPS 420, New to Ubunto and lots of problems"
date: 2008-12-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Lengthy on 2008-12-07
So I installed ubuntu and vista on the same hard drive and I have been having a good number of errors trying to get everything working.

I followed the instructions that were printed here to install and set up the partions. On the ext3 part of the partion I made that partion 24gigs instead of 8. It says it has to be at least 4 but twice that is best and any more if possible. The first install I ran had the same problems I am having but when I reinstalled it the ext3 parition had all but 500mb being used. So I doubled the space thinking that could be the problem.

Onto the errors:

First error I get when booting up is a few different GRUB errors. The first one I usually get is GRUB error 5. I have to restart my system a few times before it will move the next error, which is error 18. Again I have to restart the system a few times and then I will usually get error 21.

I looked on the grub error page about the errors and the things that say that would be affecting it dont apply. This is a brand new machine, maybe 2 months old. I have the hard drive that came with it which is a 320gig HD. and an external HD. I haven't installed on the HD and removed it, or done any of the things that might be leading to the problem.

Once I restart the machine 10-15 times I will finally get the boot menu and then can get it started up. I have no experience with ubuntu and dont know how to do a lot of the things so I am working on learning as I go.

The only problem I have ran into so far once in ubuntu is that when I start firefox I get an error saying someting to the effect of "could not initialize application security. This may be do to a read/write only in start up. The application may not work as intended" This is from memory so not an exact error message. I do not get any error codes with it, just the message. When I press okay Firefox boots up and sometimes it will work for a little while then freeze, or it wont react at all. When it's not reacting I can move the window around, resize it, type in the window, but it doesnt search or connect to anything. The other times it boots up when I try to move it, it will just crash.

Oh, one more problem. When I try to do something in the terminal, like one of the comands saus to type "sudo fdisck-lu" it will ask me for my computer password. It doesnt let me type any thing into this space. The only key that works is the enter key. I can click enter and then type for a few seconds on a new line, but then it says incorrect password.

Any and all help would be super appreicated. I am going to give it a few more days and then just uninstall Ubuntu.

---

### Post by 2hot6ft2 on 2008-12-07
> **Lengthy said:**
> 
Oh, one more problem. When I try to do something in the terminal, like one of the comands saus to type "sudo fdisck-lu" it will ask me for my computer password. It doesnt let me type any thing into this space. The only key that works is the enter key. I can click enter and then type for a few seconds on a new line, but then it says incorrect password.

For this part when asked for your password in terminal you just type it in and hit enter. Nothing will be shown while doing this. It's a safety feature.

---

### Post by Lengthy on 2008-12-07
Thank you very much. I thought it may be something like this, or some user error but wasn't sure.

---

### Post by andreasis on 2008-12-08
NOT to be rude or mean, but if you are willing to consider Vista over Ubuntu, then Linux is NOT for you.  I would encourage you to go back to Vista... it is new and shiny, and will do everything for you.

---

### Post by Gausian on 2008-12-08
Not so fast andreasis, everyone has different computing needs and should be able to choose for themselves.  Having someone else choose for them, is exactly what this community wants to avoid.


Anyway, Lengthy, how did you partition your disc?  did you use gparted or vistas built in tool?

---

### Post by andreasis on 2008-12-08
; )

---

### Post by Lengthy on 2008-12-08
> **andreasis said:**
> NOT to be rude or mean, but if you are willing to consider Vista over Ubuntu, then Linux is NOT for you.  I would encourage you to go back to Vista... it is new and shiny, and will do everything for you.
First off, when you start any sentence off "not to be rude, not to be racist, not to be a ******* PRICK" then you're going to end up sounding like that.

For the record, I am a professional poker player and all poker software that I have to use, requires windows.  I am pretty paranoid about getting viruses on my machine and I would really like to start learning more about computers, operating systems and the works.

---

### Post by Lengthy on 2008-12-08
> **Gausian said:**
> Not so fast andreasis, everyone has different computing needs and should be able to choose for themselves.  Having someone else choose for them, is exactly what this community wants to avoid.


Anyway, Lengthy, how did you partition your disc?  did you use gparted or vistas built in tool?

I think it would be gparted. I used the partion tool built into the installer.

---

