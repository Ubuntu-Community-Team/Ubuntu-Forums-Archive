---
title: "My review of Kubuntu 7.10 on Dell Inspiron 6400 with ATI Mobility Radeon X1400"
date: 2007-10-19
forum: Dell  Ubuntu Support
---

### Post by djRob on 2007-10-19
I used text install from Kubuntu 7.10 Alternate CD.

Installation  went OK as usual but after it, during startup, 
I got an error "bcm43xx: Error: Microcode "bcm43xx.microcode5.fw"
which was present in previous version of Kubuntu (7.04), but now it looked like 
the program was writing error stream to output stream - I couldn't use command line.
After googling the error I found out that it was driver for my wireless card, 
so I disabled my wireless card and the error disappeared. 

Of course KDE didn't want to start because I have ATI card so I had to install ATI driver manually, 
so the problem present in Feisty still isn't solved. Maybe somebody will explain to me, 
why ATI proprietary driver isn't installed by default? Frankly open source driver doesn't work. 
Because of that all non-technically savvy owners of ATI graphic cards will be discouraged from 
using Linux even before they had the chance to try it.

After logging in I saw that still there wasn't any control panel for touch pad (no change from Feisty here) 
so I had to install ksynaptics. Ksynaptics, although works, has one bug - after logging in I have to 
enable tapping and then disable tapping so it will be disabled, ksynaptics doesn't remember its options.
 
I also noticed that function keys stopped working - in Feisty I could lower brightness of the screen with 
the Fn - down arrow keys.

Also Suspend/Hibernate doesn't work - no change from Feisty here.

I found two new programs - Dolphin and Strigi. I uninstalled Dolphin because it screwed up Konqueror 
when I tried to setup Konqueror to open folders. Strigi died natural death of unneeded program when Strigi daemon 
stopped working after some time and didn't want to start. I uninstalled it and replaced it with Beagle.

Next I tried to play various multimedia files - installation of codecs worked fine. Thanks for that, at least 
one of my demands was satisfied.

So I am still waiting for Kubuntu which:
1. Doesn't have bcm43xx error.
2. Installs ATI proprietary driver by default.
3. Has working touchpad control panel (and function keys).
4. Has working Suspend/Hibernate.
5. And maybe has working desktop search installed.

That's all for now, maybe I will conclude this review later.

Robert

---

