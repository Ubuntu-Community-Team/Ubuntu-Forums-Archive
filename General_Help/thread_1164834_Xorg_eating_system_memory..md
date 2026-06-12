---
title: "Xorg eating system memory."
date: 2009-05-20
forum: General Help
---

### Post by QIII on 2009-05-20
I noticed that while testing a Java app my system memory was getting soaked up and not released.  I was moving back and forth through a number of screens (JFrames) fairly rapidly and testing button functionality.

I just spent two days searching for memory leaks and found none.

Another idea occurred to me. I went to the terminal and did top -- only to find that XOrg was hoarding 1.9GB of memory.  All that memory I had been searching for with the Netbeans instrumentation for two days!

Anyone have any ideas why XOrg is hoarding that much memory?  Any way to pry it out of XOrg's greedy little fists?

Jaunty 64 bit
AMD quad core
8GB
ATI Radeon 3100 graphics (sorry to all you gamers ... integrated graphics)

---

### Post by SlowCheetah on 2009-05-20
I have exactly the same problem here. While working with Aptana Studio  (JAVA Application) my system keeps getting slower to the point it's freezing. Wich ends up in an avarage of 2 hard-resets each working day. 

My Xorg uses close to 1Gbyte memory, Java about 250Mbyte. Any solutions found?

---

### Post by XCan on 2009-05-20
I'm not even doing anything advanced. Firefox, gedit + latex, evince, acroread and the occasional game and my Xorg is currently taking up 315.7 MB of RAM after an uptime of 4 days. Btw, on a GF8600GTS using the 180 driver.

---

### Post by QIII on 2009-05-20
Well, fellas, I have a reason for the behavior, but you're not going to like it.

It seems that the current Xorg has a regression to an old bug that caused it to chew up memory without releasing it back to the OS when certain types of objects rendered on screen are destroyed.

Status:  Reopened
Priority:  High
Severity: Major

Xorg has bugs with similar priority and severity that are a couple of years old.

For the moment, the best answer is to add the following to your xorg.conf:

Section "ServerFlags"
        Option          "DontZap"               "yes"
EndSection

When you start to run out of RAM, save what you are working on.

Hit Control-Alt-Backspace to kill the current session and go back to your login screen.

Ugly.

I hope Xorg fixes this before the Redmond Boyz catch on and point it out as a flaw in Linux.  Don't want our community to be a laughing stock.

---

### Post by shuffman37 on 2009-08-10
I have the same problem. Xorg usually eats about 150mb of my 384mb of ram and my system comes to a crawl after any multitasking and even after closing everything Xorg still uses 150mb ram. Swappiness=100 so thats not a problem!

---

