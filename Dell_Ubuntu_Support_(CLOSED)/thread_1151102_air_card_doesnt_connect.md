---
title: "air card doesnt connect"
date: 2009-05-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DirtyBirdflock on 2009-05-06
hello i'm not a very knowledgable person when it comes to computers so please be as simple as you can when telling me stuff. anywho i know there is probably a bunch of people having the same problem i have so sorry if i'm just re asking something that someone else has already asked. 

i have a dell inspiron 8600 and have just got the new 9.04 version of ubuntu on it well everything seems to run great and i love the new look and everything the only problem is i went out the other day and tried to use my at&T air card while out and the computer will not connect to the internet with it. i can go into any wi fi cafe and the computer will connect right off the bat but anytime i try and use the air card it tries to connect then just pops up a message telling me that the gsm network is disconnected. i'm not sure what to do from here and my brother the person who put ubuntu on my computer is stumped. i have thought about going back to windows just so i can use the air card but i really dont want to i like ubuntu and would like to keep it. if anywho has on ideas on this i would love to here it thanks.

---

### Post by coffeeaddict22 on 2009-05-07
Hi,
And welcome.
You're talking about a wireless device.  While I know its easier for you to use the icons, it's an awful lot easier to figure out your problem from the terminal (cutting and pasting pictures into the forums doesn't work well...)
Put the aircard in, open a terminal, and type in ```
lshw -C network
```
and ```
iwconfig
```
Post the results back here.  The first command asks the system what network devices are on your system, and the second asks what wireless configurations are set up.

---

