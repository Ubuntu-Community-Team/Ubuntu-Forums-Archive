---
title: "gdm stopped starting after trying a new graphics card"
date: 2011-07-17
forum: Desktop Environments
---

### Post by stsongas on 2011-07-17
Hi all,

I recently ran into a problem where I tried a new graphics card with catastrophic results.  I had a ATI card with proprietary drivers and tried to go to an EVGA card.  Bad idea.  After getting my system back to the point where it boots, all was OK except gdm did not start.  It would go to the Ubuntu logo and the 4 dots would go from orange to white forever. 

I went to another TTY via cttrl-alt-f4 and logged in.  Then ran /etc/X11/gdm start and all was fine, but I wanted this to start automagically.  After perusing the forums and Google, nothing looked helpful.  Finally I started tracking down what the S* scrips were doing and that is when I found it.  Not sure if its a bug or just my system is still screwed and I just worked around it. 

If you go into /etc/rc2.d there is a S20gdm start script.  This is linked to /etc/init.d/gdm so it is the exact same script that I was running, but one worked and one did not.  So what's up?  

In the script there are 2 lines:

INITSCRIPT="$(basename "$0")"
JOB="${INITSCRIPT%.sh}"

So when running sh -x ./S20gdm from rc2.d and it does a 

$COMMAND "$JOB" 

on line 59 of the script, it resolves to

start S20gdm 

Which is not existent, so I changed it to 

$COMMAND gdm 

and now my system comes up.  

There may be better ways and this may not address the root cause but my system now happily boots and takes me to my login screen without having to do anything goofy. 

Regards,
Chris

---

