---
title: "Gutsy Super Slow!  Lagging and Crashing Please Help!"
date: 2007-12-20
forum: Desktop Environments
---

### Post by wescrow on 2007-12-20
Hello everyone,

I am having a problem that it seems isn't so rare.  Unfortunately I cannot seem to figure it out by simply reading the forums.  I have an eMachines W3507 with an Intel Celeron D (64) 3.2 GHz, ATI Radeon Xpress 200, 512 MB DDR2.  I have recently installed Gutsy i386.  I have been able to debug many things, but this one thing escapes me.  Ubuntu is running way slower than XP did.  At first I thought it was my low RAM.  In fact I went so far as to order another Gig.  Then I started to read the forums and realized that Gutsy is not supposed to be slower than XP so I assume this is a configuration problem. 

Some of the things I have tried:

I got XGL up and running.  Now I can watch DVDs, but they lag horribly.

I tried to change the driver.  Granted I just stole commands from a post that were directed towards a guy with a similar problem and it worked.  The commands I entered were:

$  sudo apt-get install xorg-driver-fglrx

$ sudo aticonfig --initial

The first cammand worked fine, but the second aborted at some point saying:

"Aborted (core dumped)"

And now it won't run again.  It says:

"Warning: Could not find configuration file
Please copy configuration file template to /etc/X11"

I am desperate guys, I can't deal with it lagging out or crashing anymore.  I really want to be free of Windows.  Please help.

---

### Post by wescrow on 2007-12-20
Never mind, I figured it out on my own thanks.

---

### Post by tact on 2007-12-20
way to go!   what did you do to solve it?  I dont have those problems but you might share and enlighten others.

---

### Post by yron87 on 2007-12-21
Hi there! would you mind sharing your solution here? it would surely help others. thanks

---

### Post by wescrow on 2007-12-21
Sure but it's not exactly what you want to hear.  I solved this problem by ditching Ubuntu Gutsy Server and installing Ubuntu Gutsy Desktop instead.  Next I did not enable XGL because that caused all of my problems with lagging and so forth.  This kind of cripples some of the features of Gutsy as I understand, but for one reason or another it is the only way I could get it to work.

And since I changed  this to solved DVD playback has quite working again.  It was working fine, but when I tried to play the same DVD a second time it failed to work.   At this point I really don't know what I'm doing and have decided just to live without DVD playback or killer effects.  Ubuntu doesn't like my machine.

Sorry if that was misleading.

---

### Post by yron87 on 2007-12-21
Ubuntu doesn't like your machine? I don't think so. Last time I installed it on Pentium II 400 Mhz Desktop and Pentium 3 Laptop and it worked. I think there must be something wrong with your configuration. I am not sure if that kind of problem has been posted here or elsewhere. maybe you can try to google around to check if there are any solutions available to your problem. Hope you'll find one soon :) Good Luck

---

