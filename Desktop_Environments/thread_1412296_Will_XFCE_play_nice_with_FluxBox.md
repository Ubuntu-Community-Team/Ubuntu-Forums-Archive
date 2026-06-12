---
title: "Will XFCE play nice with FluxBox?"
date: 2010-02-21
forum: Desktop Environments
---

### Post by ScarySquirrel on 2010-02-21
[SOLVED] It won't work. FluxBox and XFCE fulfill the same function, and conflict with one another. I have learned this in the IRC.
:confused: Do you know if Fluxbox can work as the WM for a XFCE session? 
I have fluxbox only, at this point, but I want to try it with compiz. 

:D So, what I'm looking at is a sort of XFCE as DE, FluxBox as WM, Compiz-enabled abomination. 

I want to see that starting rightclick menu wiggle! 

Can anyone help me out with the preliminary research for my quest?

I'm tempted to just try it and see what happens, but I want to ask first.

---

### Post by NightwishFan on 2010-02-21
Compiz should replace fluxbox. (I believe it will.)

I think if you set this command as an autostarted app, then you can use fluxbox with XFCE:
```
fluxbox --replace
```

---

### Post by urukrama on 2010-02-21
You can't use Fluxbox with Compiz, but you can use Fluxbox as the window manager in XFCE, instead of xf4wm. Whenever I use XFCE, I use Openbox as the window manager and it runs fine.

To do so, start a normal XFCE session, open a terminal and type (as NightwishFan suggested):

> fluxbox --replace &

Close your terminal, and log out. Before you confirm the log out, tick the box that says "save session for future login". Whenever you login next time, you will run Fluxbox within XFCE.

If you prefer to have Fluxbox's desktop menu, rather than XFCE's, you have to prevent xfdesktop from loading (you can use the command "killall xfdesktop" and then save the session as before). If you do this, you will also lose the icons on your desktop though.

---

### Post by ixifx on 2010-03-05
I'm working on doing basically the same thing, minus the compiz, for a PC I built for my mother out of spare parts.  it's an old duron 700mhz with 256mb ram.  I installed xubuntu on it, but everything was INSANELY slow.  I started looking around the net for lightweight distros and saw that fluxbox was a commonly used lightweight window manager, so I installed that from synaptic, logged out and logged in to a fluxbox session.  now her machine is VERY snappy and responsive.

the first time I started the xfce4-panel from inside this fluxbox session I got an error message telling me that it couldn't start the notification area because one was already running.  after a little bit of research and some help from the friendly people at #fluxbox on freenode IRC I got that fixed. I needed to edit a line in

~/.fluxbox/init

starting with

session.screen0.toolbar.tools: 

and take out the "systemtray" bit

I've taken a liking to the speed and low overhead with this combination and will soon be attempting to make a personal distro install cd.

best of luck with what you're going for, and if you need help I would suggest trying that IRC channel

---

### Post by ScarySquirrel on 2010-04-23
your two posts both regarded installing xfce, and then fluxbox as the window manager. 

I wanted to do the reverse, and I have. It kind of sucked. The gdm stayed with fluxbox's crappy version, I have two volume daemons, and uninstalling fluxbox's configuration utilities will now break my themes. #-o

:cry: I am still living with the results of my daring experiment. :-({|=

Let this be a warning to you all! 

](*,)

---

