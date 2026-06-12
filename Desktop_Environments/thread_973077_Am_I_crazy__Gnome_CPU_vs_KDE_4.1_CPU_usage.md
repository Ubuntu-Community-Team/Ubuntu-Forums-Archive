---
title: "Am I crazy?  Gnome CPU vs KDE 4.1 CPU usage"
date: 2008-11-06
forum: Desktop Environments
---

### Post by zoomy942 on 2008-11-06
Call me nuts for this....

I have been using Ubuntu for a while, enjoying Gnome no sweat.  Well, last night i decide to drop Kubuntu 8.10 onto a thumbdrive with that USB LiveCD nifty utility and booted into it.  Yeah, its pretty, fine, but one thing i noticed but i didnt believe...

With Gnome/Ubuntu 8.10 my cpu (it's listed in my sig, 1.2 ULV dual core) my cpu danced from 7% or so to 25% and back down.  no big deal, i still get great battery life.  But in KDE, when I looked, it was sitting at 0% and 3% and thats it.

Is this something thats a known fact or was I just dreaming?  Was running it off the USB making it like this?  

What's the deal?

---

### Post by zoomy942 on 2008-11-06
Still doing testing...  this doesnt make sense

---

### Post by zoomy942 on 2008-11-06
No one has any info?

---

### Post by krazyd on 2008-11-06
try running 'top' in terminal on gnome and then on kde - should give you an idea of what's using all those cycles. 7-25% on idle is pretty bad. I can't compare though, as I'm using kubuntu :)

I'd suspect compiz. KDE has compositing built-in to the kwin window manager.

---

### Post by sirdilznik on 2008-11-06
I can't compare because I stay away from GNOME like the plague, but I can say that the numbers for KDE4 are pretty consistent with what I get.

---

### Post by lifestream on 2008-11-06
*ponder*
On the same laptop, KDE is always insanely slow for me, compared to Gnome+Compiz.

I'm curious about your research results :)

---

### Post by shazbut on 2008-11-07
I find the CPU usage monitor in gnome to be a processor hog, maybe that accounts for the high numbers.  Try using the same montior tool in both DEs.  Htop is a good one.

---

### Post by hardyn on 2008-11-07
I have processor use of 0-5% with gnome, not running compiz.

---

### Post by zoomy942 on 2008-11-07
So here is TOP run in the terminal.

Why are the numbers so different from the sysmon and the terminal window?

I am going to get my kubuntu on my LiveUSB up and try this too.

---

### Post by mlapaglia on 2008-11-07
The system monitor itself uses up quite a bit of proccesor. Try switching to the processes tab and look at what is taking up the processor.

Also, you will notice differences with memory usage using different programs. This is mostly in part due to the monitors counting different things in memory as actually taking up ram. Even though some might say 2% usage, your memory is being using much more than that, but by processes that quickly move out of the way when the memory is "really" needed, so it doesn't get "counted" as memory usage.

---

### Post by zoomy942 on 2008-11-07
And here is KDE.

Wow...

---

### Post by krazyd on 2008-11-09
Very interesting - if those numbers are steady, compiz (through Xorg) is quite a resource hog!

Searching the forums here, this problem seems to have been reported quite a few times, though with no real solutions..

---

### Post by irrdev on 2008-11-09
Interesting... Even without running compiz, I have found that Xorg can be a bit cpu heavy with Gnome. Never had a problem with KDE4. I have found that the system tray applets in KDE4 to be a bit heavy at startup, but I am hoping this will be fixed. 

Come to think of it, I believe this is the first post on the forums which states that KDE4 is somehow faster/stabler/better than Gnome. There's been more than enough (somewhat justifiable) complaints about KDE4's instability, features, and lack thereof. It's nice to know that not everyone has something bad to say about KDE4. :)

---

### Post by zoomy942 on 2008-11-09
I agree with you both.  Makes me wonder whats going on.

Can anyone else fire up some USB Kubuntu/Ubuntu and test what I did and see of your results match mine?

i am all about lower cpu usage, and it seems like KDE accomplishes this, but truth be told, i installed kubuntu friday night and it just felt "dis-jointed" vs the gnome i was used to.

---

### Post by Vega on 2008-11-15
> **zoomy942 said:**
> I agree with you both.  Makes me wonder whats going on.

Can anyone else fire up some USB Kubuntu/Ubuntu and test what I did and see of your results match mine?

i am all about lower cpu usage, and it seems like KDE accomplishes this, but truth be told, i installed kubuntu friday night and it just felt "dis-jointed" vs the gnome i was used to.

A friend of mine is experiencing the same difference in speed. KDE4.1 just whips Gnome out of the water in resource management. It makes me wonder if Kubuntu has been seriously optimized more so than Ubuntu

---

### Post by syms on 2008-11-15
the thing is that gnome monitor has a bug which displays cpu usage info incorecctly. you can use conky
```
sudo apt-get install conky
```
but when you will test, dont open any graphical monitors

---

### Post by FrankVdb on 2008-12-23
I have installed 8.10 on a new, powerful system (quad-core 3.2 Ghz CPU, 1600 Mhz bus, Velocirapter drive, 512 MB nVidia card).

At first, everything was alright. However, after installing the Compiz Settings Manager and adjusting a couple of Compiz effects, something suddenly confiscated a quarter of my expensive cycles.

The Gnome system monitor is indeed taking up quite a lot of resources, relatively speaking, but nothing to worry about. Top is showing me that _Xorg_ is taking up a quarter of all CPU cycles. My system is spreading the load over the four cores all the time, so one time it's this core spiking, then it's another.

Intrepid comes with Compiz installed and at first it just worked the way it should. Apparently, the Compiz settings manager has changed the Xorg configuration.

I just hate to see a 25% load on a powerful system that is just sitting there doing nothing.


EDIT: I stand corrected, I just discovered that on another viewport System Monitor had an open window running. Closing it solved the problem, so this was my problem after all.

---

