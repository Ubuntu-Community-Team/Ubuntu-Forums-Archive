---
title: "FreeNX Client Crashes"
date: 2009-03-28
forum: General Help
---

### Post by Mahkra on 2009-03-28
I had FreeNX and the NX client working great. Then one day I goofed a python script I had running and did a killall python. 
It immediately shut down my NX session and ever since when I connect a display opens and then closes. :confused:

I have tried removing temp files from both client and server. Turned on logging. Purging freeNX and reinstalling. Nothing works. 

It is also broken for windows clients as well so I assum no one can use it anymore. Any one have any idea how to fix this?

---

### Post by garretwp on 2009-03-31
This is happening to me as well. This all started after doing a few updates awhile back. I tried reinstalled and digging through the logs and still having the same issue. It will log in and as soon as it goes to load the display, it will crash. I looked at nomachine's site and they have a bug report about something very similar. I tried their suggestions and still no luck. Anyone else having problems?

- Garrett

---

### Post by dannymac64 on 2009-05-15
I have the same issue with the latest freenx server installed on Ubuntu 9.04. Happens from both windows and linux clients, 3.3.0-6

---

### Post by ktrnka on 2009-05-26
Did a little Debugging and found that if you are logging in as a user other than nx, you will need to chown /usr/bin/nx-session-launcher-suid to your username. I know there should be a better way but I'm not sure which command fixed it. I ran chmod +x /usr/bin/nx-session-launcher-suid. If that doesn't work you can just chmod 755 /usr/bin/nx-session-launcher-suid

---

### Post by sat.vivek on 2012-04-10
@ktrnka... thanks for solution, changing permissions did the trick for me.

---

