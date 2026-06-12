---
title: "Screen: wrong vertical position on clean install"
date: 2011-10-02
forum: Desktop Environments
---

### Post by LepeKaname on 2011-10-02
I just made a clean install of Xubuntu 11.04 in my laptop (Panasonic CF-W2).
Everything went fine but the screen position is about 50pixels up from what it should be. If I go to settings and change the resolution from 1024x768 to 800x600 (it doesn't display anything) and I press "ESC" key, it fixes the position. So I have to do that every time I turn on the computer. Even when I plug in an external monitor it goes back to the wrong vertical position.

Previously I installed Kubuntu and it didn't have that problem.

I wonder if there is a way to correct that problem through Xorg.conf?

Thank you in advance.

---

### Post by papibe on 2011-10-02
Could you post your this file /var/log/Xorg.0.log ?

You can use [http://paste.ubuntu.com/]("http://paste.ubuntu.com/") and paste link here.

Regards.

---

### Post by LepeKaname on 2011-10-02
I would post it later as I don't have my laptop now with me. Isn't the Xorg.conf file empty by default?

---

### Post by papibe on 2011-10-02
Indeed, but I'm not asking for /etc/X11/xorg.conf which is the configuration file, but for:
```
/var/log/Xorg.0.log
```
which is the init log from Xorg. There may be some clues about your problem, like a problem with your monitor's EDID for example.

Regards.

---

### Post by LepeKaname on 2011-10-11
Excuse my late response. I will explain what happened:

Before posting the above question I installed the "laptop-net" and "laptop-mode-tools" packages. Then I shutdown the computer (then I posted the question).

When I tried to turn on the laptop again (to get the Xorg.0.log file), by my surprise it failed, no GUI was shown and there was little cue on dmesg on what was happening. The only cue was that at the screen it stopped at "Checking battery state" or something like that. Then I remembered those last packages I installed and proceed to remove them (using console).

After that, I was still not able to have GUI (I didn't have enough time then to check it, so I rest the case some days). Tracing some errors at Xorg.0.log which reported something like: "No screen detected" or something like that. I removed (moved to other directory) the /usr/share/X11/xorg.conf.d/50-* files and It was fixed (even the vertical problem disappeared). 

I really don't understand what happened and why those files were causing any problem.

Perhaps there is some clue in what happened here that solved the vertical position? 
Anyway... thanks "**papibe**" for your help.

---

