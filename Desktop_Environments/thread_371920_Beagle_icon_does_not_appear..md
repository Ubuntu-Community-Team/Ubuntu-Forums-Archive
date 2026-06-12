---
title: "Beagle icon does not appear."
date: 2007-02-27
forum: Desktop Environments
---

### Post by patchkov on 2007-02-27
Hi guys,

Yesterday, I installed beagle. Unfortunatelly icon does not appear on my Ubuntu/gnome taskbar. Right command lines are put into Session start, such as:

beagled
beagle-search --icon

however, nothing happens. 'ps aux' shows beagle related files running in the background, so daemon works, however I cannot do anything to force beagle icon appear in the taskbar.
Even if I write in terminal:

beagle-search --icon

also nothing happens. But 'beagle-search' works itself and runs beagle GUI, but as you guessed I want to have it in icon instead in window.

BTW. Maybe this will give you any hint, however beryl icons also does not appear. I updated to edgy in last two weeks, maybe that is a reason. Previously in Dapper everything was fine (with icons).

Thanks,
Krystian

---

### Post by ComplexNumber on 2007-02-27
i didn't know the beagle icon was supposed to appear. i don't see any reason why it needs to appear in th task bar. either the GUI is open or its not. the daemon runs all the time in the background.

if beryl icon doesn't appear, the chances are you need to right click on the panel, select 'add to panel', then add the notification area.

---

### Post by patchkov on 2007-02-27
Check many of the screenshots available on the web, for example Fedora also got it, it appears.

Beryl icons does not appear any way, no such thing to add.

---

### Post by ComplexNumber on 2007-02-27
here is a screenshot of my desktop after i've clicked on the beryl icon in my menu and am running beagle. as you can see, no beagle icon.



> 
Beryl icons does not appear any way, no such thing to add.
add the Notification Area. or are you saying that you can't find it in the applets list to add?

---

### Post by patchkov on 2007-02-27
I didn't say it is impossible. I am just saying I do not have it. I wrote that in Dapper I did not have trouble at all. And now in Edgy, in applets list I do not have it at all.

BTW. What is that icon on the right next to your firefox and newsreader looking like a magnifing glass + thunder? I found this software once somewhere on the web, but cannot remember what it was.

BTW2. How you launch beagle? You type it into term or made a launcher? In my case, now, I use launcher.

---

### Post by ComplexNumber on 2007-02-27
well i'm running exactly the same as you. there's nowt wrong with my setup. so i think one can conclude that its not supposed to show in the taskbar.

> 
BTW. What is that icon on the right next to your firefox and newsreader looking like a magnifing glass + thunderdeskbar applet
> 
BTW2. How you launch beagle?its in the accessories menu. it appears as "search", but i renamed it to "Beagle Search".

---

### Post by Pigsflew on 2007-04-30
I actually have the opposite problem. I have the Beagle tray icon showing up, and I don't want it; I already have the deskbar applet running. How do I get the beagle daemon to run without the tray icon?

---

### Post by Pigsflew on 2007-05-07
Nevermind, someone told me that the two were unconnected and I could just exit the Beagle program and beagled would still run in the background. Deskbar is nifty!

---

