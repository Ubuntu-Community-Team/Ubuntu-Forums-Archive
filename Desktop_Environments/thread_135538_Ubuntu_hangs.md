---
title: "Ubuntu hangs"
date: 2006-02-24
forum: Desktop Environments
---

### Post by uthra on 2006-02-24
Hi All,

I recently installed Ubuntu 5.10 on my laptop. What I noticed is that whenever I launch any application, the mouse cursor throttles (hangs) for a second and then comes back to normal free movement. This happens everytime the system is busy doing something. This is really frustrating. I have a PIII with 256mb RAM and 512 mb swap space. Is this a known issue or is there a remedy for this?

---

### Post by andrewsawyer on 2006-02-24
You might try having a look at System Monitor and seeing if anything is maxing out your resources.  It might shed some light on the situation.

---

### Post by uthra on 2006-02-24
I tried to check with the system monitor. I found nothing unusual, except the Xorg process goes to upto 20% of cpu util. I tried with both dapper and breezy and still i'm facing the same issue. I just wanted to give a try for ubuntu so that I can throw off my windows os. I very much pleased with the look and feel of ubuntu but this one issue is really making me frustrated. we are planning for a mass migration to ubuntu. pls help us in resolving the same

---

### Post by andrewsawyer on 2006-02-24
I'm afraid I really don't know then.  Fingers crossed there is someone else in the forum that might be able to help.

---

### Post by manicka on 2006-02-24
I had a problem like this with a SuSE system some years ago. From memory it turned out to be a faulty network card that was causing the problem, although yours sounds more like it may be something to do with your video card.

Some suggestions
If you have spare cards lying around try them to see if they make a difference.
Reconfigure X by running this command in a terminal as you may not have it configured properly
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by uthra on 2006-02-24
tried reconfiguring with dpkg-reconfigure, but still facing the same issue.....every now and then my mouse refuses to move for a second and then comes back online. i think some process raises to a high priority which prevents the smooth movement of my mouse. though i say it's the mouse, it hangs the entire gui for a second, i.e even window refresh update will not take place for that second.....do you get any clue?

---

### Post by newuser111 on 2006-02-24
try sudo dpkg-reconfigure xserver-common

and it will ask you what xorg nice value you want to use, 0 is supposed to be default, try 10 or -10, im not sure which will help your problem but 19 is the highest and -19 is the lowest, nice being the cpu priority level

---

### Post by uthra on 2006-02-25
even setting the new nice value didn't help....i hv installed fedora core 4 in the same laptop and that works really fine.....don't know where the issue lies...think i've give up with ubuntu and go with fc4

---

