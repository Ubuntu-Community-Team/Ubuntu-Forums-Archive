---
title: "[SOLVED] desktop effects in gutsy"
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by adityakavoor on 2007-10-18
desktop effects was working fine with feisty
now it says desktop effects cannot be enabled
i have an intel 965 mboard integrated grfics .. X3000 series

```
aditya@ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
Blacklisted PCIID '8086:29a2' found 
aborting and using fallback: /usr/bin/metacity
```

any idea?

---

### Post by mannheim on 2007-10-18
In gutsy, the script that launches compiz checks your graphics card against a blacklist of cards which are  "known" to behave badly with compiz. But you can overrule these checks: create file under your home directory with the path ~/.config/compiz/compiz-manager and put in it the line:
```
SKIP_CHECKS=yes
```
Then compiz will be launched regardless. I guess you should also look through the bug reports and see if you can find what the issue is supposed to be (if any) with this card.

---

### Post by desheffer on 2007-10-18
It seems the Intel 965 is on the compiz-fusion blacklist because it has some unexpected behaviour. More precisely, Xv video playback is broken. [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) has some details.

To put it simply, if you really want to run compiz, you can do the following to skip the blacklist check:
```
SKIP_CHECKS=yes compiz
```

This will probably cause some problems though later on, so it's an "at your own risk" sort of thing. One thing that comes to mind is you will have to run **gstreamer-properties** and change your video output to *X Window System (No Xv)*.

---

### Post by adityakavoor on 2007-10-18
thanks mate

---

### Post by andrewabc on 2007-10-21
Hi I have same problem, my intel video card is blacklisted. 
I input the skip checks command and everything runs fine, but as soon as I close terminal the windows get messed up (titlebars I presume for emerald) and the effects still work.

I presume this means I have to find
~/.config/compiz/compiz-manager
and input it into the file so it remembers that.

But I cannot find that file or where the folder is.

---

### Post by FuturePilot on 2007-10-21
See here
[http://ubuntuforums.org/showthread.php?t=582112]("http://ubuntuforums.org/showthread.php?t=582112")
Do this at your own risk.

---

### Post by andrewabc on 2007-10-21
Thank you for the fast reply!
I am only testing ubuntu so nothing critical on it (I can format it at any time). As long as it doesn't do anything to my windows partition ;)

---

### Post by andrewabc on 2007-10-21
Is there a quick way to remove that setting I just created? :)
Maybe that should be in the sticky topic as well for people who do add it and then realize they don't want it.

---

### Post by FuturePilot on 2007-10-21
Open a terminal and type in ```
gedit .config/compiz/compiz-manager
```
Find SKIP_CHECKS=yes and remove it. Save and you're done.

---

### Post by andrewabc on 2007-10-21
Thank you. I'll bookmark this thread :)

---

### Post by Raistlin355 on 2007-10-21
I am having the same problem except that mine says:

Checking for Xgl: Not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

this is on a Dell Inspirion 1501 with an ATI 1150 vid card, running Ubuntu 7.10 Gutsy

Any ideas?  I have tried the skip_checks command but to no avail

Got it to work, I installed XGL, but the compiz config settings manager will not work, does any have any ideas to get this working?

---

### Post by adityakavoor on 2007-10-24
```

sudo apt-get install compizconfig-settings-manager

```

---

### Post by Raistlin355 on 2007-10-24
Ok I had tried to reinstall the copmizconfig but that did not work.  After I reloaded Ubuntu I ran:
sudo apt-get install xserver-xgl compizconfig-settings-manager
from the terminal and compiz works just fine!

---

