---
title: "Processor usage increases as uptime increases?"
date: 2006-03-23
forum: Desktop Environments
---

### Post by pbaehr on 2006-03-23
I recently installed a gdesklet monitor to watch my various system statistics. Since then I've noticed a trend.

When my computer first starts up fresh the processor usage tends to jump around between 2% and 10%, generally staying at the lower end. After the computer has been on for 12-24 hours without doing much of anything (like overnight) and I return to it the processor usage sits between 15% and 25% or so. If I leave it on longer (like for the rest of the day while I'm at work) I often come home and find it idles at with processor usage in the 30% - 40% range. Sometimes there is a noticeable change in performance. It depends on what I'm doing. A restart brings it back to the first range.

It is an AMD64 chip (I forget the exact model and I'm at work now) and I'm running the 32 bit version of Breezy. The computer should pretty much just be running the screensaver and the occasional cron job (my computer turns my lights on and off in the morning and evening). Also, I recently started to use SSH to connect to the computer from work. But the problem existed before I started doing that.

1) Any thoughts on what would cause this build-up?
2) Is there a command I can use to find out exactly what the processor is so busy doing?

---

### Post by lotheac on 2006-03-23
'top' should tell you what's using the processor.

---

### Post by pbaehr on 2006-03-23
I did that (via SSH) and noticed the most active program is python which is currently using 15-20% of the CPU. Second is the screensaver.

Is python a default install or am I remembering correctly that I added it because something was dependent on it? I can't remember what I installed Python for, maybe a gdesklet used it. I'll have to check and see if that's what's clogging things up later today since I probably don't really need it. I'll have to see what is relying on it.

---

### Post by engla on 2006-03-23
use 'ps auxww | less' to get a compehensive list of all processes and their command lines, so you can see which python processes are running what.

It is very possible that it's gdesklets that use python and use lots of processing power.

Another thing that can use CPU is beagled, if you have it installed. It will use all of your idle processing power for indexing if it suspects that noone uses the computer... it tries to be smart though, and should stop when you come back and use the computer for other things.

---

### Post by pbaehr on 2006-03-23
I'm trying to make heads or tails of the results from the command you gave me. I do see two lines with references to python:
python /usr/sbin/hpssd
python /usr/lib/gdesklets/gdesklets-daemon

So I guess that confirms my suspicion that gdesklets is using python. I don't know what the other one is.

The irony here is that I never actually noticed the extra usage until I installed the gdesklet that monitors the processor. I'm starting to wonder if that gdesklet itself is the culprit.

---

### Post by pbaehr on 2006-03-23
For anyone who is interested or finds this thread in a search for this problem I searched for a little while and finally tracked down this thread:
[http://www.ubuntuforums.org/showthread.php?t=27423&highlight=python+resources](http://www.ubuntuforums.org/showthread.php?t=27423&highlight=python+resources)

They describe the same thing and the program and fault is a countdown gdesklet which I am also using.

I only have it for kicks so I have no problem with disabling it. I only use it as sort of a gag to count down to the next new episode of Lost with which I am obsessed.

---

### Post by frup on 2006-04-03
my computers been on for 8 hours...running at 2% with firefox and system monitor open... right now... im about to go to bed so i shut down some porgrams.
i have amd athlon 2000+ 
just moving my mouse really fast back and forth can bring the CPU% to 15% :D hehe.

---

