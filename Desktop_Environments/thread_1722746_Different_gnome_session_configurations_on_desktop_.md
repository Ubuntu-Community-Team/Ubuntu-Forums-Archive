---
title: "Different gnome session configurations on desktop and VNC?"
date: 2011-04-06
forum: Desktop Environments
---

### Post by johann_p on 2011-04-06
I am often accessing my desktop computer via VNC from a remote computer.  
 
The problem is that the remote computer has a different screen geometry  (smaller) but when I start a gnome-session in the vnc xstartup the same  panel as for the bigger desktop computer screen appears. This will  scramble the content of the panel because it does not fit.  
 
Also, all other settings from the desktop computer are used in the VNC  session and they influence each other when they get saved. 
 
How can one keep the configuration for both sessions completely  separate? The gnome-session command does not seem to have a parameter  that works for this and gnome-panel does not have any parameter at all.

---

### Post by I-love-maverick on 2011-11-01
Did you find a solution? I've a strange problem. My setup:

1) Remote Desktop (vino server) is enabled for the user "test-user". This is suppose to run on display :0
2) I've installed TightVNC that is using gnome-session and runs on display 99 for the same user, "test-user".

**Problem:** If 1 & 2 both are running, then connecting from  TightVNC  VIEWER to <ip> or <ip>:99 connects to TightVNC  SERVER session  99 :smile:  I can't get to the main display (:0) Interestingly connecting to   <ip>:99 asks for the password and connecting to <ip> doesn't   ask for the password, but the display I get is the same! If I've  started a terminal on one session it shows up on another too!

Looks like somehow TWO gnome-session or vinosever  and TightVNC are confused :smile:

Any help is appreciated.

---

### Post by I-love-maverick on 2011-11-01
Duh! In a hindsight!

Read [http://ubuntuforums.org/showthread.php?t=1394931](http://ubuntuforums.org/showthread.php?t=1394931). Just added display number to gnome-session as below and it worked :)

gnome-session --display :1

I've attached my /etc/init.d/vncserver and ~/.vnc/xstartup. See if that helps!

---

