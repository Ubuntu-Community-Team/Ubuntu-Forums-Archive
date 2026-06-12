---
title: "Crash on logout"
date: 2007-04-04
forum: Desktop Environments
---

### Post by bward1 on 2007-04-04
I have ubuntu installed on several computers, one of which is this compaq v2000 series laptop.  Everything works fine until I go to logout or switch user, and then it crashes.  By crash I mean the screen goes blank, and nothing works including ctrl-alt-backspace ctrl-alt-F1 -- ctrl-alt-F8 and ctrl-alt-delete.  Nothing does anything, the screen stays totally black.  I press the power button to restart since there is nothing else I can think to do.  This happens when I log out of gnome, kde, or fluxbox.  I have no idea what I need to do to fix this, any ideas or even hints would be greatly appreciated.

---

### Post by JonD25 on 2007-04-04
I have a similar problem on my Dell D600 when I log out of my XGL session every once in a while. I usually don't use Gnome, so I didn't know if it was a problem for just XGL.

---

### Post by mrmonday on 2007-04-04
I don't know a lot about this, but post your /var/log/xorg.0.log This will give more technical people an idea of what's happening.

---

### Post by sdowney717 on 2007-04-15
the same thing happens with me on feisty with latest ATI restricted driver from the repo

It is happening to enough people with the ati driver enabled that the developers must know about it.
It has been like this a long time.

---

### Post by sdowney717 on 2007-04-15
Here it is

---

### Post by mrmonday on 2007-04-16
ATI doesn't have great linux support, so if it is a driver problem, don't expect a solution soon. I can't see anything wrong with your xorg.0.log, how long was it since it last crashed?

---

### Post by Rashedul on 2007-04-22
I just started using Feisty. I'm having the same problem.

---

### Post by stooka on 2007-04-26
I was having issues with logout as well.  Not sure if it was technically a crash, but when i tried to logout from either a kde or xgl (for beryl) session, my screen would go black until I pressed a key, at which point a shell-looking prompt (something about tty) would ask me to login.  After doing so, I was left with just a command line.  I was able to restart the GUI (KDE or XGL, whichever I was in when it "crashed") with startx.  Upon further investigation, I found a [wiki ]("http://www.thinkwiki.org/wiki/Problems_with_fglrx#Hardlock_on_X_logout") which seems to have solved this for me.  It involves adding TerminateServer=true to your kdmrc file.  Best of luck

---

### Post by trishacupra on 2007-05-07
> **bward1 said:**
> I have ubuntu installed on several computers, one of which is this compaq v2000 series laptop.

I have the same laptop, and same issue. Fingers crossed for a solution.

---

### Post by sachindaluja on 2007-06-03
I have the same laptop too (Presario v2000), and have been bugged by this problem for long. I was using Dapper so I tried upgrading to Fiesty but that didn't help. My current version: Ubuntu Fiesty/Linux 2.6.20-16-generic. Also using fglrx restricted driver for ATI Radeon Express 200M. One workaround which certainly helped: Modiy /etc/X11/gdm/gdm.conf so that AlwaysRestartServer=true (Source: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.8.1/+bug/107115]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.8.1/+bug/107115")).
This should certainly help.

---

