---
title: "Firefox &amp; Opera both eventually slow my computer to a halt."
date: 2009-02-19
forum: General Help
---

### Post by TruthTaco on 2009-02-19
I just switched from XP to ubuntu (well technically i dual boot windows 7 and ubuntu) I had been using opera on windows but it seems opera sucks on ubuntu/linux so switched to firefox. even switching to firefox (which i dident want to do) i still have the same basic issue although firefox seems to run better on ubuntu. The problem is if i start using opera and i open up a bunch of tabs and use it for a while etc etc close open lots of tabs then i decided to stop browsing the web (lets assume i browse the web for an hour or so opening 10 tabs close 5 open 5 more etc.) then i decide to open mplayer to play a video. the program starts up but the video wont play (when it normally does) same goes for my mp3 player. Now in the case of opera i think i could close opera and i might get the ability to play videos again etc but in the case of firefox i have to restart the computer in order to get video's to play again. opera also seems to crash randomly.
other than this i have no problem with ubuntu and i like it. I wouldent mind using ubuntu if i could get at least opera or firefox to work stably.
well i would like to point out that this dosent always happen. If its a short session then i can close firefox and be fine. but a long session and i can hardly restart the computer even after closing firefox. The shutdown tab wont comeup and i have to reset it manually. 

I would like to point out when i was using windows xp i hardly ever had to restart my computer, although i did have to kill the opera process instead of closing opera normally for it to actually close...after killing opera i could get video to play fine. but opera dosent seem to run very well in linux even if i ignore the fact that it makes video's unplayable etc. I guess if opera dident crash randomly id be able to do in ubuntu like i did in XP, just kill opera and start the video.

I would also like to point out i have a pretty much completly differnt computer.. the only thing thats the same is the powersupply (i upgraded my computer got a new hard drive etc so this dualbooting computer im on now is not the same computer as the XP computer, it is in fact quite a bit better.)
sorry for rambling on just wanted to provide alot of information for anyone that might be able to help.

---

### Post by Yashiro on 2009-02-19
Which version of Ubuntu?
It sounds like the common issue when you run old Firefox plugins on 64bit Ubuntu/Firefox.

Next time your machine is chugging, open the system monitor. 
Is there a process called npviewer destryoing your cpu time?

---

### Post by jerrrys on 2009-02-19
and which verison of opera, also how much ram? FF can chew up ram..

---

### Post by TruthTaco on 2009-02-19
as far as i know ive got 32 bit 8.04.2 ubuntu. I only have 3 firefox plugins installed, the tab plugin, speed dial, and something that was installed already "ubuntu firefox modifications". Im runnning 3.0.6 of firefox. The most ram ive seen firefox take up is 300 megs so far.

Videocard is radion x1900 series
amd x2 dual core BE-2400
2 gigs of memory
and some new gigabyte motherboard

i686, 2.6.24-23-generic (system?)

i dont like alot of plugins (which is why i used to use opera) but i installed those two to make it more like opera. getting rid of the speed dial plugin wouldent be a big deal but i dont know if i could use firefox without the tab plugin. Ill have to check on the Npviewr.. ive been kinda checking for any processes that stood out but ill look for that specifically next time.

Opera 
9.63

---

### Post by Yashiro on 2009-02-19
Without misbehaving plugins involved I've not seen Firefox grind to a halt myself.

---

### Post by jerrrys on 2009-02-19
sounds like a good setup to me. 2gigs of ram, couple of plugins. maybe you monitor your cpu/ram usage and pin it down

---

### Post by TruthTaco on 2009-02-19
Well i wouldent say firefox itself grinds to a halt... but it grinds other programs on my computer to a halt. Video's wont play, mp3's wont play, with similar problems with opera but not exactly the same. This is after having firefox open for a while after using it with lots of tabs etc. Even after closing firefox i cant get video's to play till i restart the computer.The issues with opera are similar except i dont think i had to restart the computer to get video's/mp3's working again, i just had to kill both opera processes (but its been a while i cant remember for sure.)

Right now im running firefox and ive got 13 tabs open and video's play fine, after its run a while ill check the processes and see whats up. I guess it might not be the tabs im running it could be something else that triggers it like a certain type of webpage maby youtube or java? This isent a rare occasion though, it pretty much happens 100% of the time if i leave firefox/opera open long enough.

Also this is a pretty fresh install of ubuntu, i just installed it last week and everything should be up to date etc.

---

### Post by Yashiro on 2009-02-19
Sounds like broken media plugins. Usually it's flash.

---

### Post by TruthTaco on 2009-02-19
Well i just tested it, video was working fine i had firefox open and 13 tabs, then i went to youtube and played a video and closed the tab and now my desktop video's dont work anymore. how do i go about fixing flash?

---

### Post by Yashiro on 2009-02-19
Which flashplugin do you have installed?

Do *about:plugins* in the FF address bar.

---

### Post by TruthTaco on 2009-02-19
File name: libflashplayer.so
    Shockwave Flash 9.0 r152

Is that what your looking for?

---

### Post by Yashiro on 2009-02-19
Uninstall it. Use Synaptic. Browse for a while to confirm it was indeed to blame.

---

### Post by TruthTaco on 2009-02-19
Ok i confirmed it was flash... version 9 adobe flash was what i was originally using so now ive tried gnash (dident seem to work) swfdec (worked decent) ive tried adobe 10 in firefox and it still has the same problem. Im not sure how to get it installed in opera, and i cant figure out how to get swfdec installed in opera, it seems like i need to change the plugin path in opera but i dont know what to change it to.

---

### Post by knuthf on 2009-02-21
I can confirm this. I have not removed Adobe - but installed gnash on top. If you look at the processes (e.g. with the "ps" command - or a system tool) you will find that Opera has a separate process for the plug-ins. You will then find that this takes a huge amount of time - in executing flash scripts.

I have tried to locate the huge consumption to other plug-ins, such as Java, but cannot get anywhere close to such a CPU-hog. It is most likely a bug in Flash - flv, since flv video was not shown correctly with version 9 and 10 of Adobes' own player - the media was killed. 

Ok - an alternate explanation is that DRM software in FLV is made so protective - e.g. consistently verifies that you are connected to the site with the stream - that it bogs down the system completely. If so, it will explain why the media player also failed. 
So: Do not upgrade with Adobe flash - try to avoid installing it and use open software. Gnash works fine with Opera, and Opera will automatically "register" the new in it list of plug-ins / MIME activation list. I see no reason to tell you how to edit this - which is not difficult, but may introduce errors that will require Opera to best be reinstalled.

Opera 10 is eye-candy and inherits your system appearance finally....:p

---

### Post by Beretta_NZ on 2009-02-22
I'm relieved that I am not alone. Ubuntu 8.10 here, with the exact same issue. A visit to Youtube absolutely destroys system performance and maxes out CPU usage. The Youtube clips as a result are totally jerky. I uninistalled and reinstalled the flash plugin hopin that might help. Nothing.

At this point I've just resigned myself to the fact that there is no decent way to watch Youtube in Ubuntu, which sucks.

---

### Post by Beretta_NZ on 2009-02-22
> **TruthTaco said:**
> Ok i confirmed it was flash... version 9 adobe flash was what i was originally using so now ive tried gnash (dident seem to work) swfdec (worked decent) ive tried adobe 10 in firefox and it still has the same problem.

OK, how do I tell firefox which one to use? None of these appear to be visible in the drop down box in the "applications" tab.

---

