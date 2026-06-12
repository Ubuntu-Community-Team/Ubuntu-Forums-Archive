---
title: "Runescape, OpenGL Will not work.... Grey screen"
date: 2010-09-14
forum: Gaming &amp; Leisure
---

### Post by troyyy on 2010-09-14
I'm having some issues getting Runescape to work properly in OpenGL. It will load just fine in Safemode... but I can't stand to play with the graphics Safe mode offers. And since Linux is OpenGL... I don't see why this won't work. I have tried it in both Google Chrome and Firefox. Latest on both and tried Sun JRE, and OpenJDK. Neither will work. I have a Quad core with a ATI Raedon HD5770 and Savage 2 runs on the highest settings completely smooth so I know the 3D rendering is there. It just halts at a grey screen. I tried running Chrome out of terminal hoping that I would see an output as to what is going wrong but nothing.. I'm even starting to try Wine to get it working with some sort of good graphics... Anyway, I would like to get the OpenGL settings to work natively in Linux. ANY help will be greatly appreciated. :p

---

### Post by doorknob60 on 2010-09-14
It should work, it does for me. Just make sure you're using the latest (ar a recent) version of Sun Java, and using the latest Catalyst driver (I've had the best luck with Catalyst when I use ATI, including RS). Also, try disabling Compiz or using a different browser. If you can't get it to work, sometimes there's just nothing you can do but wait for new versions of software (which in Ubuntu, means waiting till 10.10) and hope that the new versions fixes it.

---

### Post by Naiki Muliaina on 2010-09-14
I have tried a lot of different setups with Runescape last couple of days. Make sure you have the correct java-browser-plugin. If it doesnt work with OpenJDK, try the main java version. It doesnt seem to make diddliesquat difference what graphics drivers you have installed (in Lucid Lynx I should add). Its all very dependent on your Java though.

---

### Post by troyyy on 2010-09-15
I am using Sun update 20 from the partner repo. Didn't think 21 would make that difference. What update are you running are you using?

---

### Post by Naiki Muliaina on 2010-09-15
Tried today on an old ATI graphics card. HD2400 AGP (as and rubbish as they get?). I have no extra repos installed. Only thing I have done is *sudo apt-get install ubuntu-restricted-extras* . Open Source ATI graphics driver as this card got written out of the new prop drivers?

I searched Java in Synaptic and have attached a screenshot of all the java stuff I have installed. The IcedTea plugin is the important one for Runescape I believe. Make sure you set Runescape to be a trusted java applet too.

Otherwise it works fine, base Ubuntu 10.04 install with restricted extras added.

---

### Post by FattyOwl on 2010-09-16
You can install the desktop client from the RuneScape website and run it trough wine. Give that a try.

---

### Post by blazemore on 2011-01-03
Anyone got this working? Please post here if you have, don't just abandon us!

I have this issue with all combinations of the following:
Sun Java / OpenJDK(IcedTea)
Open source / Proprietary ATI driver
Firefox / Chromium

All from the repos.

---

### Post by troyyy on 2011-03-16
Alright, I've tried everything and nothing has yet to work. 

So far I have tried 2 different ATI Chips both the on-board HD4200 and the PCI-E HD5770 that I have. Same result

I have tried them both on 32bit AND 64 bit installs of both Archlinux and Ubuntu I have tried with the proprietary drivers and the open source drivers. FGLRX info always reports direct rendering through OpenGL 4.1 on the 5770 and 3.1 on the 4200. Same result no matter what configuration. I've always been testing without compiz installed on them of course though I have tried just in case with compiz running. I have really tried anything I can think of

One interesting note on this install of archlinux is I noticed when I changed to the 4200 to try it out in 32bit that the loading was taking forever so I did the normal delete the jagex cache and such then re-load. still taking forever. So I click over to another tab... I look at the network monitor and the bytes start comin in. I click back over to RS and the bar has jumped significantly.. So I start clicking back and forth from the tab and sure enough. Whenever that tab was not in focus it would load up quickly. I can only think that something with this is the culprit. 

I can get OpenGL to load if I click out of the tab quick enough and watch the 15 second keep settings timer go down but as soon as I move over to it to click yes, grey screen.

Also I've tried all of those configurations in Chromium, Firefox, Epiphany, and RS Client with JRE and OpenJDK. My brain is starting to hurt.

---

### Post by Naiki Muliaina on 2011-03-19
Unless something has changed I havent heard about, Runescape still doesnt use your graphics card, peroid. Have you tried what I posted above with the java plug ins?

---

### Post by ThatOne on 2011-05-27
I had this same problem, tried pretty much everything.

In the end a (more or less) vanilla install of Lynx works fine.

From "http://archive.canonical.com/ubuntu lucid partner"
> sun-java6-jre 6.24-1
> sun-java6-plugin 6.24-1

From "http://archive.ubuntu.com/ubuntu lucid main restricted"
> fglrx 8.723.1

From this I can only deduce the following:
If fglrx is the problem, 8.723.1 doesn't cause it.
If the OpenJDK JRE is the problem, the official JRE doesn't cause it.
If the IcedTea6 plugin is the problem, the official plugin doesn't cause it.

Maybe one day I will try to get all of the above on 10.04+ (hopefully xubuntu!), but right now I'm happy to have Java working correctly again (these problems weren't just with RuneScape for me..).

Hope this helps.

---

### Post by BBoyVirtual on 2012-05-19
Im having issues whenever I try to play Runescape too, though its not the same ones that youre having it tells me that I need to install IcedTea6 Java Web Browser Plugin, so I try but it keeps telling me that it is already installed. Any ideas anyone..?

---

### Post by pootan on 2012-05-21
Try the second option on this page    [http://services.runescape.com/m=rswiki/en/Linux_Native_Clients](http://services.runescape.com/m=rswiki/en/Linux_Native_Clients)    The RSU client or Unix client works perfectly for me with sound effects and music.   The two scripts linked at the bottom also worked.

---

