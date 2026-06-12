---
title: "X Server doesn't work"
date: 2010-07-14
forum: Desktop Environments
---

### Post by yabanta on 2010-07-14
I am a new member of this forum and I need help figuring out this problem after hours wasted trying to find a solution online. First I will provide the background information
for the problem:

I purchased a sony vaio vpccw27fx laptop a few months ago. It comes with the nvidia gt330m video card. Recently I attempted to install linux, but I couldn't see anything on the laptop screen unless I connected through an external display via VGA cable. After looking up a solution online, I figured out that I had to extract a custom EDID file for my monitor settings using windows, and then modify my xorg.conf file so that it knows to use this file.
After also wrestling with the annoying nvidia drivers installation (using the new 256.35 drivers that nvidia released apparently 6.22.2010), I finally got it to work.

Now the issue: I need to be able to ssh to a server and need to be able to see the output when running various applications on it. When I type xinit in the terminal, I get the following error message: 

"Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log"

I tried removing /tmp/.X0-lock but then I get the following error:

"_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running"

I have also tried to use cntrl-alt-f1 but usually I just get a blank screen or a chopped up screen with 3 barely discernible terminals and a bunch of weird gray stripes. Sometimes I would be able to use the terminal to type commands but other times not.  

I am very new to linux but one idea I have what's causing this issue is that nvidia is using the X Server since in my nvidia-settings window it says it is using display 0.
But if I turn off nvidia wouldn't that essentially mean I would get a blank screen just as I did before editing xconf to use the EDID file?

I would be very grateful if someone could help me with this as I need to be able to use X Server for my work and right now I stuck after so much time spent trying to fix this issue on my own. Thank you.

---

### Post by ravi84m on 2010-08-12
i had the same problem after upgrading to meerkat.
anyone?

---

### Post by whitefeather010 on 2010-10-21
meerkat upgrade here too.

I get to login screeen, select which user, type password,  and then the login screen pops up again.    

using ctrl alt f1 i can log in to a command line, but i can't start x.    I get "_xservtranssocketunixcreatelistener ...socketcreatelistener failed" 
"_xservtransmakeA11cotsserverlisteners: server is already running" 

if anyone has a solution, I'd sure appreciate hearing about it......

---

