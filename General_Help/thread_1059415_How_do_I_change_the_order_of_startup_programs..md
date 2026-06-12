---
title: "How do I change the order of startup programs."
date: 2009-02-03
forum: General Help
---

### Post by residualbit on 2009-02-03
I know that going to sessions is where you add a startup program, but I can I change the order that they start in?


I am running 32bit hardy.

Thanks!

---

### Post by residualbit on 2009-02-03
I've run through all of the different options in sessions, but didn't see anything about the order. help!

---

### Post by dchriscoe on 2009-02-03
Go to System - Prefs - Sessions.
Click on "Current Session" tab.
Change the value under "Order" at the bottom of the screen to a lower number.
For more detail info click the Help button on that screen.

Hopes this works for you.

---

### Post by residualbit on 2009-02-03
That only changes it for the current session. The issue I am having is that I use the check gmail app. When I add it to the start, it starts up before network manager(so before i am connected to the internet) which give it an error and I have to restart it. I want to have the check gmail app open last in the startup sequence.

---

### Post by residualbit on 2009-02-04
Anyone know how to do this?

---

### Post by fragos on 2009-02-04
To achieve faster boots some servers or aps are started almost simultaniously and the order is determined by which finishes first. You can overcome that by running the check gmail from a script that verifies the connection is up. You'd then start that script in sessions.

---

### Post by residualbit on 2009-02-04
how would i do that?

---

### Post by lotech on 2009-02-04
I've the same problem the networkmanager starts *after* all my internet stuffs and error keep popping up on screen, IMHO to customize individual apps with script to cope with that is not a long term solution, there must be somewhere hiding the system default we could change, or better a tool to handle that.

---

### Post by liquidpele on 2009-02-04
There is not really any good way to do this because of limitations in how Linux starts up it's services and programs - there is no way to make one service/program dependant on another starting like you can do in Windows.  This is because unlike Windows, the startup services do not adhere to an API they just do their own thing when you run them.

The best solution is to submit a bug report to the gmail checking script - it should be checking for the internet connection and not crashing or stopping just because you haven't picked up an IP yet.

---

### Post by mordoc on 2009-02-04
> **nkirk1 said:**
> how would i do that?

Here's something that found at the following:

[URL="http://www.linuxquestions.org/questions/linux-general-1/detect-if-a-network-device-is-connected-in-a-bash-script-692824/"]
http://www.linuxquestions.org/questions/linux-general-1/detect-if-a-network-device-is-connected-in-a-bash-script-692824/[/URL]

With some modification it should work...

For example, I did this:

#!/bin/bash

VARI=`ping -c 1 192.168.1.1 | grep -i "unreachable" | wc -l`
if [ $VARI -eq 0 ]; then
        gedit
fi

If the network is unreachable then it runs gedit.  You could also use a loop to sleep the script and then try again...

---

