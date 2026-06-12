---
title: "Inspiron 9400/nvidia 7900 overheating"
date: 2008-12-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jiff on 2008-12-20
A while ago, my laptop's gpu overheated while running in windows, and I had to replace the fan and the card, a GeForce GO 7900 GS.  When I got it back, I went with the all linux install, and everything was working great for several hours, maybe 8 or 9.  Then the screen started going a bit fuzzy, like what happened the first time my video card failed.  I turned off the computer, and it felt very hot, so I let it cool.  There does not seem to be any damage, I guess I turned it off in time, but I would rather not have to worry about this overheating again if I leave it on overnight or something.

I have searched the forums and found a few threads about the 7900, but they were for other systems, and I wasn't sure if the fix would be the same with a different configuration.

What I would like is to know how to view the temp of my gpu (the nvidia menu just has 0 degrees showning), and how to make the fans behave, or be able to force them to high myself.  I spent maybe an hour playing world of warcraft today, and installed tons of stuff, generally getting the system ready to go, so it seemed weird that it took so long for something to go wrong, but I am worried that it will deteriorate to the point where I can only use this for 5 minutes every hour.

I just had this video card fixed, and the repairman checked the bios and stuff and said the fan was working just fine, and he didnt see any other problems.  I assume that he also cleaned out the dust while he was in there, so I feel certain that this is a software issue.  Please help!

---

### Post by shane8002 on 2008-12-20
well nividia drivers are not open source like ati but try looking for a motherboard monitoring program that might help keep track of system temps and fan monitoring

---

### Post by jiff on 2008-12-20
Well I installed the most recent nvidia drivers - the 177.8 i think - and I installed i8kutils and sensors-applet, but I cant find where either of them is, or what command to use in terminal to run them :/  I sets sensors-applet to "run at startup" per the install wizard from synaptic, but I dont see it in my system tray

---

### Post by jiff on 2008-12-20
OK, I got gkrellm and i8k working; my fans are coming on much earlier now.  However, on my gkrellm monitor, I can see the temps of all my stuff, and though sda and sg0 are at 36 C, my gpu is at 56 C.  The only fans I see are left and right; is there another fan for the gpu that I should try to control somehow?

---

