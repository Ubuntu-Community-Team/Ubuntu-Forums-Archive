---
title: "vnc works from konsole, not from desktop"
date: 2006-08-07
forum: Desktop Environments
---

### Post by cesera on 2006-08-07
I am playing a little with vnc, and am having a really strange problem. I have a little script that basically does the following:
 
su - myuser -c "vncserver -geometry 800x600 :2"
 
when I run this script from konsole directly it works, but when I create a KDE Desktop icon pointing to the script (and click 'Run in Terminal') my vncviewer just shows a grey desktop with and 'X' cursor. In both cases Xvnc gets started, but only in the first case does the startkde command in ~/.vnc/xstartup seem to work.
 
 
Can anyone tell me what the difference is between running an application from konsole directly and running it from a desktop icon (in a terminal). I had a look at the environment variables and they basically seem to be the same, so where is the difference?
 
I am really confused by this, but that is probably just showing my ignorance.
 
 
 
Oh yes, I tried calling the script from another script and that did not work either, I don't know if that gives you clue, it doesn't help me.

---

