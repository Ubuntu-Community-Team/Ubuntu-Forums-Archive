---
title: "How can I get a good ping?"
date: 2006-07-20
forum: Gaming &amp; Leisure
---

### Post by Carrots171 on 2006-07-20
I live in Asia and have a broadband connection. (Not an especially fast one). I rarely play multiplayer games like Nexuiz, Tremulous or Doom 3 LMS Coop mod because my ping is usually around 250-300. :mad: On some more popular games like Quake 4 I've seen some servers with lower pings, but most servers are 250-300 or even worse. I have two questions:

1. Is it possible to get a good ping with a foreign server? 
2. If it is possible, how fast of an internet connection do I need?

Thanks for your help. ;)

---

### Post by handy on 2006-07-20
If you do no good here, try posting in the network sub-forum, there are some true guru's frequenting that area who may well explain your situation & it's possibilities clearly.

All the best.

---

### Post by vem0m on 2006-07-20
1. Thing is closer local servers will have best ping otherwwise u will almost always get that ping
2. i would recommend at least a 3MB down/384 KBup

---

### Post by User_Program on 2006-07-21
Your download/upload speed do play a part but the more important area is latency and how many hops it takes to get to the server you are playng on. Lower the latency=beter ping.  There is really nothing you can do to improve your ping other then finding the lowest one.  

Another thing you can try is hosting your own server and seeing if ppl close to you are intrested ?  But to host lets say a UT server setup for a 4 man you would need at least 368 upload and that is even pushing it!   Also if someone has a higher ping it will bog everyone else that has a lower ping down.  

A nice program for a graphical representation of seeing how many hops it takes and in what part of the world they are in is   xtraceroute   .....There is a ubuntu package for this called "xt" 

So to get a beter ping on foreign servers= Low Latancy (nothing you really can do about it) So a person could be on a 5 meg down and a 2 meg up and still not get a good ping if it takes too many hops to get there.

Edit:  Somthing you can check out is [http://www.game-monitor.com/](http://www.game-monitor.com/)  They have some great utilities and list most of the major game servers out there by IP,Country,Name,Game ect.  I was just on there looking for some Asian server and found some that weren't listed in the query of the games in game list.  This was for UT2k4 I did check out Q4 but it look like it isn't a very pop game in Asia.  

Ok I'll stop talkin now :)

---

### Post by Carrots171 on 2006-07-21
Thanks for the help. I'm going to try to set up a game server in my area then. (Running on Ubuntu Linux, of course)

---

### Post by vem0m on 2006-07-21
good luck on that remember it takes a pretty good system CPU speed and Memory wise also a damn good internet connection as listed abouve it takes alot(10MB up preferred minimum) best of luck to you

---

### Post by handy on 2006-07-21
> **User_Program said:**
> 

A nice program for a graphical representation of seeing how many hops it takes and in what part of the world they are in is   xtraceroute   .....There is a ubuntu package for this called "xt" 


Thanks for the headsup on **xtraceroute**, I used to use traceroute (or sum such name)
on windoze from time to time.  

It's nice to have the option again. :cool:

---

### Post by BLTicklemonster on 2006-11-20
Come on guys, there's got to be some tweaks you can do to increase your overall internet speed so your ping will lower, right? I mean there's cablenut in windows that tweaks your connection, isn't there something you can do in linux, too?

---

### Post by BLTicklemonster on 2007-03-01
[http://ubuntuforums.org/showthread.php?t=251509&highlight=cablenut](http://ubuntuforums.org/showthread.php?t=251509&highlight=cablenut)

:)

---

### Post by Gosujii-sama on 2010-09-13
There are actually more options than I've seen listed. Yes hops to destination play a role, and distance to hops also play a role. However if you are experiencing "lag" to local destinations also or locations near you there's a simple easy fix. Check all connections for static interfearance such as:

Dialup modems (if they still exist)/DSL
1) Touching wires.
2) Corroded or bad ports. (copper has a tendancy to do this even though its anti corrosive properties. such as the statue of liberty turns green from it creating this protective shell on itself which can cause bad connections like a car battery.)

Cable/SAT:
1) Check your incoming coaxial cable for faults loose connectors and if the male end is not long enough to make a connection.
2) Check to make sure all cat5 cables or other cables/wallplugs are in good non corroded condition.
3) Confirm no corrosion on pc port for cat5 cable.
4) If you use both internet and cableTV make sure both lines are run seperately from the box to location and all connections coming from the box have no faults in the lines. If a grounding block is used such as in sat connections a grounding block is a prime location for corrosion or bad connections. This can usually be found outside of the home mounted on the wall to help prevent strong electrical surges.

If all your connections check out and no sign of corrosion or bad connections the latency your experiancing is probably due to your bad up/down speed, local user load, bad internet company (*shudder* comcast), or another unknown reason such as to many hops to location, distance to great etc.

---

