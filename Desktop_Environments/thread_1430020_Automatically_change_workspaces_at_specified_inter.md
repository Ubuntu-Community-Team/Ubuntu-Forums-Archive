---
title: "Automatically change workspaces at specified interval?"
date: 2010-03-14
forum: Desktop Environments
---

### Post by seecanadarun on 2010-03-14
Hello,

I'm wondering if anyone is aware of a way to cycle through workspaces at a set interval.. whether it be a screen saver or other wise any advice would be appreciated!

---

### Post by georgemc on 2010-03-15
I was intrigued so I did a little snooping around and came up with this.
 

 I am using Ubuntu 9.04, Gnome, Compiz is switched off, and 4 work spaces.
 

 In Synaptic there is the “wmctrl” package.  I installed it, checked “man wmctrl”, and made this very simple script to just to see how it works.
 
```

 #!/bin/bash 
 # Switch through the 4 desktops 
 wmctrl -s1 
 sleep 2 
 wmctrl -s2 
 sleep 2 
 wmctrl -s3 
 sleep 2 
 wmctrl -s0 
 exit 
 
```Since my initial terminal, where I am running the script, is on the first workspace or as wmctrl sees it as <DESK> number zero, I am letting it switch through the other workspaces and end up back on my first workspace.  You could write your own little script to endlessly cycle through your workspaces.
 

 Unfortunately is does not work with Compiz switched on, so there might be some other management tool or utility for Compiz.
 

 Hope this helps and points you in a good direction.
 

 George

---

### Post by bclarky12 on 2010-04-15
you can turn off compiz with "metacity --replace &" and restart it with "compiz --replace &" A guy made launchers on his desktops for these two commands, i think its a good idea

---

### Post by Scorchgid on 2011-05-18
Okay when you say run it in terminal is it just copy pasta the code you have there? Because (and sorry bit new) it's not working. Could I have a bit of help? Also it's been a year is there something different out there now?

---

