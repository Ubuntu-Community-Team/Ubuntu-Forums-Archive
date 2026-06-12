---
title: "Ubuntu 9.04 cpu usage question"
date: 2009-04-14
forum: General Help
---

### Post by terranova on 2009-04-14
I have a E5200 @ 3.6ghz and for some reason both cores are at a constant 65%+ usage even while idle. Is there something that can be done about that? Just curious because in system monitor it shows that none of the processes running are using any of my CPU, I'm just a beginner still trying to get the hang of it all. Thank you!

---

### Post by Alekz_ on 2009-04-14
Hi terranova!

You may be able to see which process are using CPU by typing the command **top** on your terminal!

I just don't like system monitor... :/ I prefer to use the old black screen! :)

[]'s

Alekz_

---

### Post by terranova on 2009-04-14
ok I did that but the most cpu% usage is 15%.. What could be going on in the background, I installed compiz not sure if that would have any affect on it or not.

---

### Post by Alekz_ on 2009-04-14
I'm sure that compiz can use some CPU, but not 65%!!

You see one process using 15%... But the 65% is about the sum of all process running!

I'm used to run sar commando for a while to abserve my CPU usage like this:

Type the following command on a terminal:
sar 3 50

and wait until it finish (takes a while..)

PS: You saw the CPU usage in 65% for how long?

Oh! Almost forgot... I'm almost sure that sar command isn't native on Ubuntu!

[]'s

Alekz_

---

### Post by terranova on 2009-04-15
> **Alekz_ said:**
> I'm sure that compiz can use some CPU, but not 65%!!

You see one process using 15%... But the 65% is about the sum of all process running!

I'm used to run sar commando for a while to abserve my CPU usage like this:

Type the following command on a terminal:
sar 3 50

and wait until it finish (takes a while..)

PS: You saw the CPU usage in 65% for how long?

Oh! Almost forgot... I'm almost sure that sar command isn't native on Ubuntu!

[]'s

Alekz_

It stays at 65%+ 100% of the time. I'll try using that command and see what happens. Thanks!

---

### Post by terranova on 2009-04-15
Here is a screen-shot of top in terminal along with everything I have running.

---

### Post by Copernicus1234 on 2009-04-15
> **Alekz_ said:**
> 
Oh! Almost forgot... I'm almost sure that sar command isn't native on Ubuntu!


Yes it is, works fine here and I havent installed it. Didnt even know it existed. Nice program! ;)

---

### Post by DeMus on 2009-04-15
> **terranova said:**
> I have a E5200 @ 3.6ghz and for some reason both cores are at a constant 65%+ usage even while idle. Is there something that can be done about that? Just curious because in system monitor it shows that none of the processes running are using any of my CPU, I'm just a beginner still trying to get the hang of it all. Thank you!

When using System Monitor, did you also show all processes? Not just yours.
In System Monitor go to menu View and choose All Processes.
Maybe there is a machine proces which uses a lot of CPU power.

---

### Post by terranova on 2009-04-15
> **Copernicus1234 said:**
> Yes it is, works fine here and I havent installed it. Didnt even know it existed. Nice program! ;)

It doesn't work for me :(

---

### Post by terranova on 2009-04-15
> **DeMus said:**
> When using System Monitor, did you also show all processes? Not just yours.
In System Monitor go to menu View and choose All Processes.
Maybe there is a machine proces which uses a lot of CPU power.

Yes all processes is on.

---

### Post by Alekz_ on 2009-04-15
Well.. AS your attachment show us, your load avarage is about 3.5%! It's pretty normal...

You're probably using a lot of compiz efects, am I right? It really use lot of CPU!

If you wanna to be sure, replace compiz with metacity and observe you CPU load! It should be really really smaller!

[]'s

Alekz_

---

### Post by dazzlindonna on 2009-04-21
I've got the exact same thing going on. Ever since I upgraded to jaunty yesterday, system monitor is showing around 65% cpu usage, but everything i look at (top, htop, etc), shows nothing near that.  I'm starting to think it's just a bug in system monitor with jaunty.

---

### Post by cubeist on 2009-04-21
I have the same issue, not as extreme, around 50% on one core all the time, nothing shows in system monitor, but xorg is always at, or near, the top in top.  This is not compiz doing this, something else... and not normal, usually cpu idles at 2-3% in ibex.

---

### Post by networm1230 on 2009-04-21
make shore that you look at your process and kill or end the process that you are not using but be careful when doing that. uninstall programs that you don't need and get red of packets that you are not using. doing this can help the cpu process more info

---

### Post by cubeist on 2009-04-21
> **networm1230 said:**
> make shore that you look at your process and kill or end the process that you are not using but be careful when doing that. uninstall programs that you don't need and get red of packets that you are not using. doing this can help the cpu process more info


The problem is that there is no process showing what is hogging the cpu!

---

