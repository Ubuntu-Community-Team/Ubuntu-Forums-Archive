---
title: "ubuntu 6 is slow"
date: 2006-10-22
forum: Desktop Environments
---

### Post by mfaridi on 2006-10-22
I install ubuntu 6  two month ago and go to to trip 
after I came back I feel my ubuntu is so slow
It take alot of time for run
when ubuntu want go to gnome it take along time 
I have to wait 5 min and after 5 minute I can use gnome
If I want open terminal it take 2 minute
after two minute I can use terminal

for open mc I have to wait for three minute after 3 minue I can use mc

what happen for my ubuntu 

my ubuntu is so slow 

I have 1GB of physical ram
I have 2GB swap
my CPU is Athlone XP 2400+
my mainboard is ASUS A7N8X-E Deluxe

please help me my ubuntu is so slow

it was good and fast but after two month it is so slow

so sorry my english is very bad](*,)

---

### Post by WalmartSniperLX on 2006-10-22
Since I am using KDE instead of Gnome at this momment, I cannt relate completely, however I have used Gnome before. 

Ide say just wait a few days and Edgy Eft (the next release of Ubuntu) is released. It has the latest version to Gnome and I read that it will fix the slowness problems, which are common for some users. :D

---

### Post by studiesrule on 2006-10-22
Ok, I really can't tell why in the world you'd have a slow machine with that much ram. I seriously don't think you need that much swap either, so you can cut it down to 512 or something next install you make.
I think you should start up and load the process manager. And sit around and check at what's sapping up your memory. Perhaps you have a runaway process. Then note down that process, and kill it. 

Now, open up a terminal and type: rc-list, and : sudo rc-update del <process> default. This will remove that process from all the runlevels.

If this doesn't work, you'll have to go to /etc/rc.d/ Now list the files using :ls. Enter each runlevel (./rc<number>.d) and locate the script/process that's causing the trouble, and delete it. Remember to make backups everywhere

---

### Post by az on 2006-10-22
> **studiesrule said:**
> 
Now, open up a terminal and type: rc-list, and : sudo rc-update del <process> default. This will remove that process from all the runlevels.

If this doesn't work, you'll have to go to /etc/rc.d/ Now list the files using :ls. Enter each runlevel (./rc<number>.d) and locate the script/process that's causing the trouble, and delete it. Remember to make backups everywhere

While I agree that something is wrong and that there may be a process that is taking up all the cpu power, don't do that.  It depends what the problem is.  Don't just rip things out like that.

Open a terminal and run 
top

and see what process is using so much cpu power.  Post the name of the porcess here.

---

### Post by studiesrule on 2006-10-22
I recommend you do what azz says, As you can see, I'm a noob, and I don't know much. Thanks for the info though azz, I've just learnt something new.

---

