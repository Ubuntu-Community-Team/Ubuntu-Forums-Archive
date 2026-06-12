---
title: "Kubuntu successfully connected to wireless network but not internet!"
date: 2006-10-06
forum: Desktop Environments
---

### Post by Over Haze on 2006-10-06
After a few months away I have finally come back to my Kubuntu live CD and have worked out most of the kinks. I finally managed to get Kubuntu to connect to my wireless network but that&#8217;s all I can get it to connect to, I can&#8217;t get it to connect to the Internet! I&#8217;m guessing this is a problem connected to my routers ESSID or lack there of, it uses SSID. When I first managed to connect Kubuntu to my network I had forgotten to write the SSID down (when setting up in only entered my WEP) so I accessed my router and copy and pasted it into the ESSID field this caused Kubuntu to freeze up.  I tried the same thing a second time and again it froze. At this point I thought I should get on the boards and ask some advice, so I have. What am I doing wrong? 

I would love the help, I am so close!

---

### Post by wererabbit on 2006-10-06
Hey, I would try actually typing the SSID in there, rather than doing a copy/paste.  Sometimes password fields don't like the copy/paste functionality.  

Also - make sure that the wireless router is connected successfully to the dsl/cable modem it's attached to, or if it *is* the dsl/cable modem, make sure it's getting a green light on "Internet".  Routers are designed to create a local area network.  They also translate data incoming from a Wide Area Network (i.e. the Internet).  You have the LAN working, it sounds like the WAN may be not working. 

Hope this helps!
-w-

---

### Post by Over Haze on 2006-10-06
The Router is my modem so thats no an issue, also all the lights that should be green where green. I'm going to give it another go entering the SSID manually.

---

### Post by Over Haze on 2006-10-06
It worked! I finally got Kubuntu to connect to the Internet wireless! It was however unbelievably slow despite the fact I had a great connection. I would Imagen this was because I was using a live CD? Any input?

---

### Post by wererabbit on 2006-10-06
Glad to hear it works! Well, can't say for sure, but everything is a little slower off the CD, especially if that's a slower drive.  Also check in your router what speed it's wireless transmission is set to - a, b, or g.  Then check your wireless card settings and make them correspond to the router -- you want to go g, preferrably, or if you don't have that, go b.  Also keep in mind that different wireless cards have different behaviour - my Apple wireless cards pick up signals all over the place and are way faster than my Belkin pc wireless card, even though they are all rated the same at 802.11g.
-w-
ps. if you want the most responsive internet, there is nothing really better for a home user than a standard ethernet cable.  you'll just get a more accurate, more responsive internet experience, especially with any kind of fps online gaming.  Just fyi. :)

---

