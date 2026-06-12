---
title: "Tremulous Play 2 or more computers from 1 ISP"
date: 2010-03-25
forum: Gaming &amp; Leisure
---

### Post by regor210 on 2010-03-25
While playing on the Internet, when my kid logs into an game I am playing my game locks up. sometimes I get an error   message sv_botfreeclient. Is there a way for us to play on line at the same time?

we are using a router and running Ubuntu9.10

---

### Post by mastablasta on 2010-03-26
If you are connected via router then each of you has different ip so you can play on internet... in fact i did it not long ago with my bro. I think there might be something wrong with your tremulous.

---

### Post by Woojoo//.deb on 2010-03-26
fact is if you use a router you only got 1 ip for every pc that connects to the internet via that router


some servers got security options which prevent the same ip to connect multiple times at once

---

### Post by regor210 on 2010-05-03
Although I did not want to start a server, I needed Tremulous sever installed to play from one or more computers at the same time.

$ sudo apt-get install tremulous-server

Just install it and play no setup needed.

Update 12/01/2010 I found that servers that use TJW need these updates 

[http://www.dannybuntu.com/2008/02/howto-install-tremulous-backport-in.html](http://www.dannybuntu.com/2008/02/howto-install-tremulous-backport-in.html)

to run 2 or more computers playing Tremulous from one ISP.

Update 4/20/2011
I think this may be a Comcast problem.

Was having trouble with 2 of us playing XserverX (just X on the list) at the same time.
This is how I fix it.  

1st computer.
In a Tremulous game press Esc and select Options > System>Net & Sound> Net Data Rate select Lan/Cable/xDsl

Now exit and restart Tremulous and select Get New List to get a new list.

Do this on your other computer while your 1st computer is online in the game so there not trying to use the same port.

--------------------------------------------------------------------------
Update 10/26/2011

In a new install of Xubuntu 11.10 on a 64 bit computer, Tremulous + TJW would not start. Oddly enough installing Wine fix the missing dependencies. Wine is not being used just one of the packages that was installed with Wine fixed what was missing.  

The error had something to do with not having lib32-sdl. Sorry not sure what in the Wine package list fix it. It may have been lib32asound2.

---

