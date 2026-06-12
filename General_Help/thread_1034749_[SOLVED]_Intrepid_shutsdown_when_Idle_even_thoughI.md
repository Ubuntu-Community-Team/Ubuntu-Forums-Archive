---
title: "[SOLVED] Intrepid shutsdown when Idle even thoughIve set power management to do nothi"
date: 2009-01-09
forum: General Help
---

### Post by mwillams73 on 2009-01-09
Ok so heres the problem Im running Intrepid on my AMD Athlon 1.9 gigaherz cpu,Gigabyte motherboard with built in 5.1 sound, Nvidia 6200 L E with 256 ddr2 ram, 1 Gig ram, 250 gig HDD. Most of the bugs and glitches Ive experienced have been fixed, and over all im pleased with intrepids proformance, But... Whenever I download torrents usualy overnight when im asleep( I have a low bitrate so I do all my large downloads while Im asleep)after 1 hour or so intrepid shutsdown, I checked the power management setting and set them to never shut off, I set the screensaver to never come on, (I usualy just turn my monitor off) Everytime I go to sleep and get up the next day my computer is off, Why? Is ubuntu so dumb that it cant follow orders? I never had these problems with Xp so why is linux better if it cant do simple things? The only reason i switched is that Windows almost to the day of installing after a month has to be reinstalled and I got tired of it. So why should I keep using Intrepid if I cant do the thing that Xp has no problems doing?

I really dont want to go back to Xp I like the way Intrepid works and that its stable (for the most part) I also like thatusualy when I have a problem I can come here and find the solution.

Please help me with this and if you have the solution make sure you post it with step by step instructions I know how to use the terminal and all that( not a complete newb) But I like knowing exactly what needs to be done so if ever have to help someone else I can.

---

### Post by mwillams73 on 2009-01-09
Also Its not over heating my temp is 55c and thats when running labor intensive programs, I have 7 fans running and I clean them and the heatsinks regularly( everymonth) Ive also checked every other thread with the same problem  and its not hardware specific, It seems to be a problem with all makes of pc's and hardware. Please help me out Im not new to pc problems so its really frustrating when I cant fix some thing this simple

---

### Post by mssever on 2009-01-09
I suspect that gnome-power-manager is the culprit. Try firing up gconf-editor and examining the keys under /apps/gnome-power-manager to see if things are as expected. g-p-m sometimes crashes on me, in which case odd power-related things happen (in some cases, my computer won't sleep when I expect it to.

However, I've never had the problem you've described, so it's not universal.

Oh, one more thing to try: If you right click on a panel and hit Add to panel..., you can add the Inhibit Applet. When I click that applet to disable automatic sleeping, my computer won't sleep or shut down for any reason (unless g-p-m is acting up).

---

### Post by mwillams73 on 2009-01-09
Thanks Ill try those, especially the applet that sounds like what i need, When I say universal I didnt mean that everyone has the problem just that  its not specific to just my pc or only one brand of pc's, Ive found 10 others who have almost exactly the same problems and all of us are running different hardware specs,( I.E. cpu's, ram,vid cards, etc) All from different brands, I.E. AMD,Intel, ATI, Nvidia. Thats what universal means atleast thats what I was told, anyways thanks again now i can help the others out cause no ones even botherd to post anything on their threads, well except for all of us with the same problem and I told them if i could figure out a solution id send them the info.

---

### Post by mwillams73 on 2009-01-09
Well I tried the applet, didnt work went to take a nap and let my transmission run. about fifteen minutes after  i stopped moving the mouse intrepid went into sleep mode, atleast this time it didnt shut down but still for some reason it doesnt register that i dont want it to sleep, hibernate,shutdown or anything else unless I tell it to.

So tell me a little more about how to use the gconf editor is it? how do I do that mabe I can get something done that way , Im not afraid of getting my typing fingers dirty, Where do I start, still trying to learn but I think Im coming along well considering I didnt start using a computer till 3 years ago and now I know more than my uncle whos A+ certified, well atleast when it comes to programing, he still know a little more about hardware but Im catching up.

---

### Post by mwillams73 on 2009-01-09
Wow Im smarter than I thought I went to the terminal and ran gconf-editor and it popped up, I didnt know it was that easy, thanks, I really appreciate your help hopefully I can figure this out , I dont plan on  giving up on intrepid and I surely dont want to go back to Windows, they knew about a bug in the 30 gig,80 gig zunes that causes them to fry out on leap years and didnt tell anyone till jan 1 so my beloved zune died and they wouldnt take it under warranty so I refuse to support a company that screws people like that, I love intrepid even with its minor bugs its so much better, even my mom likes it, so maybe I'll have a new convert soon, and in case I do I want to know as much as can about fixing stuff that might go wrong so my mom wont freak out.

---

