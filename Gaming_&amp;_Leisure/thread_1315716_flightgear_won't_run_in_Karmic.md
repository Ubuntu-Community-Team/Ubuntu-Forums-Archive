---
title: "flightgear won't run in Karmic"
date: 2009-11-05
forum: Gaming &amp; Leisure
---

### Post by shwallace on 2009-11-05
I installed flightgear using apt-get install. It seems to have installed correctly but it quits running after the initial startup screen. Any ideas on what may be wrong?

---

### Post by Woojoo//.deb on 2009-11-05
try running it via terminal if it shuts down you will most likly see an error in the terminal window please post this here so someone can actualy help you

---

### Post by shwallace on 2009-11-06
I tried running it from a terminal and it just locked up my machine.

---

### Post by razzbar on 2009-11-06
I've been having trouble with FlightGear ever since I started trying to upgrade to the latest version (while still running Jaunty). 

I tried to do a network upgrade to Karmic, and get errors relating to it (or OpenSceneGraph, or scenegear). The intaller told me my system "may be unuseable". 

My 9.10 system is useable, but I've seen some random bugs come up. I've tried upgrading FlightGear via the Synaptic package installer, and get errors. 

Has ***ANYONE*** gotten FlightGear working with Karmic?

---

### Post by wnderinguy34 on 2009-11-08
> **razzbar said:**
> 
Has ***ANYONE*** gotten FlightGear working with Karmic?

This may not be any help ,but even though its really choppy (not enough RAM?) ,it runs the same way it did in  Jaunty for me i.e. The cessna slowly turns left until it runs off the runway,plane crashes but Flightgear does not.


 Toshiba NB200 1gb Ram  Ubuntu 9.10 (not UNR)clean install and Flightgear installed via synaptic.

---

### Post by jano2 on 2009-11-09
flightgear work here, but at low fps (videocard is a old nvidia geforce2 mx/mx 400) .
be sure to have a video card that handle openGL. 
you can have a look in the flightgear wiki:
[http://wiki.flightgear.org/index.php/Troubleshooting_Problems](http://wiki.flightgear.org/index.php/Troubleshooting_Problems)

concerning the plane turning left, this is a normal behaviour of a plane, you need to use rudder on take off to stay on the runway:

[http://wiki.flightgear.org/index.php/Understanding_Propeller_Torque_and_P-Factor](http://wiki.flightgear.org/index.php/Understanding_Propeller_Torque_and_P-Factor)

jano

---

### Post by Marflus on 2009-11-09
Oddly, it's just *started* working with the upgrade for me. Sadly I never really bothered figuring out why it wasn't working in Jaunty, so can't help out with what might have changed, but yes, it can work in Karmic.

---

### Post by shwallace on 2009-11-09
I have a radeon 9200 video card and after some more research, I've come to the conclusion that this is NOT the best video for Linux. I may have to give up on flightgear until I can upgrade my video system. If anyone has some ideas on how tweak the ati video I'd sure appreciate it.

---