### Post by TnTonly on 2009-04-24
That happen to me too :( My laptop is running at 15% in Ubuntu 8.10, but now 60%+ in both core in Ubuntu 9.04, and therefor very hot. 

Mine is AMD Turion 64 X2 with NVIDIA 7150M. May be the new Xorg that cause this?\

I've discover one more thing, my CPU is running well with Kubuntu, with less than 10% everytime

---

### Post by buvmuf on 2009-04-25
Odd. 
I just installed Ubuntu 9.04 on my desktop with a 1.6 Ghz dual core, and the gnome system monitor reported ~10-20% "background" CPU usage, most from Xorg. I ran "top" while the gnome system was still running, and top confirmed this. However, when I closed gnome system monitor, top reported that my CPU usage declined from ~10-20% to ~.5-1% usage. Maybe it's a glitch in the gnome system monitor?

---

### Post by TnTonly on 2009-04-25
> **buvmuf said:**
> Odd. 
I just installed Ubuntu 9.04 on my desktop with a 1.6 Ghz dual core, and the gnome system monitor reported ~10-20% "background" CPU usage, most from Xorg. I ran "top" while the gnome system was still running, and top confirmed this. However, when I closed gnome system monitor, top reported that my CPU usage declined from ~10-20% to ~.5-1% usage. Maybe it's a glitch in the gnome system monitor?

Not really, because GNOME System Monitor eats quite a lot of CPU usage. 
 
Your system seems to be normal. Of many system out there, only few have this bug.

I think I will report this as a bug. Hope there will be an update soon.

---

### Post by Steve H on 2009-04-25
I'm glad it's not just me that's getting the jaunty CPU hog probs. Mine seems to be running at 90 - 100% constantly. There doesn't seem to be any processes in either "top" or Sys monitor.

I'm getting sluggishness from the system as well, so I don't think it's just a reporting problem with sys mon.

EDIT: I've just found [this thread]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1435791.html") which has just made my cpu usage drop from 98% to 10% in sys mon, and from 72% to 1.3% in top. Seems to work for me, I set up my PC for remote desktop, must be something to do with the vino server.

---

### Post by TnTonly on 2009-04-25
> **Steve H said:**
> 

EDIT: I've just found [this thread]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1435791.html") which has just made my cpu usage drop from 98% to 10% in sys mon, and from 72% to 1.3% in top. Seems to work for me, I set up my PC for remote desktop, must be something to do with the vino server.

Thank you! You're a life saver. That works for me too. It took me a while to reconfigure my desktop, but the CPU usage is significant change! :popcorn:

---

### Post by JimmyVolatile on 2009-04-25
> **Steve H said:**
> I'm glad it's not just me that's getting the jaunty CPU hog probs. Mine seems to be running at 90 - 100% constantly. There doesn't seem to be any processes in either "top" or Sys monitor.

I'm getting sluggishness from the system as well, so I don't think it's just a reporting problem with sys mon.

EDIT: I've just found [this thread]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1435791.html") which has just made my cpu usage drop from 98% to 10% in sys mon, and from 72% to 1.3% in top. Seems to work for me, I set up my PC for remote desktop, must be something to do with the vino server.
How did you stop the vino server? Killing it in the System Monitor does nothing here. After a couple of seconds it's back up again.

---

### Post by Steve H on 2009-04-25
Preferences--> Remote Desktop --> turn off all the remote desktop services

i.e. don't allow anyone to connect etc

I think it is something to do with vino not signing in properly...

---

### Post by XavierGr on 2009-04-25
Thank you guys, that was my exact problem. Why does a remote desktop service has to utilize so much the CPU is beyond my grasp.
It would constantly utilize more than 30% from all 4 cores.

---

### Post by heggink on 2009-04-28
I had the same thing. Uninstalled vino and replaced with x11vnc. I can finally watch hd movies without distortion and the system performs so much better (even compared to intrepid).:guitar:

---

### Post by vbcranford@yahoo.com on 2009-04-29
I had the same problem on a DELL XPS M170 laptop. The CPU indication on the gnome System Monitor and top show 100%. BUT, neither the Monitor or top showed a runaway process!

Many thanks to whoever traced this problem to the Remote Desktop (vino-server?) Turning it off solved the problem. Now my concern is why top doesn't show the errant process!! For many years I have always depended on top to show EVERYTHING running on my computer (UNLIKE Windows task manager). The fact that the resources used by vino-server(?) don't show up in top/System Monitor probably indicates a problem between user programs like top/System Monitor and the kernel resource measurement/reporting services (I forget what it's called).

So thanks again. My laptop has cooled down sufficiently that I can touch the keyboard again after roasting at 100% CPU for a couple of days.

---

### Post by dyess002 on 2009-06-13
Guys my remote desktop is off and I am still having CPU problems.
I had the SBackup running the other day and it gave me a PID # and I was having this problem and started looking for the PID and it wasn't showing. so I know it doesn't show every process running and that scares my inards.
Right now I have 2 system moniters running side by side and oens is in the load is showing about 80% usage and the process is showing around 20%, so there is something amiss.
I think this is a high priorty bug that needs looking into.
I won't completly trust this system untill I know that it is reporting every process that is running..

---

