---
title: "Kubuntu is slooooooooooow"
date: 2005-08-19
forum: Desktop Environments
---

### Post by DrQuincy on 2005-08-19
I've been configuring Kubuntu no end for the last couple of weeks and now I've noticed somewhere along the line something is really leeching on the CPU's power.

The CPU is always on 65 - 100%!  When I bring up KsysGuard I can't work out what's using it all up.

My setup is:

P4 2.0 Ghz
GeForce 4 128 Meg
1.5 gig SDR RAM

I know this isn't a great spec but current standards but shouldn't Kubuntu be okay with this?  How can I work out what is draining the CPU?

My problem may be something simple, I'm VERY new to Linux. :)  Thanks.

---

### Post by JLTB on 2005-08-19
Go into the command line and type 'top' (its a small program that lets you see running processes).  The processes are ranked by CPU usage by default so the top (har har) one or two should be the culprit.

I have heard of people having trouble with some media programs running in the background and hogging CPU, I've also heard there are fixes for the problem (check the boards here).

GL

---

### Post by amastronardi on 2005-08-19
another useful way is:

ps aux | sort -nk 3

at the end, you will get the most demanding resources processes.

---

### Post by DrQuincy on 2005-08-25
Thanks - I did top and something called xorg-debug is hogging half my CPU - what is this?

---

### Post by DrQuincy on 2005-08-25
Strange, when looking at the process list superkaramba is taking up about 3% of the CPU and xorg-debug about 50 but when I quit super karamba xorg-debug goes down to about 5 and my machine speeds up.  Any ideas why?

---

### Post by hans796 on 2005-08-25
I saw this thread and ran "top"

Kaffeine is using 70-90% of CPU, how get ride of kaffeine running in the background?

---

### Post by manicka on 2005-08-25
[QUOTE=hans796]I saw this thread and ran "top"

Kaffeine is using 70-90% of CPU, how get ride of kaffeine running in the background?[/QUOTE]
 Set Kaffeine to not keep running in the systray after it has been closed

settings-->appearance - uncheck the relavant box

or better still

use totem-xine in gnome instead ;) (sorry, couldn't resist)

---

### Post by GeneralZod on 2005-08-25
[QUOTE=hans796]I saw this thread and ran "top"

Kaffeine is using 70-90% of CPU, how get ride of kaffeine running in the background?[/QUOTE]

This is a bug with kaffeine that stops it from quitting properly.  

```

killall kaffeine

```

should do the trick.  It will recur the next time you open kaffeine, however, unless you upgrade to the patched version (can't find the link; sorry :()

---

