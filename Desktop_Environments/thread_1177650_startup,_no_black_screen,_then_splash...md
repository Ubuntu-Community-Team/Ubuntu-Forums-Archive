---
title: "startup, no black screen, then splash.."
date: 2009-06-03
forum: Desktop Environments
---

### Post by balloooza on 2009-06-03
I would like to figure out why my ubuntu startup (after I type in username and password) gose like this

*(press enter at gdm login)*** Wait 5 sec seeing black screen** >** The see startup screen** *(I enabled)* _But the splash screen only shows the loading of the file manager_ > **The splash screen DISSAPPEARS, and the desktop is STILL LOADING!! ***(In My O*pinion, that should have all happened *While* the splash screen was still there)

What I think should happen
*(I press enter at login) ***See Splash screen immediatly, seeing whatever load in the backround **> **Splash screen gose away, and desktop is 100% ready, that means that the ONLY THING THAT SHOULD HAPPEN is the NETWORK APPLET tO CONNECT **

Is there somone who knows how to smooth up the startup on an ubuntu system?

---

### Post by balloooza on 2009-06-04
Bumpedy bump bump...

---

### Post by mmarif4u on 2009-06-04
Which graphic card you are using. I think the issue is with your xorg server.

---

### Post by balloooza on 2009-06-04
It is just a laptop, I think I will move this to brainstorm too.
Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller

---

### Post by m.ayad on 2009-06-04
What you got when you run 

```
startx
```

---

### Post by mmarif4u on 2009-06-04
There are i think some issue with Intel cards specially 965GM.
You can use this guide to settle the things.
[Link to guide]("http://ubuntuforums.org/showthread.php?t=1130582")

You can check this for more details:
[http://www.ubuntu.com/getubuntu/releasenotes/904]("http://www.ubuntu.com/getubuntu/releasenotes/904")

---

