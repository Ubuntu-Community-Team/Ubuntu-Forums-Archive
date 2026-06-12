---
title: "Gnome desktop will not load since I completed updates."
date: 2007-11-16
forum: Desktop Environments
---

### Post by scrawford on 2007-11-16
When I reboot after installing updates, I can login to the GUI, but I just get a mouse pointer on the screen. None of the other gnome desktop loads.

---

### Post by Happy_Man on 2007-11-16
And which update did you install?

---

### Post by scrawford on 2007-11-16
I'm sorry to say I don't know. I was informed there were updates available, and while multi-tasking, I decided to install all available. I was also experimenting with the appearance of my desktop at the time, so it may be a contributing factor???

---

### Post by c_plus_plus on 2007-11-16
were you using compiz? Once when i updated compiz, my gnome would not load.

---

### Post by scrawford on 2007-11-16
I tried to load compiz, but would not load. I'm using an older machine, and I don't think my graphics card is up to running compiz.

Were you able to fix the compiz problem?

---

### Post by c_plus_plus on 2007-11-16
yes, I was able to fix my compiz problem, it turns out the compiz config script runs a command called xvinfo, [which crashes my X-window system]("http://ubuntuforums.org/showthread.php?p=3785574#post3785574") so I just commented it out of my script, and now it works fine.

---

### Post by scrawford on 2007-11-17
Hello all,

I have found a solution to this problem, thanks for all the help given in the forums.

Solution: At the login screen follow the proceedure below::
              1. crtl-alt-F2
              2. At the prompt enter: sudo aptitude install ubuntu-desktop
              3. Restart your computer.
All should be good if your experience is similar to mine.
:guitar:

---

### Post by mahasmb on 2007-11-17
> **scrawford said:**
> Hello all,

I have found a solution to this problem, thanks for all the help given in the forums.

Solution: At the login screen follow the proceedure below::
              1. crtl-alt-F2
              2. At the prompt enter: sudo aptitude install ubuntu-desktop
              3. Restart your computer.
All should be good if your experience is similar to mine.
:guitar:

I had the exact same problem but it still didn't fix it.

I can't connect to the internet without WICD. So nothing gets downloaded.

---

