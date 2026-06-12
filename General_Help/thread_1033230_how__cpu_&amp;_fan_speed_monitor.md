---
title: "how ? cpu &amp; fan speed monitor"
date: 2009-01-07
forum: General Help
---

### Post by Vipercatt on 2009-01-07
Hi
I am very new to linux and finding some things a bit of a challenge but after a little searching i can usually find an answer but
I want to know if there is a small program i can use to let me monitor the cpu temperature on a dual core machine and also the fan speeds for cpu and chassis etc. I have a screenlet called temperature 2 but it doesnt seem to work, i made sure that all of the additional files needed to run it were installed through synaptic
I am using ubuntu 8.10

---

### Post by ushimitsudoki on 2009-01-07
I use conky to monitor things like temp / disk used and so on: it looks like this:
[[IMG]http://meandubuntu.files.wordpress.com/2008/09/conkynew.png?w=300&h=187[/IMG]]("http://meandubuntu.files.wordpress.com/2008/09/conkynew.png")



conky requires a bit of tweaking - there's no GUI, but it's quite flexible. you can find lots of really customized setups.

---

### Post by 3rdalbum on 2009-01-07
You need to install the "lm-sensors" package. After it is installed, you run the "sensors" program in the terminal, and it tells you what command to run to set up the sensors. Once that is done (it's quick and painless) your temperature monitor should work.

---

### Post by yollyp on 2009-01-07
I salute the experts here but to immediately answer your concern, just surf the net and voila, the help is in front of you. :D

---

