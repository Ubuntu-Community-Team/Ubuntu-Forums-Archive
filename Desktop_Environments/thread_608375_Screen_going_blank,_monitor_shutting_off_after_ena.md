---
title: "Screen going blank, monitor shutting off after enabling desktop effects"
date: 2007-11-09
forum: Desktop Environments
---

### Post by SlaughterDog on 2007-11-09
I recently installed XGL and enabled desktop effects. I've got an ATI X1900AiW

Since then, the screen goes black after several minutes of idleness. Then, several minutes later, the screensaver will come back on. Then several minutes after this, the monitor shuts off (before the time it's supposed to).

How might I fix this?

---

### Post by Jennabob on 2007-11-18
I am having the same problem here with the desktop effects. Before I had gotten the desktop effects working on my laptop, I had disabled my laptop screen from shutting down in the power management section as well as the screensaver. After I had installed the desktop effects, I have been having my monitor shut down after being idle for 10 mins. I tried going back into the power management and seeing if my settings were messed up but they are all set to "never" as far as shutting down. I'm wondering if the desktop effects have changed some setting with the power management or if that is the screensaver doing that. (I have that disabled btw) Thanks for any help in advance! lol I'm guessing since I haven't seen anyone else with this issue except here that its probably an easy fix...lmao

---

### Post by mrmiserable on 2007-11-18
not sure but desktop effect done this to me in feisty
i put this in xorg.conf 

Section "ServerFlags"
   Option "BlankTime" "0"
   Option "StandbyTime" "0"
   Option "SuspendTime" "0"
   Option "OffTime" "0"
EndSection

hope it works

---

### Post by Jennabob on 2007-11-19
I tried that and did a restart and I still have the issue...I wonder what is causing that?

---

### Post by Jennabob on 2007-12-07
I also tried a solution from this thread... [http://ubuntuforums.org/showthread.php?t=591090&highlight=screensaver+desktop+effects&page=4](http://ubuntuforums.org/showthread.php?t=591090&highlight=screensaver+desktop+effects&page=4) 
and this also didn't work. :( Any ideas would be welcome. :KS

---

