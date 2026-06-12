---
title: "htop shows 100% CPU usage, summing up processes shows 33%"
date: 2009-06-19
forum: Desktop Environments
---

### Post by laket on 2009-06-19
I really am at the end of my wisdom..
My CPU is running at 100%, when I have a look at htop, the processes sum up to 33% only (screen-shot attached). How can it be?
Well, I have no idea how to find out who is responsible for eating it all up :(

Now, when did it happen:
We have in Gnome: "System -> Preferences -> Sessions Preferences -> Options"
there you can activate: "Automatically remember running applications when logging out"
well, I did activate it just for "fun" to remember what I was working on at work. well, the next morning when I started the machine it began running at 100%. what I did was deactivate the above option and restart my session - no change in cpu usage; restarted the machine still no change :(

I used this option to remeber 3 shell windows and Firefox.

now my cpu and load is high up.

any ideas?

My machine is:
Ubuntu 9.04
kernel 2.6.28-13-generic
Gnome 2.26.1
RAM 1GB
Proc AMD Sempron 3000+

---

### Post by XubuRoxMySox on 2009-06-19
You likely have compiz and other "eye candy" effects going by default. 

Gnome and KDE are both resource hogs in my opinion... I never even approach full CPU or RAM usage, and applications load instantly and run faster simply by choosing a much more lightweight desktop environment called [LXDE]("http://lxde.org").

It's available through Synaptic. Or open a terminal and type
```
apt-get install lxde
```

Log out, and when you log back in just choose LXDE as your Session.

Drive it around and kick the tires a bit. It's pretty, friendly, and extreeeeemely lightweight. Applications appear in */usr/share/applications* and can be either dragged-and-dropped to your desktop or placed in the panel on the bottom.

Your favorite wallpapers can be moved to *usr/share.lxde/wallpapers* to customize it further.

If you like LXDE as much as I do, you can make it your default session. But **I guarantee that your CPU usage (and RAM use) will plummet** dramatically!

-Robin

---

### Post by laket on 2009-06-19
Gnome and KDE are both resource hogs in my opinion... I never even approach full CPU or RAM usage, and applications load instantly and run faster simply by choosing a much more lightweight desktop environment called [LXDE]("http://lxde.org").

-Robin[/QUOTE]

Running off to another desktop environment, might help but is not a solution to the problem itself. thanks anyway, i might explore lxde on my notebook.
everyone knows that gnome and kde need more resources, but i work on gnome for years and i didn't have this problem before. I am using the same machine (without any hardware upgrade) since ubuntu 7.10!

now just logging in on my gnome, it wows up to 100% CPU and load average is at 4.5!

---

### Post by cariboo on 2009-06-19
Instead of using htop, use top to see what apps are using all the cpu resources. I noticed in the second screenshot you have a zombie running, can you get rid of it to see if that makes a difference?

---

### Post by laket on 2009-06-19
as far as I know htop and top are the same prog, just that htop uses colors and the F keys... well, i tried in the first place top and then htop to see if there were any changes, but looks exactly the same! same processes same consumption of cpu, the biggest is X with upto 14% the rest is 1% to 2% so summing up u have something like 33%

the zombie shows up and vanishes rapidly takes about 1 second!

---

### Post by XubuRoxMySox on 2009-06-19
> **laket said:**
> 

Running off to another desktop environment, might help but is not a solution to the problem itself. thanks anyway, i might explore lxde on my notebook.



**You are right**, of course. The most recent update may help you, because I know they've been working on that. Part of the "problem" is that the kernel tends to operate in RAM first if it's available and resort to swap only if it has to. It makes the whole experience speedier, so arguably it isn't really a problem at all. Except that many people have reported high temperatures and such, so the developers have been working on a fix.

The simplest thing to try first is a system update. The last one I did required a restart because the kernel itself has been upgraded.

Beyond that I'm rather a newbie to Linux myself, but in the four months since I started seriously exploring, I discovered how much faster my old dinosaur ran on LXDE and became somewhat of a fanboy. 

It's a workaround, I guess, if all else fails.

-Robin

---

### Post by davidsands on 2009-08-06
I've been having exactly the same problem (htop shows 100% CPU while the sum of processes is much less.) I, too, not long ago, tried the option to reload running applications in gnome-session-manager, so that may what triggers the problem. Logging into Gnome as a different user works fine, and logging into KDE as the "myself" also shows normal CPU numbers. Oddly, when htop first showed CPU at 100%, I was checking something else (the system seemed to running normally.) I'll look into it further, but in the meantime I can just map what I need into a proxy user's workspace, or strange it in a strange land with KDE.

---

### Post by davidsands on 2009-08-07
**Surprise!**

Logged in as the "htop 100%" user, I noticed that vino-server in htop was intermittently active even though it wasn't in use per se. So I disabled remote desktop access to my machine in Preferences > Remote Desktop, and the htop reading fell back to the normal range (3% - 15% or so on my machine in idle).

In trying to track down the effects of checking "automatically remember running applications when logging out" in Preferences < Startup Applications, I created a couple of new users, only one of which had the option checked. Enabling remote access on this new account didn't send CPU usage to 100%. But in testing, I discovered that both of my accounts which had sessions restored at startup would not start properly if loaded as a *second* Gnome session (via the User menu). These accounts would go about as far as loading the panels and then present a white screen with no cursor. 

I'll have to become more familiar with Gnome session management to see if I can come up with some explanation or work-around as to this peculiar behavior of restoring Gnome sessions. I'll also be checking out Karmic to see if things are still as fragile.

---

### Post by laket on 2009-08-07
davidsands,
nice tryouts! I haven't searched more since I haven't found any answers on the web, even though I search for more than a month. Since I needed my machine back on track I ended up reinstalling the system...

---

### Post by Morty007 on 2009-08-07
Can anyone tell me how to log out of lxde and log back in with gnome? I followed the advice here and want gnome back. Thanks.

---

### Post by Morty007 on 2009-08-07
Nevermind, I figured it out.

---

### Post by jzwolak on 2009-09-08
compiz.real should show up in the %CPU just like other processes.  This isn't the case, therefore, compiz.real and other eye candy are not the CPU hog here.

---

### Post by KiwiBuntu on 2009-10-05
Had exactly the same problem - shut down remote desktop and immediately sorted :-/

---

