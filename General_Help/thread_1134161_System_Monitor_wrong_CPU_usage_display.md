---
title: "System Monitor wrong CPU usage display"
date: 2009-04-23
forum: General Help
---

### Post by pPrdrm on 2009-04-23
System Monitor is displaying wrong CPU usage. Even with only it running it goes like 70% to 90% CPU usage. I know this is an old problem but shouldn't it have been fixed by now? Or maybe replaced with something else?

P.S. I've just installed  Ubuntu 9.04 - Jaunty Jackalope and so far no problems (except System Monitor of course). :)

---

### Post by dabl on 2009-04-23
Not enough information.

Open a console window and run ```
top
``` and then you will see some information that should reveal which process is hogging the CPU.

---

### Post by sdennie on 2009-04-23
Actually, it's correct.  But, it's a Heisenburg kind of a problem.  You can't display your CPU usage without changing it.  The problem is that gnome-system-monitor can change it by A LOT in some cases.  It's an old bug that has gradually been getting better (at least in Hardy).

Tip: The size of the window determines how badly it skews the information.

---

### Post by pPrdrm on 2009-04-26
Well I know that CPU usage display programs are in fact programs them selves and therefore they consume CPU resources, but don't you think that 70% is a bit to much? Especially when System Monitor is the only program running? Right now I have firefox and screenlets running (with screenlets monitoring and showing lots of different info like CPU usage, disk space, network traffic and others) and the reading I get from CPU usage is only 3.5% to 4.0%. Am I the only one that finds this a little bit problematic?
Also I noticed that the CPU usage is going sky high only when I choose the Resourses Tab. So I guess it must have something to do with the programing that is responsible for this Tab and not the whole program.

---

### Post by sdennie on 2009-04-26
> **pPrdrm said:**
> Well I know that CPU usage display programs are in fact programs them selves and therefore they consume CPU resources, but don't you think that 70% is a bit to much?

Yes

> 
Especially when System Monitor is the only program running? Right now I have firefox and screenlets running (with screenlets monitoring and showing lots of different info like CPU usage, disk space, network traffic and others) and the reading I get from CPU usage is only 3.5% to 4.0%. Am I the only one that finds this a little bit problematic?


Nope.

> 
Also I noticed that the CPU usage is going sky high only when I choose the Resourses Tab. So I guess it must have something to do with the programing that is responsible for this Tab and not the whole program.

In Hardy, they switched to the new Gnome gnome-system-monitor.  It uses cairo to draw things.  The bug is well known but hasn't been fixed in over a year.  My guess is that the nature of cairo actually makes it unsuitable for using it the way it's being used.  But, no one has come up with a replacement (or figured out how to optimize cairo for this case).

---

### Post by heggink on 2009-04-27
Same here: I have a e8400 CPU (dual cores, 3Ghz). With 8.10, both (a)top and gnome system monitor showed minimal system load (<10%). Straight after upgrading to Jaunty, my CPU usage is also around the 60-70% on a practically idle system. When I add up all the CPU usage for my system I can't seem to get to the >60% usage. Also, my fan is just as quiet as before (humming at 900+ rpm) which also gives me the feel that they system isn't stressed at all. When I start to put some load on the system (HD video with totem seems to do well), I can see the CPU usage go up to a bit over 80% whereas totem consumes 65% CPU according to TOP (fas speed now picking up so load is there). Whichever way I look at it, it does not seem to make sense and my feel is that the numbers reported appear not to be correct.

---

### Post by heggink on 2009-04-27
another issue i found was vnc: with jaunty remote desktop sessions don't get refreshed. In an attempt to replace vino with x11vnc, i deinstalled vino. not only does my HD video now run much more smoothly but my idle CPU usage has dropped to minimal values (well below 10% which was what I was used to with Intrepid).
Never noticved that vino was messing things up but with the HD video looking the way it does now, i am not reinstalling it any time soon.
:guitar: Jaunty rocks now!!

---

### Post by ben2talk on 2009-05-13
Well I only use system monitor after I see in Conky cpu graph.

Now, with an idle desktop, I have around 60 percent background CPU, but the process list looks fairly normal.

Killing conky doesn't help, and running HTOP in a terminal confirms it - fairly normal list of processes jostling for top places, nm-applet, x-session manager, firefox, hald-addon-input, hald-addon-storage, gnome-do.

Normally, with these processes sitting not really working, I see very little in my CPU graph.

It looks as if I have a movie decoding in the background - this is way over the top.

---

