---
title: "I can't get special desktop effects on my computer"
date: 2008-04-20
forum: Desktop Environments
---

### Post by garrettstarnes on 2008-04-20
When I first tried to enable the desktop effects in System>Preferences>Appearance[Visual Effects] it told me "Desktop effects could not be enabled" (this is when I try either "normal" or "extra").  i posted this in another thread, but I quit getting responses.  I did however get one response to install some 'compiz' something.  I did, and it gave me some way cool choices, but it doesn't work either.  The choices are there to check (or click), but now I get a message saying 'The Composite extension is not available'.  I am new to Ubuntu, and to the terminal.  Any help would be GREATLY appreciated!!

Thanx

---

### Post by Jack3760 on 2008-04-20
Inadequet graphics card

---

### Post by rainwalker on 2008-04-20
See if you can force it to start with ```
SKIP_CHECKS=yes compiz
``` in a terminal

---

### Post by garrettstarnes on 2008-04-20
Ok, I copied that command in the terminal and it gave me a message 'fatal  no composite extention'.  I didn't think it was an inadequate graphics card because Dell said that it was an upgrade.   Maybe I'm wrong, but they did tell me that.  I have even called their tech support to no avail.  But yeah, 'fatal no composite extention'.  Thanx!!

---

### Post by overdrank on 2008-04-20
> **garrettstarnes said:**
> Ok, I copied that command in the terminal and it gave me a message 'fatal  no composite extention'.  I didn't think it was an inadequate graphics card because Dell said that it was an upgrade.   Maybe I'm wrong, but they did tell me that.  I have even called their tech support to no avail.  But yeah, 'fatal no composite extention'.  Thanx!!

HI and I believe you are using the ATI X1400 and have you looked a Envy to install the drivers
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Also I have seen issue with the white screen after enabling the effects so you may do a quick search and be prepared  :)

---

### Post by garrettstarnes on 2008-04-25
Envy did it!!!  Thanx so much.  It is a little overwhelming all of the settings and everything, but it all seems to be working now.  Thanx!!

---

