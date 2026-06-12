---
title: "Two problems in jaunty: kernel and fonts."
date: 2009-06-17
forum: General Help
---

### Post by Ddub on 2009-06-17
A few days ago I upgraded an 8.04 system to 9.04 but now my system will only boot the 2.6.24-14 kernel. I have tried booting to the 2.6.28-13 but it hangs up every time. Also when I do use the working kernel the fonts don't fully display, the bottom eighth or so the letters is chopped off and is often replaced with a line and I can for the life of me figure out why because it seems to be totally at random, sometimes I see full letters but more often than not I don't. Any ideas on what is broken would be greatly appreciated.

Also tried to boot to the live cd and that failed as well, could this mean my hardware somehow isn't compatible with the newest kernel?

---

### Post by mynameinc on 2009-06-17
What are your system specs?
Also, make a new CD, but MD5 this one.  ([HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM"))  Then, try the MD5'd CD.

---

### Post by Ddub on 2009-06-17
P4 2.0 ghz 512 mb RAM Radeon 9200 pci (my agp is dead).
And the cd checks out but still doesn't boot.

---

### Post by mynameinc on 2009-06-18
Try writing a new CD at the lower speed.

Also, look at this: [Ubuntu system requirements - Wikipedia]("http://http://en.wikipedia.org/wiki/Ubuntu#System_requirements")

When you say "checks out", you mean MD5 or the "Check CD for defects" option?

---

### Post by rushikesh988 on 2009-06-18
mynameinc I think you are right my friend also got this type of problem and his problem solved due to this solution ..Ddub brother you can also try LIVE USB to install ubuntu

---

### Post by Ddub on 2009-06-19
Problem solved: My video card finally started acting it's age and died so I switched to the integrated card and everything works. I can't do anything 3d worth crap but at least the system is running now so I'm pretty sure it was just a dying video card and nothing more.

---

