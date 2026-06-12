---
title: "Vmware: Diablo runs too fast!"
date: 2005-12-29
forum: Desktop Environments
---

### Post by anil_robo on 2005-12-29
I recently installed vmware workstation, and then created a virtual machine for windows xp and installed xp on it. All this because I want to dump windows forever only if I can make diabloII: LOrd of DEstruction work on it. I did make it work, but somehow the **game runs too fast**! The character runs so fast that it's uncontrollable! QUite laughable actually!

To test the problem, I logged on to battle.net (on vmware windows) and started a game. Someone else (using real windows diablo) joined my game, and I had a racing contest with him. On my screen, I was able to outrun him (because my game was too fast) but every few seconds the game appeared to detect that my framerate is very fast, and it put me back to the **appropriate place** on the map.

Does it have something to do with screen refresh rate? Win XP installed in vmware shows a screen refresh rate of 85Hz, and doesn't give me any other options to choose from. In Ubuntu, I have a refresh rate of 60Hz. Does this result in the increased speed I am getting in Diablo?

---

### Post by anil_robo on 2005-12-29
Anyone? :(

---

### Post by anil_robo on 2006-01-03
Bump! [IMG]http://img144.echo.cx/img144/4774/sc1027qc.gif[/IMG]

---

### Post by Sudokan on 2006-01-05
Hello, sorry I can't help with your vmware problem, but just out of curiosity, why don't you just run Diablo II and LOD with WINE; it's the way I play it and it doesn't require Windows to make it work...just curious...

Sudokan

[I]A bus station is where a bus stops.  A train station is where a train stops.
On my desk I have a work station...[/I]

---

### Post by Mr_J_ on 2006-01-05
Although I can't really help but your refresh rate of your monitor will have no influence on your framerates on your game.
Since you have Vmware workstation you might have the possibility to make the Vmware processor slower as a work around.

---

### Post by anil_robo on 2006-01-05
[quote=Sudokan]Hello, sorry I can't help with your vmware problem, but just out of curiosity, why don't you just run Diablo II and LOD with WINE; it's the way I play it and it doesn't require Windows to make it work...just curious...[/quote]
 
I tried running diablo with WINE. Failed many times. Installing Diablo takes about half an hour, and I swear I've wasted dozens of such half-hours trying to make the game work. Whever I run Diablo with wine, it gives out a lot of errors regarding my 3d support. In fact, the video setup utility with Diablo says "you do not have a graphic card - you cannot run diablo"! :(
 
So as an alternative, I installed entire XP under vmware and tried diablo from there. It runs, and connects to battle.net, but it's too fast. :(

---

### Post by anil_robo on 2006-01-05
[quote=Mr_J_]Although I can't really help but your refresh rate of your monitor will have no influence on your framerates on your game.
Since you have Vmware workstation you might have the possibility to make the Vmware processor slower as a work around.[/quote]
 
Hey that's a brilliant idea! I'll give it a try once I reach home! I have run diablo on a lowly 233 MHz processor and the single player games run kinda-ok (it's just that you have to wait for a long long time for the game to load). But multiplayer games (that's what I'm looking forward to) sync the refresh rate to the actual time elapsed. So if the game creeps slowly for some time, the game tries to match it up by increasing the game speed tremendously for a short time. That's what killed my hardcore character! :(

---

### Post by Cannedbread on 2006-01-11
this may be caused by a problem with your kernel timer interupts

does the windows clock run too fast? 

i am having a problem with my windows clock running much slower than realtime, this is caused by something to do with the kernel timer interupt thing. I dont know what you can do about it, as ubuntu is not an officially supported host OS.

[http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=1420](http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=1420)

this link sort of applies ^

[http://www.google.com/url?sa=t&ct=res&cd=3&url=http%3A//www.vmware.com/pdf/vmware_timekeeping.pdf&ei=EqzEQ_mjIMOsigG3i8DQDg&sig2=f3cMjeyBA8l89g5TFZZffg](http://www.google.com/url?sa=t&ct=res&cd=3&url=http%3A//www.vmware.com/pdf/vmware_timekeeping.pdf&ei=EqzEQ_mjIMOsigG3i8DQDg&sig2=f3cMjeyBA8l89g5TFZZffg)

This link is a huge pdf about virtual machine timing. ^ 

hopefully this helps somehow.

-cameron

---

### Post by zoiks on 2006-01-11
It's possible that installing the vmware tools within xp virtual machine will solve your problem.  While the vm is running, it's an option in vmware itself, like Tools|Install VMWare Tools or some such.  This really should be done anyway, as it makes your xp installation cooperate much better with vmware.

---

### Post by anil_robo on 2006-01-12
[quote=zoiks]It's possible that installing the vmware tools within xp virtual machine will solve your problem.  While the vm is running, it's an option in vmware itself, like Tools|Install VMWare Tools or some such.  This really should be done anyway, as it makes your xp installation cooperate much better with vmware.[/quote]

Thanks for the suggestion, Zoiks. I have VMWare tools installed in XP, but still Diablo runs too fast. In fact, I checked windows clock, and it took twelve seconds of time to advance the clock  by one second!

It means VMware windows has some clocking problems! :(

---

### Post by anil_robo on 2006-01-13
[quote=Cannedbread]this may be caused by a problem with your kernel timer interupts

does the windows clock run too fast? 

i am having a problem with my windows clock running much slower than realtime, this is caused by something to do with the kernel timer interupt thing. I dont know what you can do about it, as ubuntu is not an officially supported host OS.

[http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=1420]("http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=1420")

this link sort of applies ^

[http://www.google.com/url?sa=t&ct=res&cd=3&url=http%3A//www.vmware.com/pdf/vmware_timekeeping.pdf&ei=EqzEQ_mjIMOsigG3i8DQDg&sig2=f3cMjeyBA8l89g5TFZZffg]("http://www.google.com/url?sa=t&ct=res&cd=3&url=http%3A//www.vmware.com/pdf/vmware_timekeeping.pdf&ei=EqzEQ_mjIMOsigG3i8DQDg&sig2=f3cMjeyBA8l89g5TFZZffg")

This link is a huge pdf about virtual machine timing. ^ 

hopefully this helps somehow.

-cameron[/quote]

Thanks Cameron, I had a look at both documents. Apparently they look too much for a "newbie" like me. I had dared to play around with Ubuntu settings in the past because I had lot of time to repair if something went wrong. But I'm hardpressed with time these days, so I may try these tricks sometime later. I have no time to play diablo anyway! ;) Thanks once again and have a great day! :)

---

### Post by Cannedbread on 2006-01-16
well its all pretty much over my head too. but i have compiled a few ubuntu kernels. the gist of the docs is that your kernel interupt rate thing should be set to 1000hz instead of 100hz in order for your VMS to work right, but all 2.6 kernels have that rate by default so i dont know wtf is going on.

---

### Post by Cannedbread on 2006-01-19
Ok so i fixed my problem, it may help you but i dont know.

heres what i did.

create a shell script containing this:
```
#!/bin/bash
echo 1 > /sys/module/processor/parameters/max_cstate
vmplayer
echo 8 > /sys/module/processor/parameters/max_cstate
```

now instead of running vmplayer directly, you run this script which runs vmware for you. i modified my vmware icons to point to it. you may have to run it with sudo.

---

### Post by anil_robo on 2006-02-28
Guess what??

I ran vmware player after almost a month, played diablo, and the problem has been solved automatically! I dont' know how, why?? I didn't do a thing.

Maybe it was some update that fixed it??? I'll come to know when I use vmware in Dapper!!

Thanks everyone!! Thanks a zillions for your support.

---

### Post by citybird on 2008-02-29
I am having the same problem.

sometimes i can correct the issue by restarting the windows vm untill it runs correctly.
With windows 2000 the problem went away after just one restart.
i upgraded to xp and now the problem wont go away so easy.

after I get a restart where the vm and the game runs at the correct speed i dont shut down the game since it's easier to leave it running than to try to fix it again.

I'll let you know if I find something else out.

---

### Post by citybird on 2008-02-29
it's not just diablo. if i open the calendar and look at the clock it takes 20 seconds for the second hand to move across 30 seconds.

What's up with that. Out of 3 vmware installes i get one that runs too fast and the other 2 work fine ...

---

### Post by citybird on 2008-02-29
found a nice solution here:

[http://blog.autoedification.com/2006/11/vmware-guest-clock-runs-fast.html](http://blog.autoedification.com/2006/11/vmware-guest-clock-runs-fast.html)

basically you find your cpu freq:
```

$ cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq 
1833000

```
then you add some lines to your vmware config file:
```

$sudo su
$nano /etc/vmware/config

host.cpukHz = 1830000
host.noTSC = TRUE
ptsc.noTSC = TRUE

```
I added the lines at the end and it slowed the clock right down.

then you start the gust windows os and click the vmware tools icon in the task bar and check the time synchronization checkbox under the options tab.

---

