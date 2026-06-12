---
title: "Help! System Freezes on boot after latest updates!"
date: 2006-09-18
forum: Desktop Environments
---

### Post by Bergy on 2006-09-18
Hey all,

Today, I restarted my computer for the first time since the updates on the 15th, and linux freezes on boot during the "Starting System Log..." stage.  I would attach logs, but I am kind of a newbie and do not know which ones to look for, or, for that matter, am not sure they will exist, since the system seems to be having a problem starting them.  :lol: 

I'm running 32-bit Ubuntu on an AMD64 Machine (64-bit Ubuntu caused problems with ndiswrapper that I needed to connect to the internet) with an ATI Sapphire graphics card.  I tried doing an "apt-get update" and "apt-get dist-upgrage" followed by an "apt-get -f install", but even running the newest versions of things, I have the same troubles.  I can, however, boot into the recovery console, which is how I'm managing to post this cry for help.

One possible hint might be that when I start XWin in recovery mode, it gives me a warning message that it cannot boot the Power Manager without the dbus *system* running.

Please please please, any and all ideas are appreciated--this is driving me quite mad.

---

### Post by LTrickey on 2006-09-19
Hi>  Had same msg after update of kernel....
After reading another post I installed Linux-restricted-modules-Uour kernel-K7 in my case (maybe 686 for you) using synaptic. That seemed to fix it. For some  odd reason they got deselected. Hope this helps.

---

