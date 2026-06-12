---
title: "Strange crashing issue"
date: 2006-09-17
forum: Desktop Environments
---

### Post by katiad on 2006-09-17
I'm having an odd crashing issue. Had it in breezy, and again when I updated to Dapper (clean install on the update to Dapper just in hopes of getting rid of this issue). 

Every now and then - sometimes several times a day, sometimes once every week or two - the computer will either:

a) dump me back to the login screen   OR
b) freeze up completely - no chance of switching to another terminal or anything.

I generally have several applications open at once, and narrowing it down to a specific application seems difficult. KDE, firefox, sylpheed, gaim, agregator, calculator, gedit, etc. I have 1gb of memory, and most of what I run isn't too intensive (firefox/kde notwithstanding). 

The strange thing is that I usually leave myself logged on, firefox on, etc. when I go to work, where I and sometimes 2-3 other people will log on remotely using putty, where we talk using... talk, download files, edit files, etc. Never had a crash this way, except once, many months ago, possibly pre-dapper.

Any ideas? I have run memtest for around 15 hours (can't afford to run it longer than that) - with no errors. I'm not ruling out a hardware issue, or even a memory one, but is there any other way I can narrow things down?

---

### Post by lagagnon on 2006-09-17
I would say a 90% chance this is a hardware issue. To check that it might be run a LiveCD on the machine and stress the machine and see if the problems occur. Then you are certain it is hardware based.

As you have checked RAM (which is usually the first culprit) your other possibilities, in order of likelihood are:

1) overheating : clean out all dust especially around fans and heat sinks, check seating of CPU, renew CPU heat sink compound.

2) faulty hard drive: use "smartctl" and also the HD manufacturer's hard drive diagnostic diskette from theie website.

3) faulty power supply: you might have to replace it.

Larry, A+ certified tech.

---

### Post by javierfh on 2006-09-17
I wouldnt say that this is a hardware issue.
There are lots of post around discussing about it.
In fact i have myself similar crashes..maybe not so bad, but at the end what i have to do it is to restart X by ctrl+alt+backspace

As you well mentioned it is hard to reproduce and trace what is the faulty application or reason for it.

If you search in the forums you can see that there are more people having similar issues and i really hope someone someday can find the reason.

javi

---

### Post by lagagnon on 2006-09-17
If you had properly read the initial post, the poster had the issue with Breezy and now with Dapper so really, I doubt it is an OS problem. Sorry to disagree with you.

---

### Post by MacMan on 2006-09-18
> **katiad said:**
> a) dump me back to the login screen   OR
b) freeze up completely - no chance of switching to another terminal or anything.

Do you use the nvidia video driver? I do, and I was having the very same problems.
Turning off hardware acceleration for the nvidia driver in xorg.conf got rid of the first one.
I turned off the NvAgp option and my system hasn't frozen up yet, but I didn't run it for long in this configuration so I can't tell if the problem is really solved.

I'm not on my Ubuntu system now so I can't tell you exactly what to do to your xorg.conf file, but I'm sure you'll find everything you need with a search on this forum.

Anyway, if you use the nvidia driver, give it a try. The performance loss isn't tangible anyway.

I hope this helps.
Ciao.
-- 
Mac

---

### Post by artinla on 2006-09-18
I would boot from the LiveCD just to make sure that the problem is hardware related.  If the LiveCD crashes as well, then you definitely have a hardware problem.  

One thing hardware wise that wasn't mentioned above is the mainboard capacitors.  When they go bad, you get strange symptoms that are very similar to what you are describing.  You can find them by looking at your mainboard for little cylindrical objects that are mounted vertically on the board.  If the top of any of them isn't completely flat, or are bulging in any way, they are likely bad.

If the RAM is not the problem, then I would suspect the Capacitors next.

Art

---

### Post by katiad on 2006-09-18
Thanks for the help in hardware diagnostics & ideas.

I'll check the mainboard out for any capacitator problems visible to the eye - I'd wondered about that after reading another post here with similar issues, but wasn't sure how to check for them.

Will see if I can stress the system with the livecd - any particular apps helpful in this?

I am a little concerned about cooling - perhaps I'll upgrade to a better fan/heatsink combo. Since I don't have any hardware temp monitor, the BIOS pc health status bit is the best I can do. Is there any way to monitor this from within the OS? 

Thanks. Will be doing some research of my own here once I'm safely out of the office and back home with it.

---

