---
title: "panels dead"
date: 2006-06-13
forum: Desktop Environments
---

### Post by ronacc on 2006-06-13
my panels are dead,they are there but no icons no menus no right click .
killing and restarting no help reboot no help (i have to use a terminal to shutdown) desktop icons work right, just the panels (top and botom) are dead . mouse ok right click on destop brings up context menu. any ideas ?     breezy 5.10

---

### Post by johnc4510 on 2006-06-13
Try going into Synaptic:
System>Administration>Synaptic Package Manager
Look for:gnome-panel
Mark it for reinstallation and apply
Don't know if that will help or not.

---

### Post by ronacc on 2006-06-13
I reinstalled the panel and panel data no help . I had to start synaptic from terminal , as I said the panels are just dead white space so I dont have the aplications etc menus or icons or anything else , and right click on the panel does NOT bring up the panel menu. Im updating all packages right now to see if that helps , if it dosn't anymore ideas , I'd hate to have to reinstall the whole system , thats sooooo windows !

---

### Post by ronacc on 2006-06-13
well updating all packages didnt help either ???

---

### Post by dmizer on 2006-06-14
this is the exact same problem i was having.  i was never able to solve it completely ... i switched this box over to fc5 and it seems to be much more stable on this box.

some things i recommend:
- make sure you have all your sound configured correctly.
check here for advice on sound (as well as many other helpful hints): [http://ubuntuguide.org/wiki/Ubuntu](http://ubuntuguide.org/wiki/Ubuntu)
- turn off any kind of transparence you might have enabled.
- use the default ubuntu human theme for a while and see if that helps any.
- upgrade to a kernel specific to your box (ie. 686 rather than the default i386 kernel)
- switch to firefox 1.5 and turn off ipv6 as well as plug the memory leak by going to about:config and turning off "browser.cashe.memory.enable"
- follow this thread's advice to turn off modules you don't need: [http://ubuntuforums.org/showthread.php?t=89491&highlight=startup+processes](http://ubuntuforums.org/showthread.php?t=89491&highlight=startup+processes)

i wish you luck ... i was never able to resolve this issue despite having posted many threads.

edit to add: what's your system specs?  and have you tried a memory check via grub?

---

### Post by ronacc on 2006-06-14
this is an anchient k6-2 play box it was working perfectly when the panels went fubar, I right clicked to add an app and poof dead white space. sound etc ok everything else fine just dead panels , my destop icons work and anything I start from terminal runs ok , I updated to dapper lastnight using apt-get upgrade (after switching repositories) and its still there so mabye its a config file that got preserved I'll investigate that and report back. like I said its a play box not my main system so I cant screwup anything important.

---

### Post by dmizer on 2006-06-15
i discoverd that most of the time, my panels would die on me when they were making that little noise they make when the new menu opens or when you click on something.  i really never could nail down the exact cause because there was never anything in any of the logs that looked to be suspect.

if you are not able to play sound from two different programs at the same time, i HIGHLY suggest you take a closer look at your sound config.  heck, even if you are able to make sound from two different sources at the same time, it's still a good idea to check it.  remember, every time you right click or click somewhere in a gnome panel it is suppose to make a sound.

another huge difference was made on my machine when i changed to firefox 1.5 and gaim2 beta.  ubuntu gaim does not appear to make good use of the sound.

here's to show i gave it my best shot ;)
[http://www.ubuntuforums.org/showthread.php?t=185560](http://www.ubuntuforums.org/showthread.php?t=185560)
[http://www.ubuntuforums.org/showthread.php?t=158359](http://www.ubuntuforums.org/showthread.php?t=158359)

filed no bugs, because i couldn't point to a specific app that was causing the problem.  but there was no doubt that ubuntu was not meant for this machine.  i still use ubuntu for another toshiba laptop, but i didn't install gnome.  i also have an ubuntu server.

what processor speed and memory size do  you have?

---

