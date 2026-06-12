---
title: "Excessive RAM and slow performance on laptop"
date: 2006-08-07
forum: Desktop Environments
---

### Post by pureliquidhw on 2006-08-07
I installed ubuntu 6.06 on a HP pavillion dv1000.  It has a 1.7 Ghz centrino and 700+ MB of RAM.

The over all experince is sluggish and the system was using 412 MB of RAM.  the proc stepped down correctly, sped up when a higher demand was placed on it, but it still felt dog slow.

Issues:
downloads took longer to initialize (1-2 sec delay before pages began to render, then normal load after.)  This was the case on 3 different high speed networks (cable, slow cable, and parallel T1)
Window rendering was choppy, as was scrolling.

helpful facts:
glxgears ran @ ~800 FPS
the video driver was correct i810

I downladed debian but somehow managed to burn the iso's wrong, so no help there yet.  When i do get debian up, I'll try and post more info.

---

### Post by RedFive on 2006-08-07
I feel the same and have 1 gig of ram and an AMD 3000. Windows is pretty quick, but the gui here is sluggish and I don't think it should be. Is there a big difference between ubuntu and xubuntu in terms of this? How can I lean this thing out so it runs quicker?

---

### Post by pureliquidhw on 2006-08-08
I have the xubuntu torent running at home.  I didn't burn the debian ISO's wrong because 3 diff. applications burned teh image poorly (won't boot or even be recognized.)  I also have slackware.  Tonight will be one heck of a long one.  All 14 iso CD's for debian are waiting in line so i can try those too.

My friend suggested turning off the http and ftp servers but apache shouldn't use that much proc power when not being accessed and I still had 300MB of RAM free.  I honestly can't identify what the problem is.  Maybe if i can get APM to work I can step up the proc to full speed all the time and see if the step-down was the cause of the slowdown.

---

### Post by computergroove on 2006-08-09
My buddy was having the same problem with his Dell laptop. His problem was that he did a update from Ubuntu 5.1. I worked on it for him and noticed how slow it was. He just installed fresh from a 6.06 cd and its much faster. Have you installed the optimized kernel files on your system?

---

### Post by dennisharrison on 2006-08-09
use the 686 kernel instead of the 386 kernel (even though from what I understand speed differnece is negligible) [oh and supposedly don't use 686 kernel on your amd based system because its slower... from what I gather from several forum posts]

and look into hdparm settings for your hard drive
maybe dma is not enabled?

and do you get any errors in any of your log files?

errors at boot before mounting filesystem?

---

### Post by gotfoo on 2006-08-11
I've noticed the same issue but it only started happening recently.

I've got an AMD46/1GbRam and 2 days ago it was fine.  
Last night I noticed that mouse clicking actions were delayed .  I'd click and then move the mouse but it was acting like I was clicking, holing down the left-button and dragging.  So every time I clicked a hyper-link it tried to drag it on the page.  Or while usig gedit it kept grabbing the document tabs and dragging them.  Also Krusader got messed up because the mouse grabbed a column bar and would not let it go.  So every time I tried to click something (files or folder) it would tell me that I counldn't perform that action.  

Finnaly when I went for a 3rd reboot the system froze except for the mouse.  It could still move around the screen but it couldn't click anything.

Theese symptoms started AFTER I removed clvm and redhat cluster manager.:confused: 

And they happen when using either the touch-pad or the external usb mouse.:confused: 

I did a reboot but that didn't help. And again and again.

I have also noticed that Firefoxes' ram usage is in the 60+MB area with 3 tabs open.  And Nautilus is sucking up another 50+MB.
Also after about 30 minutes of browser, email and a gedit doc the system cache (in the gone system monitor applet) is maxed out.

I'd say this is a Firefox memory leak but the mi=use issues I described before happen in all apps.  

In the past 2 days I have applied any security updates that were released, the Firefox plugins Greasemonkey and Shazou and I removed **clvm** and **redhat cluster manager**.

***I was going to run a cluster at home because I've got 2 extra boxes (AMD 3000+ and 2800+ each w/1Gb Ram) just gathering dust. So I figured I try clustering them.***

I know this doesen't help but the more people that report these  symptoms then maybe somebody will notice.

---

### Post by it.henrik on 2006-08-11
I am also running strangely low on free ram .. I have 512 and ubuntu is using 300+ after booting?

I did upgrade from breezy... wil give myself a clean install when efty is released.

---

### Post by niteblind on 2006-08-11
!!me too post!!

mine is a clean install of kubuntu and from the point of completing install and rebooting the system is suing 380-420mb of my 512mbs of ram. This is running on a 1.6 centrino 725 processor.

I have also noticed that booting is becoming progressively slower.

niteblind

---

