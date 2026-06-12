---
title: "tightvnc Keyboard Oddity"
date: 2010-11-11
forum: Desktop Environments
---

### Post by schlameel on 2010-11-11
**_Issue_**
When accessing the server from any client, the 'd' key minimizes the current window on the server (not the VNC client itself).  Every other key seems to work fine and I can use the key combo <ALT>-d to issue a 'd', but that is less than convenient.  Anyone know how to solve this?  

I saw this post [http://ubuntuforums.org/showthread.php?p=2539412]("http://ubuntuforums.org/showthread.php?p=2539412") which said to use gconf-editor to set a keyboard layout, but that didn't fix the problem.

**_Server Environment_**
Ubuntu 10.10 (upgraded from 10.04)
32-bit
tightvnc server


**_Client 1_**
Windows 7
64-bit
tightvncviewer

**_Client 2_**
Windows 7
64-bit
realvncviewer

**_Client 3_**
Ubuntu 10.10
32-bit
Vinagre

**_Client 4_**
Ubuntu 10.10
32-bit
tsclient (uses tightvncviewer)

---

### Post by darkhelmetchris on 2010-11-11
Hmm, an interesting problem.

Now, I know this is going to sound silly, but .. I'm going to suggest it anyway.

If you are at the server console with no VNC client connected, and you press "d", does it minimize the current window?  Also, try having a client connected to VNC first, and then press "d" on the server (not at the client).  What is the result?  Also, is it at all possible that you have accidentally defined a hotkey "d" on the server set to minimize a window?  Silly, I know, but hey, sometimes a fresh perspective...  you know.

I would also, just for giggles, check the keyboard layout settings on both sides, see if there is anything strange set there.  I only suggest this because recently I have seen a couple of keyboards set to the wrong locale, and it causes some interesting little quirks.

Just my 2 cents.

I have used VNC extensively, and I have not really seen this kind of problem, so it certainly does interest me to know the outcome.  Let me know the results.

---

### Post by marjaczi on 2010-11-12
I'm experiencing the same issue. 

Server Environment
vanilla clean Ubuntu 10.10 32-bit
tightvnc server

Client
Windows 7 64-bit
tightvncviewer

my .vnc\xstartup looks like this:

#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid black
export XKL_XMODMAP_DISABLE=1
gnome-session &

---

### Post by schlameel on 2010-11-13
Chris,

Thanks for the reply.  I checked the suggested and cannot seem to find anything.  The UI works correctly on the machine itself ('d' doesn't minimize windows).  It wouldn't be the first time I missed something obvious, so I did make sure the computer is plugged in, just in case.

---

### Post by ahilan01 on 2010-11-15
I encountered the exact same problem today. You can fix it in System->Preferences->Keyboard Shortcuts.

Under Window Management look for "Hide all normal windows and set focus to the desktop". For some reason it was set to "D". I changed it to Alt+D to invert the behavior.

The setting persisted after I stopped and restarted tightvncserver. No idea how. Not sure what this will do when I head back in to work and log in from the console!

---

### Post by akfarrell on 2010-11-19
Thank you! I was having the same problem, and had the same mysterious mapping of "D" to "Hide all windows ...".

At first I tried to change this from "D" to undefined -- I don't need that mapped to a keyboard command at all -- but that didn't clear up the problem. I was doing my editing via a VNC session. So, I tried entering Alt-D. I got a message informing me that I couldn't map this action to "D" because it would make it "impossible to type." 

So, Alt by itself, or perhaps Alt-D specifically, isn't getting through somewhere, and maybe that's a clue to how we wound up with D in that setting to begin with. (I've gone with Ctrl-Alt-D, which did come through as expected.)

---

### Post by AMSlider on 2010-11-29
I had this issue as well with a xrdp/vnc session, no idea how it happened....  

The only think that solved it was to follow the directions in [http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/]("http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/")

Basically just logout, get to a terminal or ssh session, then run

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

You will have to reset any gnome/nautilus settings, but at least it's back for now...

Cheers.

Edit:
I'm not sure what I was smokin when I wrote the above and I don't think it will fix the "D" issue.  Here's what I did, all is well so far: Goto System-> Preferences-> Keyboard Shortcuts. Scroll down to "Hide all normal windows and set focus to the desktop" was set to "D".  Just highlight the "D" and hit backspace to set it to Disabled or another combo if you like.  It took a couple logout/logins via rdp to get the shortcut to work.  You may also need to restart X.  Good luck.

---

### Post by schlameel on 2010-12-01
Thanks.  I'll give this a try when I get back to the system.

*** Update - Yep that worked perfectly.

---

### Post by ecadman on 2011-01-05
More here: [http://ubuntuforums.org/showthread.php?t=1595871](http://ubuntuforums.org/showthread.php?t=1595871)

---

### Post by schlameel on 2011-01-05
Thanks ecadman.  I think that is the same solution as AMSlider's updated note.  They worked for me, though I have many complaints about my setup: windows randomly close, sometimes I don't get the gksudo (and similar) dialogs, the <ALT> key simply isn't passed.  Thankfully I have a screen on the remote server and can get up and walk the 8 feet to get a working session.

---

### Post by DaveLevy on 2011-10-04
> **ahilan01 said:**
> I encountered the exact same problem today. You can fix it in System->Preferences->Keyboard Shortcuts.

Under Window Management look for "Hide all normal windows and set focus to the desktop". For some reason it was set to "D". I changed it to Alt+D to invert the behavior.

The setting persisted after I stopped and restarted tightvncserver. No idea how. Not sure what this will do when I head back in to work and log in from the console!

This fixed it for me. 

My context is that I have a headless virtual server running Natty Narwhal so need to run a VNC server that creates a new desktop. I choose tightvnc.

Very Odd, does anyone know why this happens?

---

### Post by DaveLevy on 2011-10-05
> **akfarrell said:**
> Thank you! I was having the same problem, and had the same mysterious mapping of "D" to "Hide all windows ...".

At first I tried to change this from "D" to undefined -- I don't need that mapped to a keyboard command at all -- but that didn't clear up the problem. I was doing my editing via a VNC session. So, I tried entering Alt-D. I got a message informing me that I couldn't map this action to "D" because it would make it "impossible to type." 

So, Alt by itself, or perhaps Alt-D specifically, isn't getting through somewhere, and maybe that's a clue to how we wound up with D in that setting to begin with. (I've gone with Ctrl-Alt-D, which did come through as expected.)

This worked for me. 

I am using Ubuntu 11.04 Natty , a server build with GNOME and tightvnc. i.e the User does not have a desktop, and the adduser command may not configure any user as having desktop capability. (Dunno, havn't tested it) which is why I am using tightvnc. I am using UltraVNC as my browser. The setting of D as the hot key is repeatable, I have configured the user as a tightvnc server account twice and it configures D as 'Hide All Windows' shortcut both times.

Is this an Ubuntu Bug?

Thanks for preceding me. :D

---

### Post by thimmyyy on 2012-10-11
Big thanks ahilan01! :)

---

### Post by wildmanne39 on 2012-10-11
Old thread closed!

---

