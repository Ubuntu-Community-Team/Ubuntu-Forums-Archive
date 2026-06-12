---
title: "Aaaaaaaaaah, What the hell is this?"
date: 2008-09-12
forum: Desktop Environments
---

### Post by KornyG on 2008-09-12
Hi all,

Got a bit of a dilemma.  I wanted my ubuntu system to boot up, log itself into the normal user account (please, no lectures on security) and then start a program.  The power goes out a lot here in the wet season and it makes it a lot easier when I'm away to keep things running (I'm in the process of obtaining an ups).

So here's what happened.  I set ubuntu up to auto login (which is looks like it sort of does).  I've also set it up to start the program when it finished booting (via the desktop).  So I restarted the computer...

It now boots as per usual, but then rather than providing the login screen (which itself is a good sign) it starts loading the program I wanted started on startup.  All good you would think.  But no.  It hasn't logged in.  It's started the program, but it has no window controls or any kde interface around it or anywhere to be seen on the desktop (ie. No taskbar, no desktop icons, no desktop controls, no right click).  This may seem a little vague, please probe me for a better desription if you need it.  So the final outcome was it boots as per usual, but it loads a nice brown desktop colour and the program i set to auto start and that's it.  It does run, all the daemon's work, I can access files on it and remote telnet to it via ssh.

So I want to undo this and get back to normal.  I want to get rid of the auto login and program startup on boot, all without doing it via the desktop interface.  So the question is, how do I do this from the command line?  I have a secure telnet session, but as for the rest I have no idea.  Please help.

---

### Post by KornyG on 2008-09-12
I suspect getting rid of the application auto start will fix the whole problem and I'll look for a better solution to starting it at boot somehow.

---

### Post by tgalati4 on 2008-09-12
Well it looks like you ran your program without a desktop environment or window manager--that's where the icons and window control come from.

I would suggest an APC SmartUPS with a serial or USB cable that automatically shuts down your system (or place it in standby) so that you can ride out the power outage.

A search of these forums (apcupsd) will reveal several ways to improve your server uptime.

---

### Post by KornyG on 2008-09-13
:) Got the UPS situation sorted.  The power outages are only small so the battery will take care of the momentary losses of power.  It has a parallel port that will provide management functions, so I have no problem there.

Yep, that's what happened alright, no desktop manager.  Now to the problem, do you know how I can fix it via remote terminal through ssh? :-k

I understand what's wrong, but fixing it is the problem. :confused:

---

### Post by EnGorDiaz on 2008-09-13
well i suggest you get a bootloader program and also quickstart installed you can save all your configs back them up

also search up gdm manager in synaptic and also startup-manager

---

### Post by KornyG on 2008-09-13
Solution.  

Remembered Ctrl-Alt-Bkspc drops out of gui and in this case brings me back to login screen.  

Ran login again but as failsafe to avoid loading startup scripts.  

From there removed the startup program and now it's all good.

Ummmm, thanks for your help guys, appreciate your efforts.

---

