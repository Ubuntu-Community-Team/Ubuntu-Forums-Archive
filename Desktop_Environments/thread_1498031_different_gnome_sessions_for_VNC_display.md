---
title: "different gnome sessions for VNC display?"
date: 2010-05-31
forum: Desktop Environments
---

### Post by mikeperth on 2010-05-31
hi everyone
 
i have tightVNCserver running to provide me with a means of working on my machine whilst the wife watches mythTV on the (physical) display.
 
in 8.04 i used to have "gnome-panel &" as a line in my /home/mike/.vnc/xstartup file, and it worked fine, when i logged in via VNC i had a nice gnome panel to start apps from etc.
 
since 10.04 this stopped working and i had to change gnome-panel to gnome-session. this works... but now it loads everything up in the VNC window just like it does in my main window. this is a problem because it loads things like mythTV front end and so on... i don't want it to do that in my VNC window.
 
does anyone know how it might be possible for me to have two different 'types' of gnome session? Settings i change in System -> Preferences -> Startup Applications are common to both my VNC and my physical displays so i can't turn off mythTVfrontend in there to solve the problem.
 
i'm not sure why gnome-panel stopped working in my xstartup file, but it happened when i upgraded from 8.04 to 10.04. if i try it in the ugly xterm window on VNC i get:
 
```
 
 
Xlib:  extension "RANDR" missing on display ":1.0".
 
** (gnome-panel:26161): WARNING **: Cannot register the panel shell: cannot connect to the session bus.

```
 
the RANDR stuff i get when i launch gnome-session too so i think its the second bit that's the real problem.
 
any ideas would be greatly appreciated!
 
cheers
Mike

---

### Post by mikeperth on 2010-05-31
sorry, i should add that i really want to be logged in as the same user on both displays. again, this worked on 8.04.

---

### Post by jhalmuri3521 on 2010-05-31
I am sorry.........

Actually i dont know about that

And i also want to know is it possible

If yes then how?

---

### Post by mikeperth on 2010-06-01
One thing I had wondered is if using a different desktop environment (like kde or xcfe) in VNC would stop these problems. I'm sure it would but I would rather use gnome everywhere and "properly" solve my problem...

---

### Post by I-love-maverick on 2011-11-01
Did you find a solution? I've a strange problem. My setup:

1) Remote Desktop (vino server) is enabled for the user "test-user". This is suppose to run on display :0
2) I've installed TightVNC that is using gnome-session and runs on display 99 for the same user, "test-user".

**Problem:** If 1 & 2 both are running, then connecting from TightVNC  VIEWER to <ip> or <ip>:99 connects to TightVNC SERVER session  99 :) I can't get to the main display (:0) Interestingly connecting to  <ip>:99 asks for the password and connecting to <ip> doesn't  ask for the password, but the display I get is the same! If I've started a terminal on one session it shows up on another too!

Looks like somehow TWO gnome-session or vinosever  and TightVNC are confused :)

Any help is appreciated.

---

### Post by I-love-maverick on 2011-11-01
See if [http://ubuntuforums.org/showpost.php?p=11414767&postcount=3](http://ubuntuforums.org/showpost.php?p=11414767&postcount=3) helps. It doesn't solve all RANDR, etc. issues.

---

### Post by I-love-maverick on 2011-11-01
I take this back! This stopped working again!

---

