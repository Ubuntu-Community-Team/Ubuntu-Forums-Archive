---
title: "Help troubleshooting frequent restarts"
date: 2009-06-04
forum: General Help
---

### Post by dvord on 2009-06-04
Running 64-bit Ubuntu version 8.04.2, I have an Intel Quad core and 4 gb of kingston hyperx.  

All I'm running on it is VMWare 2.0 and 4 VM's. (mail, web, and 2  Win Serv 2003)

Several times a day the machine restarts itself.  I've looked in the System Log Viewer for any common theme as to what might be preceding these reboots, but it completely escapes me.  

I suspect a hardware problem, but I can't seem to get the thing to reboot when I'm at home watching it.  Invariably it happens while I'm at work.  I've stress tested it at home and nothing seems to make it crash.  

I write in the hopes that someone can give me some ideas on how to perhaps enable more logging to catch whatever it is that might be causing this.

TIA

---

### Post by DeMus on 2009-06-04
> **dvord said:**
> Running 64-bit Ubuntu version 8.04.2, I have an Intel Quad core and 4 gb of kingston hyperx.  

All I'm running on it is VMWare 2.0 and 4 VM's. (mail, web, and 2  Win Serv 2003)

Several times a day the machine restarts itself.  I've looked in the System Log Viewer for any common theme as to what might be preceding these reboots, but it completely escapes me.  

I suspect a hardware problem, but I can't seem to get the thing to reboot when I'm at home watching it.  Invariably it happens while I'm at work.  I've stress tested it at home and nothing seems to make it crash.  

I write in the hopes that someone can give me some ideas on how to perhaps enable more logging to catch whatever it is that might be causing this.

TIA

Just a few simple questions:
How big is the cpu load?
How big is the memory load?
Do you have swap memory installed and enabled?
What are the temperatures of the cpu (and it's cores)?
Is the time between restarts always the same, or maybe the time from leaving the computer alone to the next restart? I ask this to rule out a possibility of having some kind of timer running (for screensaver, powermanagement, or things like that)
I realize you want answers, and I only have questions, but maybe my questions bring you to ideas, hopefully the right one.

---

### Post by dcstar on 2009-06-05
> **dvord said:**
> Running 64-bit Ubuntu version 8.04.2, I have an Intel Quad core and 4 gb of kingston hyperx.  

All I'm running on it is VMWare 2.0 and 4 VM's. (mail, web, and 2  Win Serv 2003)

Several times a day the machine restarts itself.  I've looked in the System Log Viewer for any common theme as to what might be preceding these reboots, but it completely escapes me.  

I suspect a hardware problem, but I can't seem to get the thing to reboot when I'm at home watching it.  Invariably it happens while I'm at work.  I've stress tested it at home and nothing seems to make it crash.  

I write in the hopes that someone can give me some ideas on how to perhaps enable more logging to catch whatever it is that might be causing this.

TIA

Put a decent power filter on it (preferably a UPS).

---

### Post by dvord on 2009-06-05
> **DeMus said:**
> Just a few simple questions:
How big is the cpu load?
How big is the memory load?
Do you have swap memory installed and enabled?
What are the temperatures of the cpu (and it's cores)?
Is the time between restarts always the same, or maybe the time from leaving the computer alone to the next restart? I ask this to rule out a possibility of having some kind of timer running (for screensaver, powermanagement, or things like that)
I realize you want answers, and I only have questions, but maybe my questions bring you to ideas, hopefully the right one.

First off; thank you.  I need more questions.  Or at least a method to find answers.  I think the solution lies right next to me, not here on the forum.  Thanks again!  Now to some answers and more questions!

When I'm watching and the different servers are being used, overall CPU usage is well under 15%.  The VMWare host tells me that none of the guests are using more than 50 mhz of CPU.

Likewise, memory is not even 25% utilized.  I do have a swap file and it's enabled.  

For temperature, I don't know.  I need to install something in Ubuntu to see that.  Do you have any suggestions?

The reboots happen pretty randomly.  Yesterday was the worst which made me first think heat (it was hella hot yesterday), but after I got home (when it was hottest), I didn't get a single reboot.  The reboots don't happen hourly or anything either.  The second one yesterday happened 45 mins after the second one, and the one after that was 90 minutes or so, then it went over 5 hours before the next...  So on and on.

To answer the other question posed:  yes I have a UPS and this machine is the sole connected device.

---

### Post by wpshooter on 2009-06-05
Have you tested your memory ?

As far as temperatures are concerned, there is Xsensors.  Xsensors currently works fine on my Jaunty machine and although the last time I used 8.04 and 8.10, Xsensors was not working on them, my understanding that there are efforts afoot which might fix the problems so it will also run properly under on 8.04 and 8.10.

---

### Post by dvord on 2009-06-05
> **wpshooter said:**
> Have you tested your memory ?

As far as temperatures are concerned, there is Xsensors.  Xsensors currently works fine on my Jaunty machine and although the last time I used 8.04 and 8.10, Xsensors was not working on them, my understanding that there are efforts afoot which might fix the problems so it will also run properly under on 8.04 and 8.10.

Just got the memory tested.  Came out fine.

I got Xsensors and yeah it seems that it's still problematic with this distro.  I really don't think it's heat though.  I'm using the motherboard video, I have a stock fan/heatsink, and it's not rebooted during the heat of the day.  Just apparently when I'm not home.

---

### Post by dhughes on 2009-06-05
Ever since the Jaunty Beta this problem has been popping up more often on the forum.

 I had a similar problem myself (random power fails) and solved it by replacing my power supply but now I'm wondering is it possible there are certain power supplies or some other power supply/power problem that only appears with Jaunty or the kernel version it uses.

 My new system I built in July 2008 worked fine with 8.04 and then 8.10 until I tried a late Beta (late May 2009??) of Jaunty, when I had power problems I went back to 8.10 but I had to download it again since I couldn't find my old CD, I assumed Intrepid Ibex 8.10 had an updated kernel version compared to an October version.

 Anyway, rambling...but to make a long story short something seems odd regarding Jaunty and unusual power problems.

here's my post: [http://ubuntuforums.org/showthread.php?t=1112028](http://ubuntuforums.org/showthread.php?t=1112028)

---

### Post by DeMus on 2009-06-06
> **dvord said:**
> Just got the memory tested.  Came out fine.

I got Xsensors and yeah it seems that it's still problematic with this distro.  I really don't think it's heat though.  I'm using the motherboard video, I have a stock fan/heatsink, and it's not rebooted during the heat of the day.  Just apparently when I'm not home.

So, it's not the load, not the temperatures, you have checked memory and all is well. It did start after installing Jaunty? Before that you never had problems? Not ever?
Did you install extra software, something you did not have before using Jaunty and is it running when the computer crashes,
do you have some experimental software running,
do you have compiz running,
does it happen when switching off the virtual machines?

Did you add some extra hardware to your machine,
did you place it somewhere else,
did you clean the internal fans and touched something you are not allowed to touch?
I know questions again instead of answers. I am trying to help though.

I really hope I could give you an idea where to look. Report back please because this could be interesting for others as well.

---

