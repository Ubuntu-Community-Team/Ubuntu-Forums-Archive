---
title: "Why is my CPU working so hard?"
date: 2006-07-01
forum: Desktop Environments
---

### Post by KeithO on 2006-07-01
I did a fresh install of Kubunutu Dapper 2 days ago.  I am running a AMD 1900+ w/ 512 ram and dual hd's (40gig and 250gig).  Whenever I have something run that requires any amount of CPU power, it seems to take atleast 70% of my cpu load and hold on to it for several seconds while I still have about 300megs of RAM available.  What can I do to reduce this load?

---

### Post by chalex on 2006-07-01
You could stop running programs :) 

What makes you think that something is wrong?

---

### Post by KeithO on 2006-07-01
:D thanks.

nah, it doesn't matter how many programs i have running.  i typically only have Firefox running, sometimes a music player but thats it.  its like i'm opening up adobe illustrater on xp, its that painful.

---

### Post by greyhat on 2006-07-01
I would suggest running a command like 'top' in a console window while doing some of these "cpu intensive" operations, and seeing what process is using what, that might at least give you a basis to ask some more questions.  :)

---

### Post by KeithO on 2006-07-02
[QUOTE=greyhat]I would suggest running a command like 'top' in a console window while doing some of these "cpu intensive" operations, and seeing what process is using what, that might at least give you a basis to ask some more questions.  :)[/QUOTE]
i was unaware of this utility.  very swank.  right now with just firefox and konsole running, Xorg is fluctuating between 5 and 10% occasionally jumping to 25+%.

---

### Post by hoodwink on 2006-07-02
[QUOTE=KeithO]i was unaware of this utility.  very swank.  right now with just firefox and konsole running, Xorg is fluctuating between 5 and 10% occasionally jumping to 25+%.[/QUOTE]
Fairly normal on a lower end CPU, and 25% is not really working hard.

---

### Post by KeithO on 2006-07-02
are there any services i can shut down or ways to make kde a bit snappier or should i go back to gnome?

---

### Post by dpaint4 on 2006-07-02
I think you'd experience the same thing in KDE or Gnome. I have always experienced high CPU useage when running Ubuntu. More than other distros.

At first I wondered why my laptop's fan was running at high all the time, but then I noticed that if I shut down practically everything I'm doing and wait a moment, the fan slows down. So I have faith the system is running properly.

Look at it this way, XP's CPU useage was lower in general, but that OS was often completely unresponsive and glitchy. At least Ubuntu does things when you tell it to and when you click, in general, something happens.

I see the higher CPU useage as the price of a responsive OS. At work, my Mac G5 running OS 10.3.9 is also responsive and heavy on the CPU.

---

### Post by jchau on 2006-07-02
I have the same problem (Xorg appears to eat CPU resourses).  It's a real pain for me since I'm running Dapper on my laptop and powernowd keeps shooting my CPU to top speeds (not sure if powenowd is useful anymore... it is always at the max speed).  

I never had this problem before in Breezy.  It would normally stay at the minimum speed unless I'm loading a program, running a compiler, etc...

Now, it shoots to top speeds even when I just have X running (a a few other background processes which don't use the CPU significantly) without any other processor intense applications. 

I'm considering a clean reinstall, but that will be a pain (and I don't want to have to reinstall everytime I update the distro).

---

### Post by KeithO on 2006-07-02
good points.  thanks.

---

### Post by ozorba on 2006-07-02
Have you tried 

man powerd

This one sets up the conditons on how the processor should run. 

sudo gedit /etc/default/powernowd

Enter the following into the file

OPTIONS="-q -m 2 -u 80 -l 25"

the sudo /etc/init.d/powernowd restart

This will gradully ramp up the processor speed and after the loading immediately return to the lowest speed.

---

OZ

---

### Post by jchau on 2006-07-02
[QUOTE=ozorba]Have you tried 

man powerd

This one sets up the conditons on how the processor should run. 

sudo gedit /etc/default/powernowd

Enter the following into the file

OPTIONS="-q -m 2 -u 80 -l 25"

the sudo /etc/init.d/powernowd restart

This will gradully ramp up the processor speed and after the loading immediately return to the lowest speed.

---

OZ[/QUOTE]


Well, I'm using aggressive mode right now, but I'm not sure that changing the options will help much (without significantly killing performance).  For one thing, the processor usage is almost always > 33%, shoots to 100% every few seconds, and normally stays around 60%, shooting over 80% too often.  If I place it in passive mode, raise the upper limit, and raise the lower limit, I'll forcing the processor to remain at the lowest speed (since my processor usage fluctuates, and X seems to eat any available processing power).  

The problem is the increased processor usage, not powernowd.  I don't quite understand what changed in my X (Gnome) to cause it to become such a resource hog.

---

### Post by jchau on 2006-09-30
Ubuntu doesn't seem to guzzle processing power anymore.  I wonder what changed.

---

### Post by lawina on 2006-09-30
Thats Funny, 
For me only system monitor consumes something like 5-20% cpu. 
Everthing else is 0%.

---

### Post by jchau on 2006-09-30
> **lawina said:**
> Thats Funny, 
For me only system monitor consumes something like 5-20% cpu. 
Everthing else is 0%.

Well, I have SpeedStep enabled with powernowd.  It used to shoot to the maximum speed. Always (even if the computer isn't showing the Gnome system monitor).  Now, even with 3 desktops full of apps running, it will only shoot up for about a second when it needs to (eg. loading new app, testing password strength, etc.).  

Guess the Ubuntu fairies must have come and fixed my computer when I wasn't around; I'll have to remember to logout next time :-P :wink: .

---

