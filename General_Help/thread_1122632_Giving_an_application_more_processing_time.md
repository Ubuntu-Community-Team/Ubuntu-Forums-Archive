---
title: "Giving an application more processing time"
date: 2009-04-11
forum: General Help
---

### Post by Robbyx on 2009-04-11
Is it possible to permanently give an application more processing time? 

Robin

This does it on a temporary basis. Taken from [www.linex.ie](www.linex.ie)

> I often find myself encoding Mp3's, or playing a seriously powerful game such as Quake II on my machine, and due to my machines relativly weak architecture, it would be nice to get my machine to use all of its processing power (Or as much as it can spare), on a continuous basis for one app alone.

There is an app that can be run from the command line, or an rxvt, which allows you to set up the priority of an app on a scale of -20 (Highest Priority), to +20 (Lowest Priority). A 0 on this scale is normal priority which most apps run at when run.

The first thing you need to do is find out what PID (Process ID) an application has. Everytime an application is executed, it is given a PID so that you can kill it if it hangs (Crashes), or pass information to the program. The command ps will list every process you have running, from your login at bootup to the very command you just used, ie: ps. At the very left of the column is the PID number for every application running on your machine. Simply find the name of the app, and crosscheck it with the PID - Once found, make a note of it.

From the command line, or an rxvt, type in renice . So for example, if I had bladeenc running, at PID 457, and I wanted it to have the highest priority, I would enter the following command -> renice -20 457.

Try having a look at the man files for ps and renice. From the command line, just type in "man ps", and "man renice". You would be suprised at the amount of information that is of help there.


---

### Post by pbpersson on 2009-04-11
Here is an article on this, proceed with extreme caution!!!

[www.linux-magazine.com/w3/issue/65/Realtime_Computing_With_Multimedia_Apps.pdf]("www.linux-magazine.com/w3/issue/65/Realtime_Computing_With_Multimedia_Apps.pdf")

---

### Post by Robbyx on 2009-04-11
Thank you but it looks so complicated I am leaving it alone.

---

