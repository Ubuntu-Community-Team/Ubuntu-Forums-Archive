---
title: "Desktop / no menus or control panels"
date: 2010-11-06
forum: Desktop Environments
---

### Post by Cyborgoat on 2010-11-06
I have done something to loose access to my Contol panels and menus I have logged into another user and all seem to work fine.  I have logged in under GNOME safemode and it just scrolls stuff on the screen and brings back to main login screen.  I have started to reboot to recovery mode only to find I have no clue as to what to do here as I am Command handycapped..

---

### Post by ConvWin on 2010-11-06
I have kind of the same issue.  Lucid Lynx 10.04 Kubuntu KDE,  Ran some updates on system this morning, then shut it down for a bit.  When I restarted the system I have several things that are happening.  
1 - No min/max/Close buttons in upper right corner
2 - cannot move windows around desktop
3 - I had 2 desktops, now there is only one
4 - keyboard does not work when trying to input commands in Terminal or in "Alt-F2" window.
5 - Menu can't see it half the time to chose a program.

I have enough disk space, everything was working fine this morning before I shut down.  Shutdown went smooth, no crashes of system notified.  Idk. :confused: I did do some searching, but I don't have kwin or metacity in usr/bin.  It has to be the X-org but every time I mess with it I have to redo my system.  

This is very frustrating.  I'm fairly new to Kubuntu.  I like it, but if I keep having these type of problems it's not worth it.  :(

Also I have blocked updates in Systempackagekit, but they are ClamAV, why can't these update??

Please help - and thank you.

---

### Post by Cyborgoat on 2010-11-06
Its funny you mention Clamav because I turned it back on for the first time since the upgrade from 9.14.  All was fine starting out with the upgrade after about a month I realized that it wasn't scanning, so I turned it back on it found one detectable trogen and asked to quarinten it  and I did.  It wasn't too long after that I started with freezing programs to external hd not mounting. I have since noticed I lost the number key pad functions, more frequent lockups  programs freezing, and lost menus and controlpanels.    

Thanks for your reply


>>>

---

### Post by ConvWin on 2010-11-07
Yeah, I did an search of blocked updates and it said to run them manually from the terminal. I did that.  It updated, I think with one pckg.  
Then when I rebooted all hell broke loose.  
I don't really want to reload, afraid to loose all my settings and programs, plus I dual boot with Win7.  

Running Grub.25
I guess I know enough about KDE just to be dangerous.

Thanks.

---

### Post by Cyborgoat on 2010-11-09
Solved!!
Boot into recovery mode open the terminal and type: 

sudo cd /home/<problem_user>/; rm -Rf .gonf .gconfd .gnome2 .gnome2_private

This will reset everything the next time you boot into the "problem user" with default settings.

big thanks to Smoker

---

